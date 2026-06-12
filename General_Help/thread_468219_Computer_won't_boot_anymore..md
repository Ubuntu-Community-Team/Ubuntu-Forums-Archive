---
title: "Computer won't boot anymore."
date: 2007-06-08
forum: General Help
---

### Post by astanix on 2007-06-08
I don't think I've done anything to the computer since I rebooted last time.  Didn't mess with the drive or partitions or anything like that so I'm not exactly sure what could be causing this problem.
I rebooted my computer today and now it's trying to boot from the network.
I went to change the boot order in the BIOS and it was set to CD, HD, Network.
I changed it to HD, CD, Network.  Still didn't work.  I changed it back to CD, HD, Net and tried to boot from an Ubuntu CD.  This worked fine.  I chose the option 'boot from first hard disk and it just hangs at Booting from first hard disk...
The bios still detects my hard drive, so it's there and as far as I can tell it's working.  I'm not really sure what could have happened during a reboot to cause the HD to no longer be bootable.
This is an Acer C310 Laptop.

---

### Post by merlinus on 2007-06-08
If you boot from the ubuntu live cd, can you see any data on your hard drive?

If so, then it is possible that your boot sector somehow got trashed.

-merlin

---

### Post by palmtree on 2007-06-08
I am having similar problem which seems to have happened since the last update that installed the new kernal (16). I have tried booting to the previous kernal (15) with poor success. It works sometimes but not at all today.  I can still boot to Windows XP. My system is a dual boot configuration with two HD's, one for XP and the second for Ubuntu. I am not sure if folks that have Ubuntu as their sole system (i.e. not dual boot) are experiencing similar problems booting. I am hoping its a Ubuntu problem that will be fixed through an update.

---

### Post by astanix on 2007-06-08
> **merlinus said:**
> If you boot from the ubuntu live cd, can you see any data on your hard drive?

If so, then it is possible that your boot sector somehow got trashed.

-merlin

I got it booted to the live CD system and my drive is mounted with all the data there.  I went into the gnome partition manager and that drive is still marked as bootable.

[quote=palmtree]I am having similar problem which seems to have happened since the last update that installed the new kernal (16). I have tried booting to the previous kernal (15) with poor success. It works sometimes but not at all today. I can still boot to Windows XP. My system is a dual boot configuration with two HD's, one for XP and the second for Ubuntu. I am not sure if folks that have Ubuntu as their sole system (i.e. not dual boot) are experiencing similar problems booting. I am hoping its a Ubuntu problem that will be fixed through an update.[/quote]

I'm on an Ubuntu only system.  I suppose it could be an update issue due to the fact that I accept all updates without even really looking at them.  I should have learned my lesson regarding that with Windows, but I figured updating in Linux wouldn't break anything. :)

---

### Post by astanix on 2007-06-08
OK, so I booted into the live cd and unset the drive as bootable and then reset it as bootable and now it doesn't even make it to netowork boot.  It just hangs with a flashing cursor in the top left corner of the screen.
It also hangs at the "Booting from local disk..." still when I choose boot from disk on the CD.
I looked over all the grub files and they look good.
I'm sure there's a simple fix to this out there, I'm just too much of a novice to even know where to start.

---

### Post by merlinus on 2007-06-08
Did you compare /boot/grub/menu.lst to the kernels in /boot?

Also, it is possible that the grub root got changed.  This happened to me when I upgraded to the -16 kernel.

-merlin

---

### Post by astanix on 2007-06-08
The menu.lst looks fine, it had been upgraded to 16 it appears... and 16 is in there.
What do you mean that the grub root got changed?

---

### Post by merlinus on 2007-06-08
It changed from (0,7) to (0,6) and so the computer would not start.

My understanding is that the upgrade assumed that ubuntu was on the first ext3 parfition.  In my case, it is on the second.

I fixed it by pressing e at the opening screen, which allowed me to edit it back to the correct settings.

-merlin

---

### Post by astanix on 2007-06-08
It was at 0,0 and unchanged to my knowledge.

root (hd0,0)

(hd0) /dev/sda

gparted says

/dev/sda1 ext3
/dev/sda2 ext
/dev/sda5 swap

It all looks ok to me...

---

### Post by astanix on 2007-06-08
Well, I tried to do sudo grub and fix it myself but I kept getting errors.  I downloaded and used the Super Grub Disc and used that to fix it and now the problem is gone.  Thanks for the help everyone. :)

---

### Post by merlinus on 2007-06-08
Grubby, man!

:D

-merlin

---

