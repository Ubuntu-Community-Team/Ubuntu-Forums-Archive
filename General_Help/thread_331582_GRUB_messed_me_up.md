---
title: "GRUB messed me up"
date: 2007-01-04
forum: General Help
---

### Post by Bunny Boy on 2007-01-04
I've got two computers. One has a 6 GB hd running WinPro2k. The second has a 120 GB hd running ubuntu 6.06.

I had installed the 6 GB hd in the second computer when I installed ubuntu, so I could get some data off of the disk.  When I put the 6 GB hd back into the first computer, it wouldn't boot. The message "GRUB disc error" appears and that's it. 

I'm unclear on why GRUB would even write to the 6 GB hd, and I have no idea how to fix it. I installed the 6 GB hd back into the second computer, thinking maybe I could edit whatever it is on the boot partition causing the problem, but can't find anything. 

Any idea what I can do to make my Win2k boot again?

---

### Post by tzulberti on 2007-01-04
Surely, when you installed the second drive in your machine, the partitions changed. You should use a livecd to restore grub. Here are some howtos:
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29)

---

### Post by Bunny Boy on 2007-01-05
> **tzulberti said:**
> Surely, when you installed the second drive in your machine, the partitions changed. You should use a livecd to restore grub. Here are some howtos:
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29)

I'm confused. I don't think the partitions changed. There were two partitions on the Win drive, one NTFS and the other FAT32. I can mount them and access the files from them. (which is the reason I installed the drive in computer #2). I did not set up a multi-boot when I installed ubuntu, so I don't think "restoring" GRUB is the issue. I need to somehow remove whatever GRUB did to the mbr of the Win hd so I can boot it in computer #1.

I'm sorry if this wasn't clear:  there's no multi-boot system. The Win hd wouldn't be able to boot in computer #2 anyway, because it's configured for a completely different motherboard (computer #1).

---

### Post by ulisse on 2007-01-05
hmm... I think you installed grub on the 6GB hard disk MBR, and it points on a menu.list on the other HD.
Are you able to run the ubuntu pc without the 6GB hd?

Dunno if it is the same for w2k, but in xp you can boot from the win cd (on the pc with the 6 GB hd), fire up the recovery console and type:

fixmbr
fixboot

(may be something uppercase, like fixMBR, don't remember)

in this way you should remove any existing grub in that hd and restore the original windows bootloader.

---

### Post by komaroveli on 2007-01-05
when you installed HD on computer did you checked master/slave plugs?
your primary drive must be set to master drive and secondary (6Gb win drive in your case) to slave. then check in bios boot sequence settings. in those settings set you primary drive as leading drive.

---

