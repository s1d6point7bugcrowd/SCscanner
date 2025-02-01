# SCscanner

**Version 1.3**

This project is an **automated source code vulnerability scanner** designed for **bug bounty research** and **security analysis**. It scans JavaScript/TypeScript code for security vulnerabilities using multiple static analysis techniques, including **regex-based scanning, Semgrep integration, AST-based analysis, and taint analysis**. It leverages **asynchronous processing with concurrency controls** for high-performance scanning and includes **iterative AST traversal** for efficiency on large codebases.

---

## 🚀 Features

### 🔍 Multi-Technique Scanning:

- **Regex-Based Scanning:** Quickly identifies potentially dangerous patterns using **regular expressions**.
- **Semgrep Integration:** Runs **Semgrep** to perform rule-based static analysis.
- **AST-Based Analysis:** Uses Node.js with **Esprima** to parse code into an AST and checks for:
  - Cross-Site Scripting (**XSS**)
  - Insecure deserialization
  - Prototype pollution
  - Server-Side Request Forgery (**SSRF**)
  - Regular Expression Denial of Service (**ReDoS**)
  - Open Redirect
  - Command Injection
  - Path Traversal

- **Taint Analysis:** Tracks the flow of **potentially tainted data** through:
  - Assignments & Variable Declarations
  - Function Calls & Arguments
  - Member Expressions & Object Properties
  - Arrays & Template Literals
  - Binary Expressions & User Input Sources

### ⚡ Performance Optimizations:

- **Iterative AST Traversal:** Avoids deep recursion to improve performance on large files.
- **Concurrency:** Async processing with `asyncio` and `aiolimiter` enables **efficient parallel scanning**.
- **Configurable Maximum Concurrency:** Limits the number of concurrent analyses for optimized performance.

### 🛠️ Configurable Analysis:

- **Dangerous Patterns from JSON File:** Easily update patterns in `dangerous_patterns.json`.
- **Custom Semgrep Rules:** Uses **Semgrep** for additional vulnerability detection.
- **Optional Syntax Highlighting:** Uses **Pygments** (if installed) to enhance output readability.

### 📋 Comprehensive Reporting:

- **Findings Grouped by Type:** Regex-based, Semgrep, Contextual (AST), and Taint Analysis.
- **Detailed Output:** Includes file name, line number, affected code snippet, and vulnerability details.
- **Severity Levels:** Each finding is assigned a severity level (**Critical, High, Medium, Low**).
- **Contextual Code Snippets:** Displays **surrounding lines** to help understand findings.
- **Support for Multiple Output Formats (Planned):** Future support for **JSON, SARIF, and HTML reporting**.

---

## 📦 Installation

### Prerequisites:

- Python **3.8+**
- **Node.js** (for AST-based analysis using Esprima)
- **Semgrep** (optional but recommended)
- **Pygments** (optional for syntax highlighting)

### Install Dependencies:

```bash
pip install -r requirements.txt

🔧 Usage
Basic Usage:

python scanner.py --url <package-url>

Example:

python scanner.py --url https://www.npmjs.com/package/example


Running a Local JavaScript/TypeScript Project:

python scanner.py --directory <path-to-project>

python scanner.py --directory ./my-js-project


Options:
Argument	Description
--url	Analyze an NPM package from a provided URL.
--directory	Scan a local directory for vulnerabilities.
--output	Save results to a file (Planned Feature).
--highlight	Enable syntax highlighting in the report (if Pygments is installed).


🙌 Acknowledgments

Special thanks to:

    Esprima for AST parsing.
    Semgrep for rule-based security analysis.
    The security research community for developing best practices in static analysis.
