---
title: "I screwed up my computer"
date: 2007-05-13
forum: General Help
---

### Post by bo. on 2007-05-13
I downloaded Ubuntu and loaded it up from a cd then installed it on an external hard drive.  But now I cant get Windows or Ubuntu to load on it.  (Im running my computer off the live cd right now.)  When I start it up it says GRUB 1.5 loading then says error 25 and freezes up every time.  I disconected the external hd which has linux and tred to just run off the hdd with windows but the same thing hapens.  Any help?

---

### Post by bo. on 2007-05-13
I just want to get rid of this grub and run windows again I got another computer for ubuntu.

---

### Post by joe.turion64x2 on 2007-05-13
To get rid of grub you have to restore Windows MBR (master boot record). The easiest way to do that is using the Windows CD, go to Recovery mode and select something like fixmbr. You can search this in Google so you can get more accurate instructions.

---

### Post by orb9220 on 2007-05-13
> I just want to get rid of this grub and run windows again I got another computer for ubuntu.

You need to boot the xp disk and enter into recovery mode at the prompt type:
fixmbr
that will restore the mbr to xp.

---

### Post by nickoli_02 on 2007-05-13
I'm assuming the external drive is usb/firewire, right? Did you enable the option in your BIOS to boot from a USB/firewire device? If not you'll have to do that, possibly some other configurations but I'm not sure. That shouldn't screw up your grub though, unless, maybe it's loaded on the MBR of your external drive....

sorry, I'm just rambling possible scenarios. I'm not really sure what you can do.

---

### Post by floke on 2007-05-13
It looks like you installed grub to the MBR of your actual hard drive rather than your external hard drive. I would strongly advise you to read up on installing to external drives before trying this. You could try this:

From the live CD - can you see you partitions on your hard drive? If so, mount the linux one and edit the grub file: From the terminal - sudo nano /boot/grub/menu.lst

Add this to it

title Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

And reboot - you 'should' (hopefully) then be able to enter Windows (not sure if this is good or bad though :) )

Good luck

---

