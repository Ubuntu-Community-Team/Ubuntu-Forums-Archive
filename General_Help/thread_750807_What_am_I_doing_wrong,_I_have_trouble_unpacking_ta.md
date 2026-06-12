---
title: "What am I doing wrong, I have trouble unpacking tars"
date: 2008-04-09
forum: General Help
---

### Post by pwn32 on 2008-04-09
Hi, Im fairly new to ubuntu 7.10, and I'm downloading a driver to set up my wifi, the only problem is it won't unpack the tar file, i have no idea why, I know it's something I'm doing wrong though because I downloaded ndiswrapper before and that didn't work either.

chris@Chris:~$ _tar vjxf r8101-8.aaa.bb.tar.bz2_
tar: r8101-8.aaa.bb.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
chris@Chris:~$ 

I just downloaded the file to my desktop, am I supposed to put it at the root of my drive?
(I am such a noob, lol)

---

### Post by pieisgood4589 on 2008-04-09
Try 

```
sudo cd desktop
```

Then do the code to untart the package.
Sudo's there just in case :popcorn:

Also, why not just double click on the .tar.bz2 (i think) package and use the graphical wizard? :confused:

---

### Post by pwn32 on 2008-04-09
I did that, but  then I need to change my directory to the file and it doesn't find it, let me try it again though.
Thanks for the help, and just wondering how do you change to root so I don't always have to use sudo?

---

### Post by pwn32 on 2008-04-09
Okay, i guess the installer instructions were totally off, I changed my directory to desktop, and I untarred it with the actual name, not the one the instructions gave me, so Im starting to get close to getting wifi, thanks for the help!

---

