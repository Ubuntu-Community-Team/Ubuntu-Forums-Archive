---
title: "cannot execute binary file: Exec format error"
date: 2016-07-13
forum: General Help
---

### Post by Matt_Nona on 2016-07-13
Hi guys, I could really use some help.
I'm getting all kinds of problems with my installation of Ubunut today, everything was working perfectly for months until today. I came back home, tried to turn on my laptop, logged in and all I was able to see was my folders on my dekstop, no menu, no launcher, no top bar.
I solved this by running "setsid unity" however it only works until I reboot the laptop. 
When I open my terminal I get this error
"bash: /home/matt/bin/ls: cannot execute binary file: Exec format error
/home/matt/bin/bash: 1: /home/matt/bin/bash: Syntax error: "(" unexpected"
Any other binary files I try to run return similar error. 
The only thing I've done yesterday was install VirtualBox and Windows XP on it (already removed it).
I was also able to create a new user which seems to be working fine but I would really like to keep my old account and all its settings.
I'm running the latest Ubuntu 64bit
Any suggestions?

---

### Post by steeldriver on 2016-07-13
The system's version of things like 'ls' and 'bash' should be in /bin - not /home/matt/bin

It sounds like you have placed some incompatible (e.g. 32-bit versus 64-bit, or ARM instead of ELF) binaries with these names into your /home/matt/bin directory, and those are being detected first because of the order of directories your PATH

---

### Post by Matt_Nona on 2016-07-13
Thanks for your answer,
I have only installed VirtualBox and ran the usual update and upgrade which I do every day / every other day.
All the system commands like 'ls', 'uname', 'touch' are located in /bin and only links to them are in my /home/matt/bin folder. 
Nearly every command I have tried returns the same error. 
Is it safe to move those files from /home/matt/bin directory to let's say my desktop and move them back one by one to detect which one of them is giving the trouble or would that cause any more problems?

EDIT: I decided to rename all the "non links" binaries to filename.old. First try... busybox.old :) Opened the terminal and the error is gone, Going to reboot and see if the problem is gone. Thanks very much for your help steeldriver.

---

### Post by steeldriver on 2016-07-13
How and why did you create those links? that's not a usual thing to do

Can you run things with absolute paths e.g.

```

/bin/ls -l $(/usr/bin/which ls)

```
or
```

/usr/bin/file -L $(/usr/bin/which ls)

```

If so, what are the results?

---

### Post by Matt_Nona on 2016-07-13
That's a good question.... I didn't create any links so not too sure why that has happened.
Now after a reboot, I can see my files, menus and the top bar, also no errors in my terminal.
I went into /home/matt/bin folder and all the links that were there are still present but now in the type column it says "Link (broken)", can I remove those?
Everything seems to be working fine (apart from my screenshot button) and here are the results of the above commands:
```
-rwxr-xr-x 1 root root 126584 Feb 18 13:37 /bin/ls
```
and
```
/bin/ls: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=eca98eeadafddff44caf37ae3d4b227132861218, stripped
```

---

