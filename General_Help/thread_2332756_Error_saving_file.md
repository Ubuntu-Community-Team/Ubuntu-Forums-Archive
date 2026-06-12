---
title: "Error saving file"
date: 2016-08-03
forum: General Help
---

### Post by 4kh3RAm on 2016-08-03
I opened a text file using Geany.

When I tried to save it, it said

Error saving file

Error opening file hello.asm

Permission denied.

File on disk may be truncated.

Why is that happening ?

---

### Post by ajgreeny on 2016-08-03
Who is the file owner? Show us the output of ```
ls -l /path/to/hello.asm
```
Try opening it in nano  with command ```
nano /path/to/hello.asm
```and then save it with Ctrl+O followed by Enter.

---

### Post by 4kh3RAm on 2016-08-03
> ls -l hello.asm
-rw-rw-r-- 1 root root 754 Aug  3 13:25 hello.asm

It gave me "permission denied." when nano was used.

---

### Post by QIII on 2016-08-03
Before you do anything, please describe where this file is, how you are using it and why it came to have the permissions it does.  It looks like an assembly language file from a simple "hello, world" program.  Are you taking a course in assembly language?

The owner of the file is root with read/write permissions.
The owning group of the file is root with read/write permissions.
Everyone else (like you) has read-only permissions.

If you want to modify a file with those permissions for that user and group, you would need to use "sudo" in front of nano to temporarily elevate your privileges.

But when something is owned by the root user and the root group with those permissions, you had better know what you are about.

---

### Post by 4kh3RAm on 2016-08-03
> **QIII said:**
> Before you do anything, please describe where this file is, how you are using it and why it came to have the permissions it does.  It looks like an assembly language file from a simple "hello, world" program.  Are you taking a course in assembly language?

The owner of the file is root with read/write permissions.
The owning group of the file is root with read/write permissions.
Everyone else (like you) has read-only permissions.

If you want to modify a file with those permissions for that user and group, you would need to use "sudo" in front of nano to temporarily elevate your privileges.

The big question is how root became the file owner ??

I have been making assembly programs for about 10 years.

What I have been doing is using thunar in superuser mode to open/edit the file.

If I am understanding what some have posted, that can lead to "issues."

If there is a better way, I am all ears.

---

### Post by QIII on 2016-08-03
If this is something in your /home that you have been opening with "sudo" and a graphical application, it is not surprising all all that root now owns it.  That is the "issue" that can occur.

When using a gui app to open files, you should use gksudo -- I'm not sure how pkexec is coming along since I run Kubuntu and use kdesudo.

This goes for anything you open from Thunar, too.  Open Thunar with gksudo initially.

Better yet, if it's in your /home, don't open Thunar with any elevation of privileges.

---

### Post by jeremy31 on 2016-08-03
Using ```
sudo -H
``` with the command may yield better results, similar to gksudo

---

### Post by 4kh3RAm on 2016-08-03
The only reason I have been running as superuser is because reg thunar will not open mp4 files.

---

### Post by vasa1 on 2016-08-03
> **4kh3RAm said:**
> The only reason I have been running as superuser is because reg thunar will not open mp4 files.Why do you need Thunar to open mp4 files?

Avoid root, sudo, gksudo, sudo -H, as far as possible. From other threads, it appears your home folder is stuffed with files owned by root!

---

### Post by 4kh3RAm on 2016-08-03
Thanks for your patience.

1. I have gone thru the transition for Windows to Linux.

2. And then from Puppy Linux which is root by default to a non-root distro like Ubuntu.

I try to provide the info that is needed so you can help me.

But I am human and frequently fail.

What is wrong with thunar ?

Thunar has properties that I have not found with other file managers.

I use thunar which is non-root on Ubuntu.

Meaning that from a console, typing thunar opens a non-root Thunar.

For super thunar, I use.

echo password | sudo -S thunar

If you have an alternative that has custom actions, eye am game.

I am sometimes terse in my posts, though I do not intend to.

---

### Post by ajgreeny on 2016-08-04
I think this all harks back to the thread you started at [https://ubuntuforums.org/showthread.php?t=2332438](https://ubuntuforums.org/showthread.php?t=2332438) and your use of **sudo** in a completely unsupported manner which has led to root ownership of many of your home files and folders.

Having been involved in that linked thread, I am aware of your distrust of the **chown** command but I do not see any other way out of your problem; you will have to return all your /home to your own user ownership, and also I very strongly recommend that you stop using applications as root to edit files in your home, or this problem will just escalate into more and more problems for you.

---

### Post by 4kh3RAm on 2016-08-04
I can not find the thread with the chown command that I have not ran yet.

I want to run it and see what happens.

---

### Post by 4kh3RAm on 2016-08-04
> **jeremy31 said:**
> Using ```
sudo -H
``` with the command may yield better results, similar to gksudo

I added -H to all my sudos in my backup script.

---

### Post by ajgreeny on 2016-08-04
> **4kh3RAm said:**
> I can not find the thread with the chown command that I have not ran yet.

I want to run it and see what happens.
I gave you a link for that in my post No 11, but to refresh your memory it is ```
sudo chown -R andy:andy /home/andy
```

---

### Post by 4kh3RAm on 2016-08-04
thanks.

Everything now has the correct owner and no more need to run anything as a superuser.

---

### Post by ajgreeny on 2016-08-04
Please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

