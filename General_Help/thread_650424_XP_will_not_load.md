---
title: "XP will not load"
date: 2007-12-26
forum: General Help
---

### Post by jds1999 on 2007-12-26
I set up a partition from the Ubuntu boot cd. The partition setup worked fine. Then installed Ubuntu from boot CD to the partition as instructed. Install worked fine. All windows files and file system are still on my hard drive. But I cannot get XP to boot from grub menu. It shows windows xp professional and when I selected it... it says system loading. But nothing ever loads. What can I do to fix this?

---

### Post by perixx on 2007-12-26
Hi!

Look into your /boot/grub/menu.lst file; do you have an entry for windows that looks sorta like this (with all lines)?

> title Windows XP/Vista 
 rootnoverify (hd0,0) 
 makeactive
 chainloader +1


**Edit:**
Refer to this page for more detailed info about Grub and error-messages, if any:
[http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")
This link here is a nice and easy step-by-step Howto for an alternative Windows-Grub dualboot setup:
[http://www.icpug.org.uk/national/linnwin/contents.htm]("http://www.icpug.org.uk/national/linnwin/contents.htm")
Here you can find SGD - the Super Grub Disk - will let you boot into any system (and maybe also fix XP's boot-up, if you can figure out how to use it - that didn't work for me)
[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

Do you have XP on your first partition (hda1) and Ubuntu on the second (hda2)?

perixx

---

### Post by jds1999 on 2007-12-26
# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/hda1

title Microsoft Windows XP Professional

root (hd0,0)

savedefault

makeactive

chainloader +1

So from this I would assume XP is on hda1.

---

### Post by perixx on 2007-12-26
Yes, it is. To be honest, I've encoutered problems with XP several times after installing Ubuntu (or friends of mine)...
Solutions reached from:

> - recovering the MBR and bootsector by running the recovery console from the XP-disk, logging into XP-installation and doing 'fixboot c:' & 'fixmbr c:' (where drive letter 'c:' can vary; there's a command (search in 'help') to find the respective drive letter (if more than one XP-installation), but you should already notice from your login).

- receiving a 'no bootable system disk' error and encountering  an inaccessible drive after trying to use the 'chainload Linux from XP-bootloader' method by cloning the Linux-bootsector into a file in c:\ (could be resolved by just doing the 'fixboot' trick in the recovery console, along with setting hda1/hd0 'active/bootable' with 'diskpart'. 

- once I had exactly the same problem, but 'fixboot' and 'fixmbr' wouldn't bring back XP again, after the Ubuntu-installation, to which Grub in the MBR pointed to - and from which XP was chainloaded - was deleted by accident. The only way to bring XP back to life again, was to completely re-install Ubuntu into the wiped partition (manual Grub setup).  
I suppose there was a problem with the HDD itself and /or BIOS, resulting in some sort of MBR-write-protection....

- doing a complete re-installation of both systems, because XP was overwritten by checking the 'use all of drive'-option during the Ubuntu-installation.

I personally would start from depending what's more important to you - XP or Ubuntu. Have your live-CD at hand, if things go bad. 
If it's the first one, I'd recommend to try using only the 'fixboot' trick at first - this way you might be able to circumvent re-installing Grub (but I'm not perfectly sure). You can always try to do the 'fixmbr' the second time. 

You can boot into the Ubuntu-partition with SGD afterwards and do a new manual setup of Grub from there. Or you can use the XP bootloader to chainload Grub in your Ubuntu-partition (you'll have to install Grub into your Ubuntu's partition, the 'superblock', for this). For problems you might encounter with this, see:
[http://ubuntuforums.org/showthread.php?t=621827]("http://ubuntuforums.org/showthread.php?t=621827")

perixx

---

### Post by jds1999 on 2007-12-27
Ok I have tried to load the windows fixboot and fixmbr neither work... here is what it is telling me now.  A disk read error occured.  I can get ubuntu back by using SGD but still no windows.  All the file systems are still there the partition is in place.  Any recommendations?

---

### Post by perixx on 2007-12-28
Hi again!

Sorry to see that there's so much trouble... can you boot into protected mode of XP by pressing F8 at startup (right after the BIOS boot splash screen)?

If not, you might try to boot up your XP with a self-mdae NT boot floppy or the 'BartPE' disk.

If you're not afraid of borking things, you could also try to zero out the bootsector of your HD with 'MHDD' - or Terabyte's 'MBRWORK' might also be able to do that. If I'm not mistaken, just 0-ing the very bootsector of hda1 (XP), not the entire MBR, and doing a 'fixboot' after that might solve the problem. Anybody please correct me if I'm wrong!
See also:
[http://hddguru.com/]("http://hddguru.com/")

Anyway, before you start getting experimental, you should back up any vital data on your partitions, as long as they're still accessible - if you really mess it up, you can still do a clean installation. 'Partition Find & Mount' perhaps can help temporarily if you've lost/deleted a partition already....

Hope this helps you...

perixx

---

### Post by jds1999 on 2007-12-28
Progress has been made.  I can now boot back into windows from a CD I found a file at this website [http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm) I have tried his solutions for fixing the boot loader none have worked so far.  Any suggestions on how I can fix this from inside windows.  Ubuntu is still there if I don't run the boot loader grub menu loads and ubuntu boots up.  But now at least I can get back to XP.  XP only shows a C: drive in my computer no partition.  It does show the other partition when I right click on my computer and click manage.  Thanks for your help... I have a friend coming to look at this machine over new year's who knows more than I do if we come up with a solution we will pass it on.

---

### Post by RockHaxor on 2007-12-28
I found this tool to be a great asset, it has everything you could possibly want and more.

[http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")

download this iso image , burn it to a cd and use a tool on the disc called Super Grub Disc. 

I believe it will repair the MBR for you.

If you don't want the entire Ultimate Boot CD then you can download Super Grub at this link:

[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/") 

Good Luck

---

