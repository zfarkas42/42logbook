# 42 Heilbronn Project Logbook

A retro terminal-style project management and log-keeping tool built for students at 42 Heilbronn. Track your projects, write log entries, manage deadlines, and keep a to-do list — all from the command line, with a phosphor-green aesthetic.

---

## Features

- **Project management** — add, edit, delete, and search projects with subject, milestone, deadline, notes, and team members
- **Log entries** — per-project log files with a two-panel browser (entry body on the left, entry list on the right)
- **Deadline countdown** — always shows days and hours left to submit on the main screen, colour-coded by urgency
- **To-do list** — quick tasks that appear on the main screen every time you open the logbook
- **Team members** — up to 10 members per project with full name and intra login
- **Editor integration** — auto-detects `micro`, `nano`, `vim`, `vi`, `emacs`; or set your own preference in Settings
- **Fireworks screensaver** — activates after configurable idle timeout
- **Boot sequence** — retro terminal startup with project and deadline summary
- **All data stored locally** — plain binary files, no database, no internet required

---

## Requirements

- GCC
- A POSIX-compatible system (Linux / macOS)
- A terminal that supports ANSI escape codes

---

## Compile & Run

```bash
gcc logbook.c -o logbook -lm
./logbook
```

---

## Navigation

The menus are keyboard-driven:

| Key | Action |
|-----|--------|
| `↑` / `↓` | Move selection |
| `Enter` | Confirm |
| `Esc` | Cancel / go back |
| Letter | Jump to first item starting with that letter |

Inside the log browser:

| Key | Action |
|-----|--------|
| `↑` / `↓` | Select entry |
| `a` | Add new entry |
| `r` | Read selected entry |
| `e` | Edit selected entry |
| `d` | Delete selected entry |
| `i` | Show project info |
| `b` / `Esc` | Back to main menu |
| `q` | Return from entry viewer |

---

## Data Files

All data is stored in binary files in the same directory as the binary. **Keep all of these files together** — moving just `logbook.dat` without the log files will leave your entries behind.

| File | Contents |
|------|----------|
| `logbook.dat` | All projects (name, subject, milestone, deadline, notes, team) and the to-do list |
| `settings.dat` | Editor preference and screensaver settings |
| `logs_0.dat`, `logs_1.dat`, … | Log entries for each project, one file per project numbered from 0 |

To back up or sync your data, copy **all** of these files together.

---

## Settings

Access via the main menu → **Settings**:

- **Preferred editor** — set `nano`, `vim`, `micro`, etc. Falls back to auto-detection or `$EDITOR` if not set.
- **Screensaver** — enable/disable the fireworks animation
- **Screensaver timeout** — idle time in minutes before the screensaver activates (1–60)

---

## Project Structure

```
logbook.c       # entire program – single file, no dependencies beyond libc and libm
logbook.dat     # created on first run
settings.dat    # created on first run
logs_N.dat      # created when the first log entry is added to project N
```

---

## Deadline Colours

| Colour | Meaning |
|--------|---------|
| Green | Plenty of time |
| Amber | Under 7 days |
| Red | Under 24 hours or overdue |

---

## License

Do whatever you want with it.
