---
title: "Bootable from flashdrive?"
date: 2008-05-24
forum: General Help
---

### Post by sugarfresh on 2008-05-24
i was jc if i could download the installer and run it from a 1GB flashdrive, or basically install ubuntu from a flashdrive.

---

### Post by xfceuser on 2008-05-24
for this purpose you need to boot from USB, which your BIOS must have an option for (not all have !). then you must copy the CD structure from the ISO file exactly on the USB drive (which needs a special program).
Alternatively you could use a USB cd player, if all you need is connection via USB port.

---

### Post by sugarfresh on 2008-05-24
lol pretty sure that was a copy+paste reply, lol, but basically can i just copy the iso to my flashdrive and run it to install ubuntu not as a  live cd but as my actual os, windows xp as screwed up on me for the last time, actually 3 times if u count when i got a virus. but can i just copy the iso to my usb drive and run it?

---

### Post by sugarfresh on 2008-05-24
maybe i should've made the title "install ubuntu from flashdrive?" cuase that is my question not if i can have the os on my flashdrive. out of cd-r disks.

---

### Post by xfceuser on 2008-05-24
again the answer is the same (if you wish again a "copy+paste reply" !)
because when you want to install ubuntu, you need to boot from the installation CD, and no computer can boot from iso files alone !

---

### Post by sugarfresh on 2008-05-24
That's depressing, i don't have a cd-r at hand rite now, and my other pc that is much faster than this is inoperable bc of a windows xp error. it does run in sm though, is there anyway that i could install ubuntu without a cd, like wubi and then installing from that? i want to make it main os and delete xp completely

---

### Post by xfceuser on 2008-05-24
try this:
[http://www.bootdisk.com/pendrive.htm](http://www.bootdisk.com/pendrive.htm)
if you could boot from the USB and boot from the iso of Ubuntu ...
It might not be easy ...

---

### Post by xfceuser on 2008-05-24
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
this one is for linux ...

---

### Post by astadolfo3 on 2008-05-24
You could use a friend's PC (or another PC you have access to) to run the installationCD and install a bootable version of ubuntu into your USB key. Keep the video drivers generic. Then you can use the same USB key to boot your PC and customize your configuration.

---

### Post by xfceuser on 2008-05-24
this a guide to exactly what you want to do,

[http://mhashem.wordpress.com/2008/05/10/install-ubuntu-from-usb-flash-memory/](http://mhashem.wordpress.com/2008/05/10/install-ubuntu-from-usb-flash-memory/)

but it needs you already have a running Ubuntu somewhere ...

---

### Post by sugarfresh on 2008-05-25
would a wubi ubuntu count as a running linux?

---

### Post by Inventech on 2008-05-25
> **sugarfresh said:**
> would a wubi ubuntu count as a running linux?

Yeah, why not?:)

---

### Post by sugarfresh on 2008-05-25
well i'm just curious in order to install ubuntu most people run a live cd, and install onto a harddrive after ubuntu has booted up from cd. is there a way to install ubuntu on its own partition after doing the 30GB install using wubi. basically can i use wubi and actually install ubuntu on its own partition larger than 30GB?

---

### Post by AndyCee on 2008-05-27
Just to verify: You want to install a Ubuntu partition FROM wubi?

---

### Post by werries on 2008-05-27
i think he wants to put it on a flashdrive w/ wubi. and then put it on a partition from the flashdrive.
well wubi does count if you've got ubuntu in it. 
so heres the best guide i've found (besides from [www.pendrivelinux.com](www.pendrivelinux.com))
[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

---

### Post by issih on 2008-05-27
You certainly can install ubuntu from a usb drive, I did it just a few days ago. See here:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

This is from memory as I am sitting downstairs beer in hand and don't feel like moving, so its not going to be perfect, but here goes.

1. Get hold of live cd iso file.
2. Mount iso file.
3. Copy EVERYTHING from the mounted iso to the flash drive, including hidden files ("cp -r" is your friend here).
4. change the name of the isolinux folder and the isolinux.cfg file inside it to syslinux and syslinux.cfg respectively.
5. run "syslinux -s /dev/<X>" were <x> is your flash drive.

That is a bit technical I know, so just yell at me if I went over your head anywhere, have a read of the web page anyway, and know it IS achievable, even if it is a bit of a fiddle :)

---

### Post by sugarfresh on 2008-05-29
thank you all for your responses, but i tried several things, and i just had to wait till i got to school and barrowed a cd from my teacher of my computer repair class, thx though:)

---

