---
title: "[SOLVED] GRUB device mapping"
date: 2008-04-03
forum: General Help
---

### Post by savory19 on 2008-04-03
Hello,

I have been struggling with this one for a couple of days now so I thought I'd ask for some help:

I have built a new system with two new SATA drives, plus one re-used IDE drive for data (does not have an OS installed on it).

I first installed WinXP on one of the SATA drives, then installed Ubuntu 7.10 on the other, taking the default bootloader options.  The first problem was that it would boot directly into XP on startup.  Switching the boot priority in the BIOS got me to GRUB (with XP as an option), but I then cannot load either OS (error 17 for Linux, 'NTLDR is missing' for WinXP).  Memtest and recovery mode also give error 17.

/boot/grub/device.map:

(hd0)   /dev/hda
(hd1)   /dev/sda
(hd2)   /dev/sdb


relevant details from /boot/grub/menu.lst:

title       Ubuntu 7.10 
root       (hd2,0)


title       WinXP
root       (hd1,0)
savedefault
makeactive
map       (hd0)  (hd1)
map       (hd1)  (hd0)
chainloader  +1


I thought it possible that I inadvertently installed GRUB to the MBR of the XP drive, so...

relevant details from GRUB:

'find /boot/grub/stage1'   returns (hd2,0)


Seems right.  For fun I tried to switch hd1 and hd2 in menu.lst, and this strangely allowed me to load XP from GRUB, but still got error 17 trying to load Ubuntu.


Can anybody tell me if something looks wrong here?  Any help would be greatly appreciated.


Note: I burned a SuperGRUB disc and it recognizes GRUB, Linux, and Windows.  If I select GRUB, I get the same menu I had with regular GRUB and both OSs boot flawlessly.  I just don't want to always have to have the SuperGRUB disc in.

---

### Post by phidia on 2008-04-03
Grub needs to be installed to the drive that is 1st in bios boot order. 
If you don't want the 1st drive to be the drive grub is installed to you will need to 
change that in bios AND edit /boot/grub/menu.lst to reflect the drive that the respective installs 
are on.
If you got an error 17 trying to boot ubuntu it's because the drive order and menu.lst are not in agreement. Hope that helps.

---

### Post by savory19 on 2008-04-03
Thanks for the reply.  

I believe GRUB is now on the drive that is booting first, although the order was different when GRUB was installed.  I can't see why this would matter though since I am able to boot into GRUB on startup and the errors seem to only come in stage2.

If I try to switch the boot priority back to what it was originally I just get XP with no GRUB.

Does the designation of a drive as hd0, hd1, hd2... (and sda, sdb... for that matter) have anything to do with BIOS boot priority?

---

### Post by phidia on 2008-04-04
I think, in bios, the boot order is in the settings either by default or the user.
I have had the bios change the boot order-after a power out situation or crash and it will totally confuse grub-and the errors you listed will be seen.

I would try to reinstall grub from the livecd with everything set the way you want to keep it-respective to drive order.

---

### Post by phidia on 2008-04-04
I think, in bios, the boot order is in the settings either by default or the user.
I have had the bios change the boot order-after a power out situation or crash and it with totally confuse grub-and the errors you  listed will be seen.

I would try to reinstall grub from the livecd with everything set the way you want to keep it-respective to drive order.

---

### Post by Mariuchi on 2008-04-05
Hi, I have the same problem since installation Hardy Beta. Changing boot priority in BIOS messing everything.
I found this page while ago,
[http://users.bigpond.net.au/hermanzone/p15.htm#device.map]("http://users.bigpond.net.au/hermanzone/p15.htm#device.map")
It looks like You said: "designation of a drive as hd0, hd1, hd2... (and sda, sdb... for that matter) have anything to do with BIOS boot priority". 
Good luck in finding solution :)

---

### Post by forrestcupp on 2008-04-05
> **phidia said:**
> 
I would try to reinstall grub from the livecd with everything set the way you want to keep it-respective to drive order.

+1

That is what you need to do.  Keep everything how you have it now, and reinstall grub.  [Here is a guide](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub) to do that if you don't know how.  When you restore Grub, it should put it on the correct drive's MBR and set itself up right.

---

### Post by savory19 on 2008-04-05
The link that Mariuchi provided was very helpful.

Everything is working now (with the Ubuntu drive first in BIOS boot priority) after some edits to device.map and menu.lst

I did not have to reinstall GRUB.

new device.map:

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/hda

new menu.lst items:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)

title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


The lesson I have learned from this is that the sd*/hd* designations seem to be determined by BIOS boot order, while the hd* designations are done by GRUB and for GRUB.  

Thanks everybody for help.

---

