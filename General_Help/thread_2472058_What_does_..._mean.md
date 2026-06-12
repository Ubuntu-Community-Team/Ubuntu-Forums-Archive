---
title: "What does .../ mean?"
date: 2022-02-16
forum: General Help
---

### Post by rsteinmetz70112 on 2022-02-16
I think I screwed up. 
What does .../ mean or do in a command? For example cd .../ I know ./ means the current directory and ../ means the parent directory.

---

### Post by TheFu on 2022-02-16
If you have an aliases, it is common to mean the "grandparent" directory. If you don't have any alias, it should end in an error.
If you see a directory with ... and you didn't create it, then it is highly likely someone has hacked the system.

---

### Post by rsteinmetz70112 on 2022-02-16
Actually I attempted to move a directory to it's parent and mistyped "mv directory .../" instead of "mv directory ../". I got no error message and the directory isn't in the parent, grandparent or any other place on the file system according to find. The original directory still shows it uses a lot of space but the only file in it is a lost+found directory with nothing in it. There is only one alias defined as far as I can tell and it doesn't have anything to do with this. 

I was hoping there is some way to recover it rather the restore from a backup.

OK your comment helped me figure it out. Apparently the directory was renamed "..." and still exists. I was able to rename it and move it as originally intended. That's not what I expected to happen at all, but it does make some kind of sense.

Thank You again TheFu.

---

### Post by ActionParsnip on 2022-02-16
Interestingly the "." and ".." things are files. Special files that live in every folder in the file system.

---

### Post by The Cog on 2022-02-16
I would expect that "mv directory .../" would rename directory to "...". That's a hidden directory because it starts with a dot. If I'm right, you should be able to see it with "ls -al" or in a file manager after selecting to show hidden files, and you should just be able to rename it again.

---

### Post by TheFu on 2022-02-16
> **ActionParsnip said:**
> Interestingly the "." and ".." things are files. Special files that live in every folder in the file system.

Everything on any Unix-like OS is a file, unless it is a running process. There are 2 choices.  Files and processes. Nothing else.

---

### Post by rsteinmetz70112 on 2022-02-16
> **The Cog said:**
> I would expect that "mv directory .../" would rename directory to "...". That's a hidden directory because it starts with a dot. If I'm right, you should be able to see it with "ls -al" or in a file manager after selecting to show hidden files, and you should just be able to rename it again.

That's correct. I was able to list it and rename it. Everything is now as it should be.  In my initial state of panic I didn't initially realize I had mistyped the intended command. I didn't try that particular command. I usually list hidden files using "ls .??*" in this case that didn't work.

---

### Post by TheFu on 2022-02-16
> **rsteinmetz70112 said:**
> That's correct. I was able to list it and rename it. Everything is now as it should be.  In my initial state of panic I didn't initially realize I had mistyped the intended command. I didn't try that particular command. I usually list hidden files using "ls .??*" in this case that didn't work.

That's what the **ls -a** is for.  I have a number of ls-based aliases, including an alias for plan ls.  Since we don't allow ls to be used in scripts (bash globbing is very powerful), it isn't all that dangerous.

---

