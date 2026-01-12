<p align="center">
  <img src="https://raw.githubusercontent.com/getbindu/create-bindu-agent/refs/heads/main/assets/light.svg" alt="bindu Logo" width="200">
</p>

<h1 align="center">reasoning-team-agent</h1>

<p align="center">
  <strong>Build a Reasoning Team in Agno that answers complex queries by orchestrating specialized agents with transparent analytical thinking. The team leader uses reasoning tools to plan and delegate tasks like web search and financial data retrieval, then synthesizes findings into structured, source-backed insights. Ideal for financial research platforms, investment analysis tools, market intelligence systems, and decision support applications, this setup makes the team’s reasoning process visible and auditable.</strong>
</p>

<p align="center">
  <a href="https://github.com/raahulrahl/reasoning-team-agent/actions/workflows/main.yml?query=branch%3Amain">
    <img src="https://img.shields.io/github/actions/workflow/status/raahulrahl/reasoning-team-agent/main.yml?branch=main" alt="Build status">
  </a>
  <a href="https://img.shields.io/github/license/raahulrahl/reasoning-team-agent">
    <img src="https://img.shields.io/github/license/raahulrahl/reasoning-team-agent" alt="License">
  </a>
</p>

---

## 📖 Overview

Build a Reasoning Team in Agno that answers complex queries by orchestrating specialized agents with transparent analytical thinking. The team leader uses reasoning tools to plan and delegate tasks like web search and financial data retrieval, then synthesizes findings into structured, source-backed insights. Ideal for financial research platforms, investment analysis tools, market intelligence systems, and decision support applications, this setup makes the team’s reasoning process visible and auditable.. Built on the [Bindu Agent Framework](https://github.com/getbindu/bindu) for the Internet of Agents.

**Key Capabilities:**
- 🧠 Multi-agent reasoning with transparent analytical thinking
- 🔍 Web search via DuckDuckGo for general queries
- 💰 Financial data retrieval from trusted sources (CNBC, Reuters, Bloomberg, WSJ)
- 🔗 MCP server integration (Google Maps, Airbnb)
- 📊 Structured, source-backed insights

---

## 🚀 Quick Start

### Prerequisites

- Python 3.10+
- [uv](https://github.com/astral-sh/uv) package manager
- API keys for OpenRouter and Mem0 (both have free tiers)

### Installation

```bash
# Clone the repository
git clone https://github.com/raahulrahl/reasoning-team-agent.git
cd reasoning-team-agent

# Create virtual environment
uv venv --python 3.12.9
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
uv sync

# Configure environment
cp .env.example .env
```

### Configuration

Edit `.env` and add your API keys:

| Key | Get It From | Required |
|-----|-------------|----------|
| `OPENROUTER_API_KEY` | [OpenRouter](https://openrouter.ai/keys) | ✅ Yes |
| `MEM0_API_KEY` | [Mem0 Dashboard](https://app.mem0.ai/dashboard/api-keys) | If you want to use Mem0 tools |

### Run the Agent

```bash
# Start the agent
uv run python -m reasoning_team_agent

# Agent will be available at http://localhost:3773
```

### Github Setup

```bash
# Initialize git repository and commit your code
git init -b main
git add .
git commit -m "Initial commit"

# Create repository on GitHub and push (replace with your GitHub username)
gh repo create raahulrahl/reasoning-team-agent --public --source=. --remote=origin --push
```

---

## 💡 Usage

### Example Queries

```bash
# Financial analysis
"Analyze Tesla's recent financial performance and market sentiment"

# Market research
"Compare investment opportunities in renewable energy sector"

# Trend analysis
"Research market trends for AI startups in 2024"
```

### Input Formats

**Plain Text:**
```
Natural language queries about financial data, market research, or general web search topics
```

**JSON:**
```json
[
  {"role": "user", "content": "Your query here"}
]
```

### Output Structure

The agent returns structured output with:
- **Analysis**: Synthesized findings from multiple agents
- **Reasoning Steps**: Transparent step-by-step analytical process
- **Sources**: Citations from web search and financial data sources
- **Member Responses**: Individual agent contributions (web search, finance)

---

## 🔌 API Usage

The agent exposes a RESTful API when running. Default endpoint: `http://localhost:3773`

### Quick Start

For complete API documentation, request/response formats, and examples, visit:

📚 **[Bindu API Reference - Send Message to Agent](https://docs.getbindu.com/api-reference/all-the-tasks/send-message-to-agent)**


### Additional Resources

- 📖 [Full API Documentation](https://docs.getbindu.com/api-reference/all-the-tasks/send-message-to-agent)
- 📦 [Postman Collections](https://github.com/GetBindu/Bindu/tree/main/postman/collections)
- 🔧 [API Reference](https://docs.getbindu.com)

---

## 🎯 Skills

### explainable-business-reasoning (v1.0.0)

**Primary Capability:**
- Multi-agent reasoning with web search and financial data retrieval
- Transparent reasoning process with step-by-step analysis
- Specialized agents for web search and financial data

**Features:**
- Reasoning team leader orchestrates specialized agents
- Web search agent with DuckDuckGo integration
- Finance agent with curated financial news sources
- MCP server support for extended capabilities
- Source-backed insights with citations

**Best Used For:**
- Complex queries requiring multiple data sources
- Financial research and market analysis
- Investment opportunity comparisons
- Tasks needing transparent reasoning process

**Not Suitable For:**
- Real-time trading execution
- Simple fact lookup queries
- Tasks requiring domain-specific proprietary data

**Performance:**
- Average processing time: ~1-2 seconds
- Max concurrent requests: 10
- Memory per request: 256MB

---

## 🐳 Docker Deployment

### Local Docker Setup

```bash
# Build and run with Docker Compose
docker-compose up --build

# Agent will be available at http://localhost:3773
```

### Docker Configuration

The agent runs on port `3773` and requires:
- `OPENROUTER_API_KEY` environment variable
- `MEM0_API_KEY` environment variable

Configure these in your `.env` file before running.

### Production Deployment

```bash
# Use production compose file
docker-compose -f docker-compose.prod.yml up -d
```

---

## 🌐 Deploy to bindus.directory

Make your agent discoverable worldwide and enable agent-to-agent collaboration.

### Setup GitHub Secrets

```bash
# Authenticate with GitHub
gh auth login

# Set deployment secrets
gh secret set BINDU_API_TOKEN --body "<your-bindu-api-key>"
gh secret set DOCKERHUB_TOKEN --body "<your-dockerhub-token>"
```

Get your keys:
- **Bindu API Key**: [bindus.directory](https://bindus.directory) dashboard
- **Docker Hub Token**: [Docker Hub Security Settings](https://hub.docker.com/settings/security)

### Deploy

```bash
# Push to trigger automatic deployment
git push origin main
```

GitHub Actions will automatically:
1. Build your agent
2. Create Docker container
3. Push to Docker Hub
4. Register on bindus.directory

---

## 🛠️ Development

### Project Structure

```
reasoning-team-agent/
├── reasoning_team_agent/
│   ├── skills/
│   │   └── reasoning_team_agent/
│   │       ├── skill.yaml          # Skill configuration
│   │       └── __init__.py
│   ├── __init__.py
│   ├── __main__.py
│   ├── main.py                     # Agent entry point
│   └── agent_config.json           # Agent configuration
├── tests/
│   └── test_main.py
├── .env.example
├── docker-compose.yml
├── Dockerfile.agent
└── pyproject.toml
```

### Running Tests

```bash
make test              # Run all tests
make test-cov          # With coverage report
```

### Code Quality

```bash
make format            # Format code with ruff
make lint              # Run linters
make check             # Format + lint + test
```

### Pre-commit Hooks

```bash
# Install pre-commit hooks
uv run pre-commit install

# Run manually
uv run pre-commit run -a
```

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Powered by Bindu

Built with the [Bindu Agent Framework](https://github.com/getbindu/bindu)

**Why Bindu?**
- 🌐 **Internet of Agents**: A2A, AP2, X402 protocols for agent collaboration
- ⚡ **Zero-config setup**: From idea to production in minutes
- 🛠️ **Production-ready**: Built-in deployment, monitoring, and scaling

**Build Your Own Agent:**
```bash
uvx cookiecutter https://github.com/getbindu/create-bindu-agent.git
```

---

## 📚 Resources

- 📖 [Full Documentation](https://raahulrahl.github.io/reasoning-team-agent/)
- 💻 [GitHub Repository](https://github.com/raahulrahl/reasoning-team-agent/)
- 🐛 [Report Issues](https://github.com/raahulrahl/reasoning-team-agent/issues)
- 💬 [Join Discord](https://discord.gg/3w5zuYUuwt)
- 🌐 [Agent Directory](https://bindus.directory)
- 📚 [Bindu Documentation](https://docs.getbindu.com)

---

<p align="center">
  <strong>Built with 💛 by the team from Amsterdam 🌷</strong>
</p>

<p align="center">
  <a href="https://github.com/raahulrahl/reasoning-team-agent">⭐ Star this repo</a> •
  <a href="https://discord.gg/3w5zuYUuwt">💬 Join Discord</a> •
  <a href="https://bindus.directory">🌐 Agent Directory</a>
</p>
