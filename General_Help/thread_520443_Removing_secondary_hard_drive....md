---
title: "Removing secondary hard drive..."
date: 2007-08-08
forum: General Help
---

### Post by s1mple_M4N on 2007-08-08
Hi all, been a while since I had to ask a question here.

First off, really enjoying Feisty and encouraging all my friends to try Ubuntu.

I have a dual-boot XP/Feisty system with the XP drive being slave/secondary. I would like to remove the XP drive as I no longer require Windows and would like to add the drive to a file server on my home network.

My question is: in order to take away the option to start Windows when my PC boots, can I just comment out the Windows entry in my /boot/grub/menu.lst file??

Thanks in advance,

RoyJ

---

### Post by renzokuken on 2007-08-08
if your xp drive is secondary or slave tis shouldnt be a problem no.

if it was master/primary, ubuntu may renumber all your drives and not be able to boot at all without some intervention

...but yu should be ok

---

### Post by dabl on 2007-08-08
> **s1mple_M4N said:**
> can I just comment out the Windows entry in my /boot/grub/menu.lst file??



CAUTION!

You may THINK it is a secondary/slave, but if the Master Boot Record is on that drive, which it may well be, then that is where Grub was written, and you won't be able to boot anything if you remove the drive, because there won't be any boot record anywhere in your system.

If you run GParted (which is now a repository package that you must choose to install, as opposed to an included package with the basic Ubuntu installation), look for the "bootable" flag on your partitions.  If you find it on your Win XP drive, that's your indicator that you've got a Grub reinstallation job ahead of you, before you pull that drive.

Here's the good stuff on fiddling with Grub setups (written for Kubuntu, but it's the same for Ubuntu):  [http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

:)

---

### Post by s1mple_M4N on 2007-08-08
Wierd...

Gparted tells me both drives are boot.
I used this tutorial [http://ubuntuforums.org/showthread.php?p=677880#post677880]("http://ubuntuforums.org/showthread.php?p=677880#post677880") to help me set my system up.
Not too sure what to do now - could I try commenting the XP lines out of menu.lst and if it doesn't work use a live disc to edit it back again??

Thanks again,

RoyJ

**************
SOLVED - looked a bit harder before I posted. Thanks guys for taking the time to help!

**************

---

### Post by apetresc on 2007-08-08
> **s1mple_M4N said:**
> Wierd...

Gparted tells me both drives are boot.
I used this tutorial [http://ubuntuforums.org/showthread.php?p=677880#post677880]("http://ubuntuforums.org/showthread.php?p=677880#post677880") to help me set my system up.
Not too sure what to do now - could I try commenting the XP lines out of menu.lst and if it doesn't work use a live disc to edit it back again??

Thanks again,

RoyJ
No, commenting out the lines in menu.lst wouldn't cause a problem even if removing the drive would.

What you should do is remove the drive and try booting. If it works, good, proceed with removing the lines from menu.lst. If it doesn't, pop in the LiveCD and install GRUB on the remaining drive.

---

