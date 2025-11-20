# LangChain Agent Boilerplate - Build Your Own AI Assistant

This is a **versatile agent platform** that showcases the fundamentals of building task-oriented AI assistants. While the example implementation focuses on data generation, the architecture is intentionally simple and adaptable—**you can easily swap out the tools to create agents for any domain**: DevOps automation, content generation, data analysis, file management, API orchestration, or any other use case that benefits from natural language interaction and autonomous decision-making.

**Think of this as your starting point** for building custom AI agents without the complexity of starting from scratch.

## 🔑 Key Features

### Platform Capabilities
- **Natural Language Interface**: Users interact conversationally without learning command syntax
- **Autonomous Execution**: Agent fills gaps, makes decisions, and executes multi-step workflows
- **Tool-Based Architecture**: Easy to add new capabilities by defining simple Python functions
- **Conversation Memory**: Maintains context across multi-turn interactions
- **Error Handling**: Graceful error recovery with helpful user feedback
- **Zero Configuration**: Works out of the box with minimal setup

### Example Implementation (Data Generation)
The included tools demonstrate the pattern:
- **JSON File Operations**: Read and write JSON files with proper formatting
- **Sample Data Generation**: Create realistic user profiles with configurable parameters
- **Parameter Inference**: Agent intelligently fills missing details without prompting users

## 🛠️ Technologies

- **LangChain**: Agent orchestration and tool management
- **LangGraph**: ReAct agent pattern implementation
- **OpenAI GPT-4**: Language model for natural language understanding
- **Python 3.x**: Core programming language

## 📦 Installation

