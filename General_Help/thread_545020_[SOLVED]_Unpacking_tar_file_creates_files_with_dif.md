---
title: "[SOLVED] Unpacking tar file creates files with different owner"
date: 2007-09-07
forum: General Help
---

### Post by zethar on 2007-09-07
When I unpack a tar file with the comand:

sudo tar xvfz en.linuxx86.tar.gz

the directory and files that are created are not owned by me but rather a different user account! 

I have had other odd ownership problems and I wonder if there are some configuration files that may be corrupted and that I can edit to fix the problem?

---

### Post by logos34 on 2007-09-07
You used sudo so they're owned by root now.  Try it again without sudo

---

### Post by zethar on 2007-09-07
Thanks for the point.  I moved the tar file to my desktop so I didn't need to use sudo and it unpacked fine.

I am still perplexed about the original problem which I didn't clearly explain.  When I use sudo to unpack the tar file, the unpacked files are owned by my wife's account rather than the root or my own account which I am logged into!

---

### Post by logos34 on 2007-09-08
> **zethar said:**
> Thanks for the point.  I moved the tar file to my desktop so I didn't need to use sudo and it unpacked fine.

**I am still perplexed about the original problem which I didn't clearly explain.  When I use sudo to unpack the tar file, the unpacked files are owned by my wife's account rather than the root or my own account which I am logged into!**

Oh I see. That is odd.  But then again I'm not an expert on permissions/ownership issues.

---

### Post by nabilmalik on 2008-06-11
Today i came across the exact same problem. When i 'sudo tar -xvf <filename.tar>', the contents that are extracted are owned (user and group) by a different user on my machine. When I extract it without sudo, it seems all normal and are extracted with my account owner ship..

Any one having any ideas whats going on. I have using Ubuntu 8.04 with the following output of uname -a command.

Linux gravity 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux

Please help. Many Thanks.

-Nabil.

---

