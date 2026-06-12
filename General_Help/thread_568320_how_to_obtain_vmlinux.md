---
title: "how to obtain vmlinux?"
date: 2007-10-05
forum: General Help
---

### Post by gnychis on 2007-10-05
Hi all,

I'm trying to run oprofile on the kernel and therefore need vmlinux rather than vmlinuz which seems to be the only thing included in the kernel packages.  Is it somewhere that I am missing, or do i need to build the kernel myself?

Thanks!
George

---

### Post by yang on 2008-02-06
Bump, please. To add some more info, I'm getting:

```

$ sudo opcontrol --vmlinux=/boot/vmlinuz-2.6.22-14-generic 
The specified file /boot/vmlinuz-2.6.22-14-generic does not seem to be valid
Make sure you are using the non-compressed image file (e.g. vmlinux not vmlinuz)

```

There's no vmlinux file. How do I get this?

---

### Post by gnychis on 2008-02-06
read the first section i wrote on Building VMLinux

[http://www.gnuradio.org/trac/wiki/InBandProfiling](http://www.gnuradio.org/trac/wiki/InBandProfiling)

---

### Post by gnychis on 2008-02-06
oh but make sure to change to the appropriate kernel names, things are newer these days

---

### Post by rototor on 2008-07-10
You can do this much simpler:

[https://lists.ubuntu.com/archives/kernel-team/2006-August/001007.html](https://lists.ubuntu.com/archives/kernel-team/2006-August/001007.html)

Just install the matching linux-image-debug-??? package, and you get the correct matching kernel image in 

/boot/vmlinux-???

Building vmlinuz yourself doesn`t really work (at least it did not for me), because you must have the exact same build tools and environment, otherwise the symbols may not match ....

---

