---
title: "redirection stderr ?"
date: 2008-03-13
forum: General Help
---

### Post by jackm on 2008-03-13
Hi all,
When I trie the following command** the error message** isn't redirect to **file2**
```
cat <file1 2>file2
bash: file1: No such file or directory

```
but when I reverse the order of redirection or try  the following 
```
cat file1 2>file2
```
the redirection is done
Why the first command doesn't work :confused:

---

### Post by scragar on 2008-03-13
first command is the equiv to:
```
file1>cat 2>file2
```
so it's not finding the file called file1 that your wanting to run.

---

### Post by dcstar on 2008-03-13
> **scragar said:**
> first command is the equiv to:
```
file1>cat 2>file2
```
so it's not finding the file called file1 that your wanting to run.

And if it originally was:

```
cat <./file1 2>file2
```

it might have worked differently (assuming "file1" was executable).

---

