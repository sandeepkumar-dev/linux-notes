# 🐧 Linux — Complete Notes

> **Topic:** Linux for Developers & DevOps Engineers
> **Level:** Beginner to Intermediate
> **Environment:** AWS EC2 / Any Linux Terminal

---

## 📋 Table of Contents

1. [Why Learn Linux?](#1-why-learn-linux)
2. [Linux Operating System Overview](#2-linux-operating-system-overview)
3. [Linux History](#3-linux-history)
4. [Linux Architecture](#4-linux-architecture)
5. [Linux Distributions](#5-linux-distributions)
6. [Setup — Getting a Linux Machine](#6-setup--getting-a-linux-machine)
7. [Basic Commands](#7-basic-commands)
8. [File & Directory Commands](#8-file--directory-commands)
9. [File Operations](#9-file-operations)
10. [Viewing File Content](#10-viewing-file-content)
11. [Search — `grep` Command](#11-search--grep-command)
12. [Word Count — `wc` Command](#12-word-count--wc-command)
13. [VI Editor](#13-vi-editor)
14. [SED — Stream Editor](#14-sed--stream-editor)
15. [User Management](#15-user-management)
16. [Group Management](#16-group-management)
17. [File Permissions](#17-file-permissions)
18. [File Ownership — `chown`](#18-file-ownership--chown)
19. [Find Command](#19-find-command)
20. [Zip & Unzip](#20-zip--unzip)
21. [Networking Commands](#21-networking-commands)
22. [Package Managers](#22-package-managers)
23. [Quick Reference Tables](#23-quick-reference-tables)

---

## 1. Why Learn Linux?

Linux is the backbone of modern IT infrastructure. Whether you are a developer deploying an application or a DevOps engineer managing pipelines, Linux knowledge is non-negotiable.

| Reason | Detail |
|--------|--------|
| **Servers run on Linux** | Stable, reliable, and cost-effective for production |
| **DevOps tooling** | Docker, Kubernetes, Jenkins, Ansible, Terraform all run on Linux |
| **Cloud computing** | AWS, Azure, and GCP provide Linux-based virtual machines |
| **Security model** | User and permission system reduces attack surface |
| **Performance** | Lightweight, fast, and efficient compared to other operating systems |
| **Open source** | Free to use, modify, and distribute |

---

## 2. Linux Operating System Overview

Linux is a **community-driven, open-source operating system** maintained by developers worldwide.

| Feature | Description |
|---------|-------------|
| **Open source** | Source code is freely available — anyone can modify and distribute it |
| **CLI-based** | Command Line Interface gives powerful, precise control over the system |
| **Highly secure** | Less prone to malware and attacks compared to other OS |
| **Widely used** | Powers servers, databases, cloud infrastructure, and production systems |
| **Cost-effective** | Free to use — no licensing fees |

---

## 3. Linux History

| Event | Detail |
|-------|--------|
| **Creator** | Linus Torvalds |
| **Year** | 1991 |
| **Inspiration** | UNIX — but UNIX was expensive and restricted |
| **Base reference** | MINIX OS (used as a learning and reference system) |
| **Goal** | Create a free, open alternative to UNIX |
| **Name origin** | **Lin**us + **Unix** = **Linux** |

> **Note:** Linux is just the **kernel** — the core. A full operating system built around it is called a **distribution** (distro).

---

## 4. Linux Architecture

Linux is organized in layers, from user-facing applications down to physical hardware.

```
┌─────────────────────────────────┐
│         Applications            │  ← User programs (browser, editor, etc.)
├─────────────────────────────────┤
│            Shell                │  ← Interface between user and kernel
│     (bash, zsh, sh, etc.)       │     Interprets your commands
├─────────────────────────────────┤
│            Kernel               │  ← Core of Linux
│  (CPU, Memory, Device mgmt)     │     Manages hardware resources
├─────────────────────────────────┤
│           Hardware              │  ← Physical components (CPU, RAM, Disk)
└─────────────────────────────────┘
```

| Layer | Role |
|-------|------|
| **Applications** | Programs the user runs (Python script, web server, etc.) |
| **Shell** | Reads user commands and passes them to the kernel |
| **Kernel** | Core of the OS — manages CPU, memory, and devices |
| **Hardware** | The physical machine |

---

## 5. Linux Distributions

Because Linux is open-source, anyone can take the Linux kernel and build their own customized operating system around it. These are called **distributions** (or **distros**).

There are **600+ distributions** available. Below are the most commonly used:

| Distribution | Best For |
|-------------|----------|
| **Ubuntu** | Beginners — most popular, large community |
| **Red Hat (RHEL)** | Enterprise environments, paid support |
| **Debian** | Stability and security |
| **Fedora** | Latest features, upstream for RHEL |
| **Kali Linux** | Cybersecurity and penetration testing |
| **Amazon Linux** | Optimized for AWS cloud environments |
| **CentOS** | Free alternative to RHEL (community edition) |

> For DevOps and cloud work, **Ubuntu** and **Amazon Linux** are the most commonly encountered.

---

## 6. Setup — Getting a Linux Machine

You have three options to get a Linux environment:

| Option | Method | Best For |
|--------|--------|----------|
| **Option 1** | Install directly on hardware using a bootable USB | Full performance, personal machine |
| **Option 2** | Virtual Machine — VirtualBox or VMware | Safe isolated environment on Windows/Mac |
| **Option 3 (Recommended)** | Cloud — Launch a Linux VM on AWS EC2 | Real-world practice, accessible from anywhere |

> **Recommended:** Use **AWS EC2** to launch a free-tier Linux instance. This mirrors real production environments.

---

## 7. Basic Commands

These are the first commands you should know — they help you understand where you are and what the system looks like.

| Command | Description | Example Output |
|---------|-------------|---------------|
| `whoami` | Shows the currently logged-in user | `ubuntu` |
| `pwd` | Prints the current working directory | `/home/ubuntu` |
| `date` | Shows the current date and time | `Sat Mar 28 10:30:00 UTC 2026` |
| `cal` | Displays the calendar for the current month | Monthly calendar |
| `clear` | Clears the terminal screen | (blank screen) |

```bash
$ whoami
ubuntu

$ pwd
/home/ubuntu

$ date
Sat Mar 28 10:30:00 UTC 2026
```

---

## 8. File & Directory Commands

### Creating and Removing Directories

| Command | Description |
|---------|-------------|
| `mkdir dirname` | Create a new directory |
| `mkdir -p a/b/c` | Create nested directories in one command |
| `rmdir dirname` | Remove an **empty** directory |
| `rm -rf dirname` | Remove a directory and **all its contents** (use carefully) |

```bash
mkdir projects              # create a folder
mkdir -p projects/java/src  # create nested folders at once
rmdir empty-folder          # only works if folder is empty
rm -rf old-project          # permanently deletes everything inside
```

> **Warning:** `rm -rf` is irreversible. There is no recycle bin in Linux.

---

### Listing Files

| Command | Description |
|---------|-------------|
| `ls` | List files and folders in current directory |
| `ls -l` | Detailed list with permissions, size, owner, date |
| `ls -la` | Detailed list including hidden files (files starting with `.`) |
| `ls -lh` | Human-readable file sizes (KB, MB, GB) |

```bash
$ ls
documents  downloads  projects

$ ls -l
drwxr-xr-x 2 ubuntu ubuntu 4096 Mar 28 10:00 projects
-rw-r--r-- 1 ubuntu ubuntu  512 Mar 28 09:00 notes.txt

$ ls -la
drwxr-xr-x  5 ubuntu ubuntu 4096 Mar 28 10:00 .
drwxr-xr-x 20 root   root   4096 Mar 28 08:00 ..
-rw-r--r--  1 ubuntu ubuntu  512 Mar 28 09:00 .bashrc
```

---

### Navigating Directories

| Command | Description |
|---------|-------------|
| `cd dirname` | Move into a directory |
| `cd ..` | Move up one level (parent directory) |
| `cd ~` | Go to home directory |
| `cd /` | Go to root directory |
| `cd -` | Go back to previous directory |

```bash
cd projects         # move into projects folder
cd ..               # go back to parent
cd ~                # go to /home/ubuntu
cd /etc             # go to /etc (system config folder)
```

---

## 9. File Operations

### Creating Files

| Command | Description |
|---------|-------------|
| `touch filename.txt` | Create an empty file (or update timestamp if exists) |
| `touch a.txt b.txt` | Create multiple files at once |

```bash
touch notes.txt
touch file1.txt file2.txt file3.txt
```

---

### Viewing File Content

| Command | Description |
|---------|-------------|
| `cat file.txt` | Print entire file content to terminal |
| `cat -n file.txt` | Print content with line numbers |
| `tac file.txt` | Print content in **reverse** order (last line first) |

```bash
cat notes.txt
cat -n notes.txt     # shows line numbers
tac notes.txt        # last line appears first
```

---

### Copying, Moving, Renaming

| Command | Description |
|---------|-------------|
| `cp file1.txt file2.txt` | Copy file1 and name the copy file2 |
| `cp -r folder1 folder2` | Copy an entire folder recursively |
| `mv oldname.txt newname.txt` | Rename a file |
| `mv file.txt /tmp/` | Move file to a different directory |
| `rm file.txt` | Delete a file permanently |

```bash
cp notes.txt notes-backup.txt
cp -r projects projects-backup
mv draft.txt final.txt
mv final.txt /home/ubuntu/documents/
rm unwanted.txt
```

---

## 10. Viewing File Content

When files are large, you don't want to print everything with `cat`. Use these commands instead:

| Command | Description |
|---------|-------------|
| `head file.txt` | Show first **10 lines** |
| `head -n 20 file.txt` | Show first 20 lines |
| `tail file.txt` | Show last **10 lines** |
| `tail -n 20 file.txt` | Show last 20 lines |
| `tail -f file.txt` | **Follow** file in real-time (great for log monitoring) |
| `less file.txt` | Paginate through large files (press `q` to quit) |
| `more file.txt` | Similar to less but scroll forward only |

```bash
head server.log           # first 10 lines
tail server.log           # last 10 lines
tail -f /var/log/syslog   # watch live log updates (Ctrl+C to stop)
less bigfile.txt          # scroll through — press q to exit
```

> **Tip:** `tail -f` is the most used command for **real-time log monitoring** in production debugging.

---

## 11. Search — `grep` Command

`grep` (Global Regular Expression Print) searches for a pattern inside a file or output.

### Basic Syntax

```bash
grep "pattern" filename
```

### Common Options

| Command | Description |
|---------|-------------|
| `grep "error" app.log` | Find lines containing "error" |
| `grep -i "error" app.log` | Case-insensitive search |
| `grep -n "error" app.log` | Show matching line numbers |
| `grep -r "error" /var/log/` | Search recursively through all files in a directory |
| `grep -v "error" app.log` | Show lines that do **not** match |
| `grep -c "error" app.log` | Count the number of matching lines |

```bash
grep "ERROR" server.log
grep -i "null pointer" app.log   # catches NullPointer, nullpointer, etc.
grep -n "timeout" app.log        # know exactly which line to investigate
grep -r "config" /etc/           # search across all files in /etc
```

### Combining `grep` with Other Commands

```bash
cat app.log | grep "ERROR"        # pipe cat output into grep
ps aux | grep "java"              # find all running Java processes
```

> **Tip:** `grep` is one of the most powerful commands for **log analysis and debugging** on servers.

---

## 12. Word Count — `wc` Command

`wc` (Word Count) counts lines, words, and characters in a file.

| Command | Description |
|---------|-------------|
| `wc file.txt` | Shows **lines**, **words**, and **characters** |
| `wc -l file.txt` | Line count only |
| `wc -w file.txt` | Word count only |
| `wc -c file.txt` | Character/byte count only |

```bash
$ wc notes.txt
  42  310  1850 notes.txt
# 42 lines, 310 words, 1850 characters

$ wc -l server.log
2048 server.log    # 2048 lines in the log file
```

**Practical use — count errors in a log:**

```bash
grep "ERROR" app.log | wc -l    # how many ERROR lines are there?
```

---

## 13. VI Editor

`vi` (Visual Editor) is the default text editor available on almost every Linux system. It is powerful but has a learning curve due to its **modal** design.

### Modes

| Mode | How to Enter | Purpose |
|------|-------------|---------|
| **Command Mode** | Default (press `Esc` anytime) | Navigate, delete, copy, paste |
| **Insert Mode** | Press `i` | Type and edit text |

### Opening and Saving

```bash
vi filename.txt       # open or create file
```

### Essential Commands

| Action | Command (in Command Mode) |
|--------|--------------------------|
| Enter insert mode | `i` |
| Go back to command mode | `Esc` |
| Save and exit | `:wq` |
| Exit **without** saving | `:q!` |
| Save without exiting | `:w` |
| Delete current line | `dd` |
| Copy current line | `yy` |
| Paste copied line | `p` |
| Go to line number | `:10` (goes to line 10) |
| Search for text | `/pattern` then press Enter |
| Go to beginning of file | `gg` |
| Go to end of file | `G` |

### Quick Workflow

```bash
vi app.conf          # 1. Open file
i                    # 2. Press i to enter insert mode
# make your edits
Esc                  # 3. Press Esc to exit insert mode
:wq                  # 4. Save and quit
```

> **Tip:** If you get stuck in vi, press `Esc` and then type `:q!` to exit without saving.

---

## 14. SED — Stream Editor

`sed` is a powerful command-line tool for **searching, replacing, inserting, and deleting text** in files — without opening them in an editor. It is widely used in **automation and scripting**.

### Basic Syntax

```bash
sed 'operation' filename
```

### Common Operations

| Command | Description |
|---------|-------------|
| `sed 's/old/new/' file.txt` | Replace **first** occurrence per line |
| `sed 's/old/new/g' file.txt` | Replace **all** occurrences (`g` = global) |
| `sed -i 's/old/new/g' file.txt` | Replace in-place — **modifies the actual file** |
| `sed -i '1d' file.txt` | Delete line 1 |
| `sed -i '2,5d' file.txt` | Delete lines 2 through 5 |
| `sed -n '5,10p' file.txt` | Print only lines 5 to 10 |

```bash
# Replace "linux" with "unix" everywhere in the file
sed 's/linux/unix/g' notes.txt

# Permanently change the file (modify in place)
sed -i 's/localhost/192.168.1.1/g' config.properties

# Delete the first line (e.g., remove a header)
sed -i '1d' data.csv

# Preview lines 100 to 200 of a large log file
sed -n '100,200p' server.log
```

> **Tip:** Always test `sed` **without** `-i` first to preview changes before modifying the actual file.

---

## 15. User Management

Linux is a **multi-user system**. Each user has their own home directory, files, and permissions.

### Important Files

| File | Purpose |
|------|---------|
| `/etc/passwd` | Stores user account information (username, home dir, shell) |
| `/etc/shadow` | Stores encrypted passwords |
| `/etc/group` | Stores group information |

### Commands

| Command | Description |
|---------|-------------|
| `sudo useradd username` | Create a new user |
| `sudo passwd username` | Set or change a user's password |
| `su username` | Switch to another user |
| `sudo userdel username` | Delete a user |
| `sudo userdel -r username` | Delete user **and** their home directory |
| `id username` | Show user's UID and group memberships |
| `whoami` | Show currently logged-in user |

```bash
sudo useradd john           # create user
sudo passwd john            # set password for john
su john                     # switch to john
sudo userdel john           # delete user
sudo userdel -r john        # delete user and home directory

id john
# uid=1001(john) gid=1001(john) groups=1001(john),27(sudo)
```

> **Note:** `sudo` (Super User Do) allows a permitted user to run a command as the root (administrator) user.

---

## 16. Group Management

Groups allow you to give **shared permissions** to multiple users at once.

| Command | Description |
|---------|-------------|
| `sudo groupadd groupname` | Create a new group |
| `sudo usermod -aG groupname username` | Add user to a group (`-a` = append, `-G` = group) |
| `sudo gpasswd -d username groupname` | Remove user from a group |
| `getent group groupname` | View members of a group |
| `groups username` | Show all groups a user belongs to |

```bash
sudo groupadd devs                  # create group
sudo usermod -aG devs john          # add john to devs group
getent group devs                   # list members of devs

groups john
# john : john sudo devs
```

> **Tip:** After adding a user to a group, they must **log out and back in** for the change to take effect.

---

## 17. File Permissions

Every file and directory in Linux has a set of **permissions** that control who can read, write, or execute it.

### Permission Types

| Symbol | Permission | Meaning |
|--------|-----------|---------|
| `r` | Read | View file content or list directory |
| `w` | Write | Modify file or add/remove files in directory |
| `x` | Execute | Run file as a program or enter a directory |
| `-` | No permission | Access denied |

### Permission Structure

```
-rwxr-xr--
│└──┴──┴──
│  │  │  └── Others (everyone else)
│  │  └───── Group
│  └──────── Owner/User
└─────────── File type (- = file, d = directory, l = link)
```

**Example breakdown:**

```
-rwxr-xr--
```

| Who | Permissions | Meaning |
|-----|------------|---------|
| Owner | `rwx` | Can read, write, and execute |
| Group | `r-x` | Can read and execute, cannot write |
| Others | `r--` | Can only read |

---

### Numeric (Octal) Permissions

Each permission has a numeric value:

| Permission | Value |
|-----------|-------|
| `r` (read) | `4` |
| `w` (write) | `2` |
| `x` (execute) | `1` |
| `-` (none) | `0` |

Add the values together for each group:

| Octal | Permissions | Meaning |
|-------|------------|---------|
| `7` | `rwx` | Full access |
| `6` | `rw-` | Read and write |
| `5` | `r-x` | Read and execute |
| `4` | `r--` | Read only |
| `0` | `---` | No access |

---

### `chmod` — Change Permissions

```bash
# Using numeric mode
chmod 755 script.sh     # Owner: rwx, Group: r-x, Others: r-x
chmod 644 notes.txt     # Owner: rw-, Group: r--, Others: r--
chmod 600 secret.txt    # Owner: rw-, Group: ---, Others: ---

# Using symbolic mode
chmod u+x script.sh     # add execute for owner (u = user/owner)
chmod g-w file.txt      # remove write from group
chmod o+r file.txt      # add read for others
chmod a+x script.sh     # add execute for all (a = all)
```

### Common Permission Sets

| Command | Octal | Who can do what |
|---------|-------|-----------------|
| `chmod 777` | `rwxrwxrwx` | Everyone has full access (not recommended) |
| `chmod 755` | `rwxr-xr-x` | Owner full, others can read and execute |
| `chmod 644` | `rw-r--r--` | Owner read/write, others read only |
| `chmod 600` | `rw-------` | Only owner can read/write (private files) |
| `chmod 700` | `rwx------` | Only owner has full access |

---

## 18. File Ownership — `chown`

Every file belongs to a **user** (owner) and a **group**. `chown` changes who owns a file.

| Command | Description |
|---------|-------------|
| `sudo chown username file.txt` | Change file owner |
| `sudo chown username:groupname file.txt` | Change both owner and group |
| `sudo chown -R username folder/` | Recursively change ownership of folder |

```bash
sudo chown john notes.txt               # john is now the owner
sudo chown john:devs notes.txt          # john owns it, devs group has access
sudo chown -R john:devs /var/www/app/   # change ownership for entire folder
```

> **Note:** You need `sudo` (root privileges) to change ownership of files you don't own.

---

## 19. Find Command

The `find` command searches for files and directories based on various criteria.

### Basic Syntax

```bash
find [where to search] [what to look for]
```

### Common Uses

| Command | Description |
|---------|-------------|
| `find /home -name "file.txt"` | Find file by exact name |
| `find /home -name "*.log"` | Find all `.log` files |
| `find /home -iname "file.txt"` | Case-insensitive name search |
| `find /home -type f` | Find only files (not directories) |
| `find /home -type d` | Find only directories |
| `find /home -type f -empty` | Find empty files |
| `find /home -size +100M` | Find files larger than 100MB |
| `find /home -mtime -7` | Files modified in the last 7 days |
| `find /home -mtime +30 -delete` | Find and delete files older than 30 days |
| `find /home -user john` | Files owned by a specific user |

```bash
find /var/log -name "*.log"                  # all log files
find / -type f -size +500M                   # large files eating up disk space
find /home/john -mtime -1                    # files modified in the last 24 hours
find /tmp -type f -mtime +7 -delete          # clean up files older than 7 days
find /etc -name "*.conf" -type f             # all config files
```

> **Tip:** Combine `find` with other commands using `-exec` or `xargs` for powerful automation.

```bash
find /var/log -name "*.log" -exec wc -l {} \;   # count lines in every log file
```

---

## 20. Zip & Unzip

### Compressing Files

| Command | Description |
|---------|-------------|
| `zip output.zip file.txt` | Zip a single file |
| `zip output.zip file1.txt file2.txt` | Zip multiple files |
| `zip -r output.zip folder/` | Zip an entire folder (recursive) |

```bash
zip backup.zip notes.txt
zip -r project-backup.zip /home/ubuntu/projects/
```

### Extracting Files

| Command | Description |
|---------|-------------|
| `unzip file.zip` | Extract in current directory |
| `unzip file.zip -d /target/` | Extract to a specific directory |
| `unzip -l file.zip` | List contents without extracting |

```bash
unzip backup.zip
unzip project-backup.zip -d /home/ubuntu/restored/
unzip -l archive.zip      # preview what's inside
```

### `tar` — Alternative Archiving Tool

`tar` is more commonly used on Linux than `zip`, especially for backups.

| Command | Description |
|---------|-------------|
| `tar -czf archive.tar.gz folder/` | Compress folder to `.tar.gz` |
| `tar -xzf archive.tar.gz` | Extract `.tar.gz` |
| `tar -tzf archive.tar.gz` | List contents |

```bash
tar -czf project-backup.tar.gz /home/ubuntu/projects/
tar -xzf project-backup.tar.gz
```

> **Memory aid for `tar` flags:** **c**reate, e**x**tract, **z**ip (gzip), **f**ile, **v**erbose

---

## 21. Networking Commands

| Command | Description |
|---------|-------------|
| `ping google.com` | Test network connectivity |
| `ping -c 4 google.com` | Ping exactly 4 times |
| `wget <url>` | Download file from the internet |
| `curl <url>` | Fetch content from a URL (API calls, downloads) |
| `curl -o file.txt <url>` | Download and save with a specific filename |
| `ifconfig` | Show network interface details (IP address, etc.) |
| `ip addr` | Modern alternative to `ifconfig` |
| `netstat -tulpn` | Show open ports and listening services |
| `ssh user@host` | Securely connect to a remote Linux machine |
| `scp file.txt user@host:/path/` | Securely copy file to remote machine |

```bash
ping -c 4 google.com               # test if internet is working
wget https://example.com/file.zip  # download a file
curl https://api.example.com/data  # call a REST API
ifconfig                           # see your machine's IP address
ssh ubuntu@54.123.45.67            # connect to an EC2 instance
```

### `curl` vs `wget`

| Feature | `curl` | `wget` |
|---------|--------|--------|
| API calls / REST | Best choice | Limited |
| Downloading files | Supported | Best choice |
| Output to terminal | Default | No |
| Recursive download | No | Yes |

---

## 22. Package Managers

Package managers install, update, and remove software on Linux.

### Ubuntu / Debian — `apt`

```bash
sudo apt update                     # refresh the list of available packages
sudo apt upgrade                    # upgrade all installed packages
sudo apt install package-name       # install a package
sudo apt remove package-name        # uninstall a package
sudo apt search package-name        # search for a package
```

```bash
sudo apt update
sudo apt install nginx              # install Nginx web server
sudo apt install git                # install Git
sudo apt install openjdk-17-jdk    # install Java 17
```

---

### Red Hat / Amazon Linux / CentOS — `yum` or `dnf`

```bash
sudo yum update                     # update packages
sudo yum install package-name       # install a package
sudo yum remove package-name        # remove a package
sudo yum search package-name        # search for a package
```

```bash
sudo yum install git
sudo yum install java-17-amazon-corretto
```

> **Note:** Newer versions of Red Hat / Fedora use `dnf` instead of `yum`. The syntax is identical — just replace `yum` with `dnf`.

---

### Common Packages for Developers

| Package | Install Command (Ubuntu) | Purpose |
|---------|--------------------------|---------|
| Git | `sudo apt install git` | Version control |
| Java 17 | `sudo apt install openjdk-17-jdk` | Java development |
| Python 3 | `sudo apt install python3` | Python development |
| Docker | See Docker docs | Containerization |
| Nginx | `sudo apt install nginx` | Web server / reverse proxy |
| curl | `sudo apt install curl` | HTTP requests / API testing |
| vim | `sudo apt install vim` | Improved vi editor |

---

## 23. Quick Reference Tables

### Most Used Commands at a Glance

| Category | Command | What It Does |
|----------|---------|--------------|
| Navigation | `pwd` | Print current directory |
| Navigation | `cd /path` | Change directory |
| Navigation | `ls -la` | List all files with details |
| Files | `touch file` | Create empty file |
| Files | `cat file` | Print file content |
| Files | `cp a b` | Copy file |
| Files | `mv a b` | Move or rename file |
| Files | `rm file` | Delete file |
| Directories | `mkdir dir` | Create directory |
| Directories | `rm -rf dir` | Delete directory and contents |
| Viewing | `head file` | First 10 lines |
| Viewing | `tail file` | Last 10 lines |
| Viewing | `tail -f file` | Live log monitoring |
| Viewing | `less file` | Scroll through large file |
| Search | `grep "text" file` | Search for pattern |
| Search | `find / -name "file"` | Find file by name |
| Permissions | `chmod 755 file` | Set permissions (numeric) |
| Permissions | `chown user file` | Change file owner |
| Users | `sudo useradd user` | Create user |
| Users | `sudo passwd user` | Set password |
| Users | `su user` | Switch user |
| Packages | `sudo apt install pkg` | Install package (Ubuntu) |
| Packages | `sudo yum install pkg` | Install package (RedHat) |
| Network | `ping google.com` | Test connectivity |
| Network | `curl <url>` | HTTP request |
| Network | `wget <url>` | Download file |
| Archive | `zip -r out.zip dir/` | Compress folder |
| Archive | `unzip file.zip` | Extract zip |
| Archive | `tar -czf out.tar.gz dir/` | Create tar archive |

---

### File Permission Cheat Sheet

| Octal | Symbolic | Meaning |
|-------|----------|---------|
| `777` | `rwxrwxrwx` | Full access for everyone |
| `755` | `rwxr-xr-x` | Owner full, others read+execute |
| `644` | `rw-r--r--` | Owner read+write, others read only |
| `600` | `rw-------` | Only owner can read+write |
| `700` | `rwx------` | Only owner has full access |

---

### Linux Directory Structure

| Directory | Purpose |
|-----------|---------|
| `/` | Root — top of the filesystem |
| `/home` | User home directories (`/home/ubuntu`) |
| `/etc` | System configuration files |
| `/var/log` | Log files |
| `/tmp` | Temporary files (cleared on reboot) |
| `/bin` | Essential binary commands |
| `/usr/bin` | User-installed commands |
| `/opt` | Optional third-party software |

---

### grep Options Quick Reference

| Option | Meaning |
|--------|---------|
| `-i` | Case-insensitive |
| `-n` | Show line numbers |
| `-r` | Recursive (search in all files) |
| `-v` | Invert match (show non-matching lines) |
| `-c` | Count matching lines |
| `-l` | Show only filenames with matches |

---

> **Note:** These notes cover Core Linux commands used daily by developers and DevOps engineers. Practice each command hands-on in a terminal for the best results.
> **Recommended practice environment:** AWS EC2 Free Tier — launch an Ubuntu instance and run these commands directly.
