---
title: "Matlab R2009b and R2010a and lib64/libc.so.6: not found on Ubuntu 12.04"
date: 2012-12-19
forum: General Help
---

### Post by loremaster on 2012-12-19
Hi guys, I really really need help on this and will appreciate help.

Currently am working on a project that requires Matlab R2009b and R2010b to work with.

But when i try to install them,  i get error like

/lib64/libc.so.6: not found

but i could go ahead and install successfully but whenever i launch Matlab, i get a message saying

/usr/local/matlabR2009b/bin/util/oscheck.sh: /lib64/libc.so.6: not found

However i still get to use Matlab as usual but my code runs into error whenever i try to compile .cc files, i get the similar error like missing libc.so. 6 error and fail in compiling.

I researched on this problem and tried,

sudo rm /lib64/libc.so.6

sudo ln -s /lib/i386-linux-gnu/libc-2.15.so /lib64/libc.so.6

but even after removing the links and recreating them.  I get this error;

ln: failed to create symbolic link `/lib64/libc.so.6': File exists

The same error still persist.

I'm a new Ubuntu user and i am using Ubuntu 12.04 64 bit. Any advice is appreciated! Thank you in advance!

---

### Post by matt_symes on 2012-12-29
Hi

Open a terminal and type

```
ls -l $(find /lib -name 'libc.so.6')
```That is a small L after ls.

Please post the results back here.

Also post the results of

```
uname -a
```

Kind regards

---

### Post by anshuhim20 on 2013-04-19
I am sending the results for the requested:
ls -l $(find /lib -name 'libc.so.6')
lrwxrwxrwx 1 root root 12 Oct  6  2012 /lib/i386-linux-gnu/libc.so.6 -> libc-2.15.so
lrwxrwxrwx 1 root root 29 Mar 13 13:30 /lib/libc.so.6 -> /lib/i386-linux-gnu/libc.so.6

$ uname -a
Linux mv-HP-Z210-Workstation 3.2.0-40-generic-pae #64-Ubuntu SMP Mon Mar 25 21:44:41 UTC 2013 i686 i686 i386 GNU/Linux

---

### Post by matt_symes on 2013-04-19
Hi

Can you post the exact error message you are seeing. You are using 32 bit Ubuntu.

Kind regards

---

