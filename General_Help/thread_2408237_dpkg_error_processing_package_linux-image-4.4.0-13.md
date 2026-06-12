---
title: "dpkg: error processing package linux-image-4.4.0-133-generic (--remove):"
date: 2018-12-15
forum: General Help
---

### Post by dwi.junianto on 2018-12-15
Hello guys, 
I have a problem when I want to install application in Terminal.. The apllication can't be installed and get information that the procces is error..
like this its information:

dpkg: error processing package linux-image-4.4.0-133-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-4.4.0-133-generic
 linux-image-4.4.0-133-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

anyone could help me, I'm very frustrated..

---

### Post by dbergst on 2018-12-15
Have you tried running the following command?

sudo dpkg --configure -a

---

### Post by dwi.junianto on 2018-12-16
I've tried to running thats command, and the result is

Setting up grub-pc (2.02~beta2-9ubuntu1.15) ...
/var/lib/dpkg/info/grub-pc.config: 35: /etc/default/grub: =: not found
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 grub-pc

What's next?

---

