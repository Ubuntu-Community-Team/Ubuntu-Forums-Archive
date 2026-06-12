---
title: "Can't get my hard drive to show up."
date: 2014-09-24
forum: General Help
---

### Post by rapzeh on 2014-09-24
I installed Ubuntu on a USB Stick using Wubi, then following another tutorial I deleted the disk from "Disk Management", But now my second Hard Drive doesn't show up on My Computer! I only see one 1TB hard drive, whereas I should have two. How do I get my other hard drive back again? Help please!

(I should probably mention I'm trying to uninstall Ubuntu.)

---

### Post by yancek on 2014-09-24
> I installed Ubuntu on a USB Stick using Wub

Not sure how you did that because wubi is software to install Ubuntu inside a windows operating system much the same as using virtual software.  It is on the windows system partition somewhere.  How to uninstall the wubi program and the installed Ubuntu inside windows is explained on the wubi page, you delete it the same way you would delete any program/application in windows.  See the link below.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Mark Phelps on 2014-09-24
>  wubi is software to install Ubuntu inside a windows operating system much the same as using virtual software.

Actually, WUBI only INSTALLS the software from inside Windows.  When you then launch Ubuntu, it runs by itself, NOT inside a VM.

As to the location, it creates a single file (root.disk) which resides somewhere on a Windows filesystem partition.  If you installed it to the USB stick, inside an NTFS partition there, when you removed that partition, you removed the file.  IT might still show up under Programs because it doesn't look like you properly uninstalled it, but it won't work anymore because the main file is gone.

---