### Prerequisites
- Python 3.9 or higher
- OpenAI API key ([Get one here](https://platform.openai.com/api-keys))

### Option 1: Using `uv` (Recommended) ⚡

[`uv`](https://github.com/astral-sh/uv) is an extremely fast Python package installer and virtual environment manager written in Rust. It's 10-100x faster than pip!

1. **Install uv** (if not already installed):

```bash
# macOS/Linux
curl -LsSf https://astral.sh/uv/install.sh | sh

# Windows
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"

# Or via pip
pip install uv
```

2. **Clone the repository**:
```bash
git clone <repository-url>
cd AI_agent
```

3. **Create virtual environment and install dependencies**:
```bash
# Create venv with uv
uv venv

# Activate the virtual environment
# On Windows (PowerShell)
.venv\Scripts\Activate.ps1

# On Windows (CMD)
.venv\Scripts\activate.bat

# On macOS/Linux
source .venv/bin/activate

# Install dependencies with uv (extremely fast!)
uv pip install langchain langchain-openai langgraph python-dotenv
```

4. **Create a `.env` file** with your OpenAI API key:
```bash
# Create .env file
echo "OPENAI_API_KEY=your_api_key_here" > .env

# Or on Windows (PowerShell)
"OPENAI_API_KEY=your_api_key_here" | Out-File -FilePath .env -Encoding utf8
```

### Option 2: Using Traditional pip

1. **Clone the repository**:
```bash
git clone <repository-url>
cd AI_agent
```

2. **Create and activate virtual environment**:
```bash
# Create virtual environment
python -m venv .venv

# Activate it
# On Windows (PowerShell)
.venv\Scripts\Activate.ps1

# On Windows (CMD)
.venv\Scripts\activate.bat

# On macOS/Linux
source .venv/bin/activate
```

3. **Install dependencies**:
```bash
pip install langchain langchain-openai langgraph python-dotenv
```

4. **Create a `.env` file** with your OpenAI API key:
```
OPENAI_API_KEY=your_api_key_here
```

### Option 3: Using requirements.txt

If a `requirements.txt` file exists:

```bash
# With uv (fast)
uv pip install -r requirements.txt

# With pip (traditional)
pip install -r requirements.txt
```

### Verify Installation

```bash
python -c "import langchain; import langgraph; print('✓ All dependencies installed successfully!')"
```

## 🚀 Usage

### Running the Example Agent

```bash
python main.py
```

### Example Interactions (Data Generation Demo)

```
You: Generate users named John, Jane, Mike and save to users.json
You: Create 5 users with last names Smith, Jones with gmail.com emails
You: Make users aged 25-35 and save to employees.json
You: Read users.json
```

### 🔧 Customizing for Your Use Case

To create your own agent, simply:

1. **Define your tools** using the `@tool` decorator:
```python
@tool
def your_custom_function(param1: str, param2: int) -> str:
    """Clear description of what this tool does."""
    # Your logic here
    return "Result"
```

2. **Update the tool list**:
```python
TOOLS = [your_custom_function, another_function]
```

3. **Customize the system message** to define your agent's role:
```python
SYSTEM_MESSAGE = "You are [AgentName], a helpful assistant that..."
```

That's it! The agent will automatically learn to use your tools based on their docstrings and function signatures.

## 💪 Strengths of This Platform

### 1. **Minimal & Understandable**
- ~160 lines of clean, well-documented Python code
- No complex abstractions or hidden magic—easy to understand and modify
- Perfect learning resource for understanding LangChain agents
- Simple enough for beginners, powerful enough for production

### 2. **Excellent User Experience**
- Users don't need to know function signatures or parameter names
- Natural language processing makes it accessible to non-technical users
- No need for rigid command structures or menus

### 3. **Autonomous Decision Making**
- Agent intelligently fills in missing parameters without constant prompting
- Reduces cognitive load by making sensible defaults
- Handles multi-step workflows automatically (e.g., generate → validate → save)

### 4. **Highly Extensible Architecture**
- Adding new capabilities is as simple as defining a new `@tool` function
- No configuration files or complex setup required
- Agent automatically learns to use new tools from their docstrings
- Tools can be anything: API calls, file operations, database queries, computations

### 5. **Production-Ready Patterns**
- Robust error handling with user-friendly messages
- Comprehensive input validation examples
- Proper type hints for maintainability
- Conversation history management

### 6. **Framework Agnostic Logic**
- Tools are plain Python functions—no vendor lock-in
- Easy to migrate to different LLM providers or frameworks
- Can swap OpenAI for Anthropic, Gemini, or local models with minimal changes

## ⚠️ Current Limitations (By Design)

### Intentional Simplicity
This boilerplate prioritizes **clarity and learnability** over feature completeness. These limitations are opportunities for you to extend the platform:

### 1. **Basic Tool Set**
- Only 3 example tools provided (by design—add your own!)
- No advanced capabilities out of the box
- Focused on demonstrating patterns, not solving all problems

### 2. **Memory Management**
- Conversation history grows unbounded in long sessions
- May hit token limits with extensive conversations
- No conversation summarization or pruning (implement if needed)

### 3. **Production Features Not Included**
- No authentication or authorization
- No rate limiting or cost controls
- No structured logging or monitoring
- No unit tests (add based on your use case)

### 4. **Single-Session Design**
- No persistence between sessions
- No multi-user support
- No conversation history storage

### 5. **CLI-Only Interface**
- No web UI or API endpoints
- Terminal-based interaction only
- No graphical interface

### 6. **Safety Features**
- Limited input validation (expand based on your tools)
- No transaction support or rollback mechanisms
- No confirmation prompts for destructive operations

**Remember**: These are features you can add based on your specific requirements. The platform provides the foundation—you build the features that matter for your use case.

## 🤖 Why LangChain Agents?

### Why the Agentic Approach

The use of **LangChain agents** with the **ReAct pattern** is well-justified for this project for several reasons:

#### 1. **Dynamic Tool Selection**
The agent autonomously decides which tools to use based on user intent. For example:
- User says "save users" → agent uses `generate_sample_users` + `write_json`
- User says "read users.json" → agent uses `read_json`
- This eliminates the need for rigid command parsing or menu systems

#### 2. **Handling Ambiguity**
Users provide incomplete specifications like "generate 5 users". The agent:
- Identifies missing parameters (names, domains, age ranges)
- Makes intelligent decisions to fill gaps
- Executes multi-step workflows automatically

This would require extensive custom logic without an agent framework.

#### 3. **Natural Language Understanding**
LangChain leverages GPT-4's language capabilities to:
- Parse varied phrasings ("create", "make", "generate", "build")
- Extract intent and parameters from unstructured text
- Provide conversational responses

#### 4. **Extensibility**
Adding new tools is trivial:
```python
@tool
def new_function():
    """Description for the agent"""
    pass
```
The agent automatically learns to use new tools without retraining or configuration changes.

#### 5. **Error Reasoning**
When errors occur, the agent can:
- Understand the error message
- Attempt alternative approaches
- Explain issues to users in natural language

#### 6. **Reduces Development Complexity**
Without agents, this would require:
- Intent classification models
- Entity extraction systems
- Complex state machines for multi-turn conversations
- Explicit workflow orchestration

LangChain abstracts all of this into a unified framework.

### When Agents Might Be Overkill

For simpler use cases (single tool, no conversation, strict inputs), agents add unnecessary complexity and cost. However, for scenarios requiring **natural interaction**, **multi-tool coordination**, and **autonomous decision-making**, agents are the optimal choice.

### Why This Boilerplate?

Building agents from scratch involves understanding multiple concepts: tool calling, conversation management, prompt engineering, error handling, and framework integration. This project provides a **minimal working example** that demonstrates all these patterns in ~160 lines of code, letting you focus on building your domain-specific tools rather than framework plumbing.



## 📝 License

[GPL-3.0 license]

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.