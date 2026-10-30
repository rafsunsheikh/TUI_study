# TUI study

A list of the terminal apps (TUIs) we are building. Each TUI lives in its own repository; this repository only keeps the list and the conventions they share.

A TUI is an app that runs inside a terminal window but behaves like a full app, with panels, lists and keyboard shortcuts. `htop` and `lazygit` are well-known examples.

## The TUIs

| TUI | What it does | Status | Repository |
|---|---|---|---|
| **vizdesk** | Scans CSV and Excel files, suggests cleaning steps and charts by fixed rules (no LLM), and draws PNG figures in a grid you choose. Saves a redraw recipe, a notebook script and alt text with every figure. | v0.2.0 on [PyPI](https://pypi.org/project/vizdesk/) (`pipx install vizdesk`) and [npm](https://www.npmjs.com/package/vizdesk) (`npm install -g vizdesk`). Homebrew coming. | [rafsunsheikh/vizdesk](https://github.com/rafsunsheikh/vizdesk) |

## How we build them

These are the defaults every TUI here starts from. A TUI can depart from them when it has a reason.

| Topic | Default |
|---|---|
| Language and UI | Python with Textual for the terminal UI and Rich for command-line output [1][2]. |
| Two ways in | A full TUI, plus a command line with the same features, so the tool also works in scripts and CI. |
| Suggestions | Fixed rules and statistics on the user's data, each with a plain reason. No LLM unless the TUI is about one. |
| Your files | Never changed. Results go to an output folder. |
| Tests | pytest, including a headless run of the TUI with Textual's test pilot. Checked on more than one Python version. |
| Real-world check | Run on popular public datasets or inputs, compare with what practitioners do, and keep every fix as a regression test. |
| Distribution | One Python package on PyPI; npm and Homebrew packages are thin wrappers that install it. |
| Licence | MIT. |

## Adding a new TUI

1. Create its own repository (for example `rafsunsheikh/<name>`), public unless there is a reason not to be.
2. Add a row to the table above: name, what it does in one or two sentences, status, and the repository link.
3. Update the status when it changes (for example "published on PyPI").

## References

1. Textual documentation, https://textual.textualize.io
2. Rich documentation, https://rich.readthedocs.io
