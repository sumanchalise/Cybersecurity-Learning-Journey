# OverTheWire Bandit Progress Log

## Overview

This document records my progress through the OverTheWire Bandit wargame as part of my cybersecurity learning journey.

The goal of Bandit is to develop Linux command-line skills, file enumeration techniques, text searching, and basic system navigation.

> Note: This repository documents the methodology, commands used, observations, and outcomes for educational purposes.

---

# Level 0 → Level 1

### Objective

Connect to the Bandit server and retrieve the password stored in the `readme` file.

### Commands Used

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

### Outcome

Successfully connected to the remote system and obtained the password for the next level.

Password Retrieved:

```text
6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR
```

---

# Level 1 → Level 2

### Objective

Read a file named `-`.

### Commands Used

```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
ls
cat ./-
```

### Key Learning

Files with special names can be referenced using relative paths.

### Password Retrieved

```text
PK8fYLZg2hnHSz83plBL1iEPKdD3QToB
```

---

# Level 2 → Level 3

### Objective

Read a file whose name contains spaces.

### Commands Used

```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
ls
cat -- "--spaces in this filename--"
```

### Key Learning

Special characters and spaces in filenames require proper quoting.

### Password Retrieved

```text
7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME
```

---

# Level 3 → Level 4

### Objective

Locate a hidden file.

### Commands Used

```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
ls
ls -a
cat ...Hiding-From-You
```

### Key Learning

Hidden files can be displayed using the `-a` option.

### Password Retrieved

```text
xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq
```

---

# Level 4 → Level 5

### Objective

Identify the only human-readable file.

### Commands Used

```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
ls
file -- *
cat ./-file07
```

### Key Learning

The `file` command helps identify file types before attempting to read them.

### Password Retrieved

```text
6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG
```

---

# Level 5 → Level 6

### Objective

Find a file matching specific criteria.

### Commands Used

```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
find . -type f -size 1033c ! -executable
```

### Key Learning

The `find` command can search based on size, type, and permissions.

### Password Retrieved

```text
pXa26xhMWaC2SvDotA4r9EgZkulOeSBW
```

---

# Level 6 → Level 7

### Objective

Find a file owned by a specific user and group.

### Commands Used

```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
find / -type f -size 33c -user bandit7 -group bandit6
```

### Key Learning

File ownership metadata can be used for targeted searches.

### Password Retrieved

```text
Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3
```

---

# Level 7 → Level 8

### Objective

Locate the password stored beside the word "millionth".

### Commands Used

```bash
ssh bandit7@bandit.labs.overthewire.org -p 2220
grep "millionth" data.txt
```

Alternative commands explored:

```bash
grep -i "millionth" data.txt
sort data.txt
du
```

### Key Learning

`grep` is a powerful utility for searching text patterns within files.

### Password Retrieved

```text
VR1ljMayciFxbnUokuQmJFw6QC9VKtub
```

---

# Command Reference

| Command | Purpose                                            |
| ------- | -------------------------------------------------- |
| `ssh`   | Connects securely to a remote system.              |
| `ls`    | Lists files and directories.                       |
| `ls -a` | Lists all files, including hidden files.           |
| `cat`   | Displays file contents.                            |
| `file`  | Identifies a file's type.                          |
| `find`  | Searches for files based on conditions.            |
| `grep`  | Searches text for matching patterns.               |
| `sort`  | Sorts file contents alphabetically or numerically. |
| `du`    | Displays disk usage information.                   |

---

# grep Options Learned

| Option                          | Purpose                                 |
| ------------------------------- | --------------------------------------- |
| `grep -i`                       | Case-insensitive search.                |
| `grep -c`                       | Count matching lines.                   |
| `grep -l`                       | Show only filenames containing matches. |
| `grep -w`                       | Match complete words only.              |
| `grep -o`                       | Display only the matching text.         |
| `grep -n`                       | Show line numbers with matches.         |
| `grep -v`                       | Show lines that do not match.           |
| `grep ^pattern`                 | Match lines starting with a pattern.    |
| `grep pattern$`                 | Match lines ending with a pattern.      |
| `grep -e`                       | Search using multiple patterns.         |
| `grep -A 3`                     | Show 3 lines after a match.             |
| `grep -B 3`                     | Show 3 lines before a match.            |
| `grep -C 3`                     | Show 3 lines before and after a match.  |
| `grep -f patterns.txt file.txt` | Use patterns stored in a file.          |

---

## Skills Developed

- Linux navigation
- File handling
- Hidden file discovery
- File type identification
- Enumeration techniques
- Text searching
- Pattern matching
- Basic system reconnaissance
- Secure remote access using SSH
