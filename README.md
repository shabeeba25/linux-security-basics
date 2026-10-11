# linux-security-basics
Beginner Linux investigation lab covering system information, file permissions, processes, and listening network ports.
# Linux Security Basics

## Project Overview

This repository documents my hands-on learning of Linux commands and fundamental security concepts using Ubuntu on Windows (WSL).

The goal of this project is to understand Linux users, file permissions, group memberships, and basic system security through practical exercises.

## Environment and Tools

* Operating System: Ubuntu on Windows (WSL)
* Platform: Windows
* Tools: Linux terminal and standard Linux commands
* Level: Beginner

## Practical Exercise 1: System Information

### Commands Used

```bash
whoami
pwd
uname -a
```

### What I Learned

* `whoami` identifies the current Linux user.
* `pwd` displays the current working directory.
* `uname -a` displays kernel and system information.

These commands help establish which user and environment I am working in.

## Practical Exercise 2: Understanding File Permissions

### Command Used

```bash
ls -l /etc/passwd
```

### Observation

The command returned the following output:

```text
-rw-r--r-- 1 root root 1430 Feb 6 2026 /etc/passwd
```

### Analysis

* File type: Regular file
* Owner: root
* Group: root
* Permissions: `rw-r--r--`
* File size: 1430 bytes

The owner has read and write permissions. The group and other users have read permissions.

### Security Relevance

The `/etc/passwd` file contains Linux user account information. Its permissions allow account information to be read while restricting modification through ordinary file permissions.

## Practical Exercise 3: Understanding Sensitive File Permissions

### Command Used

```bash
ls -l /etc/shadow
```

### Observation

The command returned the following output:

```text
-rw-r----- 1 root shadow 804 Feb 6 2026 /etc/shadow
```

### Analysis

* File type: Regular file
* Owner: root
* Group: shadow
* Permissions: `rw-r-----`
* File size: 804 bytes

The owner has read and write permissions, members of the group have read permission according to the displayed mode, and other users have no permissions according to that mode.

### Security Relevance

The `/etc/shadow` file stores sensitive password authentication information, including password hashes where applicable.

Restricting access to this file helps protect authentication information from unauthorized access.

**Safety note:** I inspected the file's metadata and permissions without publishing its contents.

## Practical Exercise 4: User and Group Identification

### Command Used

```bash
id
```

### Observation

The command displayed my Linux user ID, primary group, and supplementary group memberships.

My account belongs to the `sudo` group.

### Analysis

The `id` command helps identify the current user's identity and group memberships.

Membership in the `sudo` group commonly allows a user to request administrative privileges on Ubuntu, depending on the system's configuration.

### Security Relevance

Group membership affects access to resources and administrative capabilities. Privileged accounts should be protected carefully and granted only the permissions they need.

## Key Security Concepts Learned

1. Linux file permissions control access to files and directories.
2. User and group ownership influence access permissions.
3. Sensitive authentication information requires additional protection.
4. Privileged group membership can increase the impact of account compromise.
5. The principle of least privilege helps reduce unnecessary access.

## Limitations

This is a beginner-level practical learning project, not a complete security audit or penetration test.

The observations describe the permissions and information displayed by my Ubuntu environment during the exercises.

## Future Improvements

* Investigate running processes and listening network sockets.
* Learn to inspect Linux system logs.
* Explore user privileges and access controls in more detail.
* Develop Python scripts to automate selected system checks.
* Practise security investigations in authorized lab environments.

## Learning Approach

I am building my cybersecurity knowledge through practical exercises, observing real system behaviour, documenting findings, and learning the underlying security concepts.
