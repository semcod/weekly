# Weekly - Project Quality Analyzer

## AI Cost Tracking

![PyPI](https://img.shields.io/badge/pypi-costs-blue) ![Version](https://img.shields.io/badge/version-0.1.43-blue) ![Python](https://img.shields.io/badge/python-3.9+-blue) ![License](https://img.shields.io/badge/license-Apache--2.0-green)
![AI Cost](https://img.shields.io/badge/AI%20Cost-$0.92-orange) ![Human Time](https://img.shields.io/badge/Human%20Time-15.6h-blue) ![Model](https://img.shields.io/badge/Model-openrouter%2Fqwen%2Fqwen3--coder--next-lightgrey)

- 🤖 **LLM usage:** $0.9157 (14 commits)
- 👤 **Human dev:** ~$1557 (15.6h @ $100/h, 30min dedup)

Generated on 2026-07-06 using [openrouter/qwen/qwen3-coder-next](https://openrouter.ai/qwen/qwen3-coder-next)

---

[![PyPI](https://img.shields.io/pypi/v/weekly?logo=pypi&logoColor=white&style=for-the-badge)](https://pypi.org/project/weekly/)
[![PyPI - Downloads](https://img.shields.io/pypi/dm/weekly?logo=pypi&logoColor=white&style=for-the-badge)](https://pypi.org/project/weekly/)
[![Python Versions](https://img.shields.io/pypi/pyversions/weekly?logo=python&logoColor=white&style=for-the-badge)](https://pypi.org/project/weekly/)
[![License: Apache-2.0](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Documentation](https://img.shields.io/readthedocs/weekly/latest?logo=readthedocs&logoColor=white&style=for-the-badge)](https://weekly.readthedocs.io/)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg?style=for-the-badge&logo=python&logoColor=white)](https://github.com/psf/black)
[![Imports: isort](https://img.shields.io/badge/imports-isort-%231674b1?style=for-the-badge&labelColor=ef8336)](https://pycqa.github.io/isort/)
[![Checked with mypy](http://www.mypy-lang.org/static/mypy_badge.svg?style=for-the-badge)](http://mypy-lang.org/)
[![codecov](https://codecov.io/gh/wronai/weekly/branch/main/graph/badge.svg?token=YOUR-TOKEN-HERE&style=for-the-badge)](https://codecov.io/gh/wronai/weekly)
[![Build Status](https://github.com/wronai/weekly/actions/workflows/tests.yml/badge.svg?style=for-the-badge)](https://github.com/wronai/weekly/actions)
[![CodeQL](https://github.com/wronai/weekly/actions/workflows/codeql-analysis.yml/badge.svg?style=for-the-badge)](https://github.com/wronai/weekly/actions/workflows/codeql-analysis.yml)
[![pre-commit.ci status](https://results.pre-commit.ci/badge/github/wronai/weekly/main.svg?style=for-the-badge)](https://results.pre-commit.ci/latest/github/wronai/weekly/main)
[![Ruff](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/charliermarsh/ruff/main/assets/badge/v2.json&style=for-the-badge)](https://github.com/astral-sh/ruff)
[![CodeFactor](https://www.codefactor.io/repository/github/wronai/weekly/badge?style=for-the-badge)](https://www.codefactor.io/repository/github/wronai/weekly)
[![OpenSSF Scorecard](https://api.securityscorecards.dev/projects/github.com/wronai/weekly/badge?style=for-the-badge)](https://api.securityscorecards.dev/projects/github.com/wronai/weekly)
[![Dependabot](https://img.shields.io/badge/dependabot-enabled-025e8c?style=for-the-badge&logo=dependabot)](https://github.com/dependabot)
[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-2.1-4baaaa.svg?style=for-the-badge)](CODE_OF_CONDUCT.md)
[![Discussions](https://img.shields.io/badge/GitHub-Discussions-5865F2?style=for-the-badge&logo=github&logoColor=white)](https://github.com/wronai/weekly/discussions)
[![Twitter Follow](https://img.shields.io/twitter/follow/wronai?style=for-the-badge&logo=twitter&label=Follow%20%40wronai)](https://twitter.com/wronai)

Weekly is a comprehensive Python project quality analyzer that helps developers maintain high code quality by automatically detecting issues and suggesting improvements. It analyzes various aspects of your Python projects and generates actionable reports with clear next steps.

## ✨ Features

- 🧪 **Test Coverage Analysis**: Check test coverage and test configuration (now parses `coverage.xml`)
- 📚 **Documentation Check**: Verify README, LICENSE, CHANGELOG, and API docs
- 🔄 **CI/CD Integration**: Detect CI/CD configuration and best practices
- 📦 **Dependency Analysis**: Identify outdated or vulnerable dependencies (now with `pip-audit` integration and AST parsing)
- 🛠️ **Code Quality**: Check for code style, formatting, and common issues
- 🔒 **Security Checks**: Detect hardcoded secrets and insecure function usage
- 📦 **Packaging Check**: Verify PEP 517/518 compliance and distribution metadata
- 🚀 **Release Readiness**: Check version consistency and changelog status
- 📊 **Interactive Reports**: Generate detailed reports in multiple formats (JSON, Markdown, Text, HTML)
- 🔍 **Multi-Repo Scanning**: Scan multiple Git repositories with parallel processing
- 📅 **Date-based Filtering**: Flexible date parsing for analyzing recent changes

## 🔍 Git Repository Scanning

Weekly can scan multiple Git repositories in a directory structure and generate comprehensive reports for each one, plus a summary report.

It also extracts **Recent Changes** (commits, files/lines changed, commit type breakdown) and writes a per-repo `changelog.md` into the report directory.

### Basic Usage

```bash
# Scan all Git repositories in ~/github
weekly scan ~/github

# Only show repositories with changes in the last 7 days (default)
weekly scan ~/github --since "7 days ago"

# Specify a custom output directory
weekly scan ~/github -o ./weekly-reports

# Run with 8 parallel jobs for faster scanning
weekly scan ~/github -j 8

# Generate JSON reports instead of HTML
weekly scan ~/github --format json
```

### Recent Changes + changelog.md

When you run `weekly scan ... --since "..."`, the per-repo reports include a **Recent Changes** section and a `changelog.md` file in the repository report directory.

- **If `git-cliff` is available**, Weekly uses it to generate `changelog.md`.
- **If `git-cliff` is not available**, Weekly falls back to an internal summary (commit + diff stats).

Optional installation (recommended) for richer changelog output:

```bash
cargo install git-cliff
```

### Example Output

```
🔍 Scanning Git repositories in /Users/username/github...
✅ Scan complete! Generated reports for 3 repositories.
📊 Summary report: weekly-reports/summary.html

✅ org1/repo1: 5 checks
   ✓ style: Passed
   ✓ code_quality: Passed
   ✓ dependencies: 2 outdated packages found
   ✓ docs: Documentation is 85% complete
   ✓ tests: 92% test coverage
```

### Command Options

```
Usage: weekly scan [OPTIONS] [ROOT_DIR]

  Scan multiple Git repositories and generate reports.

  ROOT_DIR: Directory containing Git repositories (default: current directory)

Options:
  -o, --output PATH      Output directory for reports (default: ./weekly-reports)
  -s, --since TEXT        Only include repositories with changes since this date (e.g., "7 days ago", "2023-01-01")
  --recursive / --no-recursive  Scan directories recursively (default: True)
  -j, --jobs INTEGER      Number of parallel jobs (default: 4)
  -f, --format [html|json|markdown]  Output format (default: html)
  --summary-only          Only generate a summary report, not individual reports
  -v, --verbose           Show detailed output
  --help                  Show this message and exit.
```

### Programmatic Usage

```python
from pathlib import Path
from datetime import datetime, timedelta
from weekly import GitScanner

# Create a scanner instance
scanner = GitScanner(
    root_dir=Path.home() / "github",
    output_dir="weekly-reports",
    since=datetime.now() - timedelta(days=7),
    recursive=True,
    jobs=4
)

# Run the scan
results = scanner.scan_all()

# Process results
for result in results:
    print(f"{result.repo.org}/{result.repo.name}:")
    for name, check in result.results.items():
        status = "✓" if check.is_ok else "✗"
        print(f"  {status} {name}: {check.message}")
```

## 🚀 Installation

### Using pip

```bash
pip install weekly
```

### Using Poetry (recommended)

```bash
poetry add weekly
```

### For Development

```bash
# Clone the repository
git clone https://github.com/wronai/weekly.git
cd weekly

# Install with Poetry
poetry install --with dev

# Install pre-commit hooks
pre-commit install

# Activate the virtual environment
poetry shell
```

## Usage

### Basic Usage

Analyze a Python project:

```bash
weekly analyze /path/to/your/project
```

### Command Line Options

```
Usage: weekly analyze [OPTIONS] PROJECT_PATH

  Analyze a Python project and provide quality insights.

  PROJECT_PATH: Path to the project directory (default: current directory)

Options:
  -f, --format [text|json|markdown]  Output format (default: text)
  -o, --output FILE                  Output file (default: stdout)
  --show-suggestions / --no-suggestions
                                      Show improvement suggestions (default: true)
  -v, --verbose                      Show detailed output
  --help                             Show this message and exit.
```

### Examples

1. Analyze current directory and show results in the terminal:
   ```bash
   weekly analyze .
   ```

2. Generate a Markdown report:
   ```bash
   weekly analyze -f markdown -o report.md /path/to/project
   ```

3. Generate a JSON report for programmatic use:
   ```bash
   weekly analyze -f json -o report.json /path/to/project
   ```

## Output Example

### Text Output

```
📊 Weekly Project Analysis Report
================================================================================
Project: example-project
Generated: 2025-06-07 12:34:56

Summary:
--------------------------------------------------------------------------------
✅ 5 passed
⚠️  3 warnings
❌ 1 errors

Detailed Results:
--------------------------------------------------------------------------------
✅ Project Structure
  Found Python project with proper structure

✅ Dependencies
  All dependencies are properly specified
  
⚠️  Test Coverage
  Test coverage is below 80% (currently 65%)
  
  Suggestions:
    • Add more test cases to improve coverage
    • Consider using pytest-cov for coverage reporting

❌ Documentation
  Missing API documentation
  
  Suggestions:
    • Add docstrings to all public functions and classes
    • Consider using Sphinx or MkDocs for API documentation

Recommended Actions:
--------------------------------------------------------------------------------
1. Improve Test Coverage
   • Add unit tests for untested modules
   • Add integration tests for critical paths
   • Set up code coverage reporting in CI

2. Enhance Documentation
   • Add docstrings to all public APIs
   • Create API documentation using Sphinx or MkDocs
   • Add examples to the README
```

### Programmatic Usage

```python
from pathlib import Path
from weekly import analyze_project
from weekly.core.report import Report

# Analyze a project
report = analyze_project(Path("/path/to/your/project"))

# Get report as dictionary
report_data = report.to_dict()

# Get markdown report
markdown = report.to_markdown()

# Print summary
print(f"✅ {report.summary['success']} passed")
print(f"⚠️  {report.summary['warnings']} warnings")
print(f"❌ {report.summary['errors']} errors")

# Get suggestions
for suggestion in report.get_suggestions():
    print(f"\n{suggestion['title']}:")
    for item in suggestion['suggestions']:
        print(f"  • {item}")

### Most Active Files

- `src/main.py`: 12 changes
- `tests/test_main.py`: 8 changes
- `README.md`: 5 changes

### Languages Used

- `.py`: 15 files
- `.md`: 3 files
- `.json`: 2 files

## 📋 Next Steps

- [ ] Add tests for recent changes
- [ ] Refactor large files: src/utils.py, src/processor.py...

## 📜 Recent Commits

- `a1b2c3d` Fix bug in data processing (2023-05-15)
- `f4e5d6a` Add new feature X (2023-05-14)
- `b3c4d5e` Update documentation (2023-05-13)
- `c6d7e8f` Refactor module Y (2023-05-12)
- `d9e0f1a` Initial commit (2023-05-10)

*[View full history in the JSON file]*
```

## Development

### Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/wronai/weekly.git
   cd weekly
   ```

2. Install dependencies (recommended):
   ```bash
   poetry install --with dev
   ```

### Running Tests

```bash
poetry run pytest
```

### Code Style

This project uses:
- Black for code formatting
- isort for import sorting
- flake8 for linting
- mypy for type checking

Run all checks:

```bash
black .
isort .
flake8
mypy .
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

Licensed under Apache-2.0.
## Author

Tom Sapletta
## Acknowledgments

- Built with ❤️ by the WronAI team
- Inspired by various Git analysis tools

<!-- taskill:status:start -->

## Status

_Last updated by [taskill](https://github.com/oqlos/taskill) at 2026-04-25 13:49 UTC_

| Metric | Value |
|---|---|
| HEAD | `8545fd9` |
| Coverage | 73.0% |
| Failing tests | — |
| Commits in last cycle | 21 |

> Added a deep code analysis engine with seven supporting modules, introduced a CLI with validation and API hooks, and substantially improved test coverage and documentation. Several refactors and report-style improvements for LLM output were applied, and auto_update_config was disabled to preserve manual test strategy.

<!-- taskill:status:end -->
