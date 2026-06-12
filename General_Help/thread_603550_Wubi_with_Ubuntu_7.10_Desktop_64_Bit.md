---
title: "Wubi with Ubuntu 7.10 Desktop 64 Bit"
date: 2007-11-05
forum: General Help
---

### Post by Scoty on 2007-11-05
can i install Ubuntu 7.10 Desktop 64Bit DVD with Wubi or only 32Bit CD/DVD?

---

### Post by ago on 2007-11-05
Wubi will try to download the CD ISO matching your architecture. So for 64 bits it will by default use the CD ISO. To use 32 bit you have to pass "--32bit" when launching wubi.

---

### Post by Scoty on 2007-11-05
> **ago said:**
> Wubi will try to download the CD ISO matching your architecture. So for 64 bits it will by default use the CD ISO. To use 32 bit you have to pass "--32bit" when launching wubi.

i have a Intel Core2Duo but i have install Vista 32Bit and have install Wubi under Vista. can i use a DVD image?

---

### Post by mikedep333 on 2007-11-05
> **ago said:**
> Wubi will try to download the CD ISO matching your architecture. So for 64 bits it will by default use the CD ISO. To use 32 bit you have to pass "--32bit" when launching wubi.

The --32bit is very good advice. You should mention that on the official site.

> **Scoty said:**
> can i use a DVD image?
Wubi automatically grabs and works with the desktop cd image.

---

### Post by Scoty on 2007-11-05
ok i have download the 64 Desktop CD Version but i can not install. i have only a black screen without message. with the 32 Bit Version i dont have problems.

---

### Post by paetyndog on 2008-02-07
*Still learning this stuff ...*

It seems the Wubi installer incorrectly detects my system as 64 bit hardware cuz it tries to download the AMD64 ISO image. Even though its not 64 bit, the ubuntu  install went OK on and actually came up and was functional - even detected and configured my wireless card flawlessly !!! 

However, I had some issues with some important (required for my VPN to work) RPM packages I was converting to .deb using alien - messages like
[FONT="Fixedsys"]dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)[/FONT]

I stumbled across this thread and have launched the Wubi-7.10-alpha-rev386.exe with the **--32bit**  option - 
Right now its downloading the corrected ubuntu-7.10-desktop-i386.iso image. 

If there is another way to change rather than reinstall, lemme know. I've heard rumblings about chroot, but a new install is likely an easier (for me) path ...

I'll update this post with my results on running alien on the corrected kernel architecture

---

### Post by ago on 2008-02-07
> **paetyndog said:**
> *Still learning this stuff ...*
It seems the Wubi installer incorrectly detects my system as 64 bit hardware cuz it tries to download the AMD64 ISO image.
Intel Core Duo processors are 64 bits and the Amd64bit image is recommended even for intel. You can override passing the --32bit argument

> However, I had some issues with some important (required for my VPN to work) RPM packages I was converting to .deb
If you can install our job is finished :P 
for anything else you should ask in the general ubuntu forums

---

