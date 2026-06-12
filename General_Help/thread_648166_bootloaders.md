---
title: "bootloaders"
date: 2007-12-23
forum: General Help
---

### Post by Sequences on 2007-12-23
I recently installed a few operating systems in the following order:

windows
linux(ubuntu)
windows

After I had installed Ubuntu, the bootloader showed the various ways I can boot Ubuntu and it also showed the windows I had installed previously. However, after I installed the final windows, the linux bootloader seems to have been overridden.

I have noticed that Windows cannot recognize the formatting used by Linux, and if it is a Windows bootloader I am using, it might also not be recognizing the Linux system I have installed. Is there a way where I can get the bootloader to show Linux so that I can use it, or is there an actual loader that I can download and use?

Thanks in advance,

Seq

---

### Post by p_quarles on 2007-12-23
Yeah, the Windows bootloader doesn't play nice with other operating systems. GRUB, however, is designed to do just that. You'll need to reinstall it, which can be done using the Ubuntu live CD and following these directions:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by PeterJS on 2007-12-23
Yeah the windows installer is kinda rude like that and will over write the master boot record with out asking permission, and NTLDR doesn't deal with linux so well, which is a nice way of saying at all.

Grub (the default Ubuntu bootloader) on the other hand is pretty good about detecting other operating systems when it's installed and configuring itself too boot them.

It's kind of a pain to fix, but here's the documentation:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0)

Use the link p_quarles provided, it's a much cleaner version of the same thing.

The general rule is to try and do your best to install Ubuntu last, live and learn. Good luck.

---

### Post by Sequences on 2007-12-23
It worked, thanks so much for the help.

---

