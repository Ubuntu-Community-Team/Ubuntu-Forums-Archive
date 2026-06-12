---
title: "Installing Boot Loader After XP/Ubuntu are Installed"
date: 2006-07-05
forum: General Help
---

### Post by kLOTTiS on 2006-07-05
Hey Guys, I have 2 Computers, one has Windows XP installed on a 250gb HDD
one has Ubuntu 5.10 Installed on a 10gb HDD, is it possible to just plug the 10gb into my main Windows computer and dual boot them?

---

### Post by tonyr on 2006-07-05
Yes it is possible.

You will either have to make the 10gb drive the first drive by plugging it into the
primary controller, or by selecting the boot drive in the BIOS, if you BIOS supports
that. You would ahve to modify the grub menu.list to know where WIndows is
and set up the boot clause.

OR...
you will have to install the GRUB or LILO boot loader onto the big drive MBR and edit the
grub menu.lst file anyway.

Research this out  before you do anything.

---

### Post by flarkit on 2006-07-05
It is possible, but you'd need to be sure that your hardware drivers on the Linux installation will be correctly updated for the new PC.

---

### Post by kLOTTiS on 2006-07-06
i have the HDD plugged in and working with linux, however i cannot yet boot windows, windows is on the slave disk and i am using this config

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1

however i am not sure if the (hd*) numbers are correct, is there any way of finding out?

---

### Post by tonyr on 2006-07-06
You should be able to use the grub **find** command, but you need to be 
booted from the LiveCD or some other recovery CD or a grub floppy (see [this]("http://www.troubleshooters.com/linux/grub/grub.htm") or [this]("http://www.openbg.net/sto/os/xml/grub.html")).

Here are a some threads with discussions about the same problem.  Maybe you 
can pick up some clues here. **confused57** has a lot to say.
[http://www.ubuntuforums.org/archive/index.php/t-34794.html](http://www.ubuntuforums.org/archive/index.php/t-34794.html)
[http://www.ubuntuforums.org/showthread.php?t=205637&page=2](http://www.ubuntuforums.org/showthread.php?t=205637&page=2)
[http://www.ubuntuforums.org/showthread.php?p=1192173](http://www.ubuntuforums.org/showthread.php?p=1192173)

---

