---
title: "Reinstall of Feisty on Dual-Boot Machine?"
date: 2007-07-29
forum: General Help
---

### Post by A. J. Rimmer on 2007-07-29
I've searched the forums and documentation, but can't quite find an answer to this one:

I have Feisty installed on an HP dv5220 laptop in a dual-boot configuration with Windows XP.  I originally installed Dapper several months ago, and recently did a double upgrade to Edgy, and then immediately to Feisty, using the Alternate CDs with network support.

Having tinkered with Ubuntu for several months now, I'm inclined to delete everything and do a fresh install and update of Feisty, just to get everything back to the "stock" configuration (so I can start tinkering, tweaking, and learning again, and to make sure nothing got misconfigured by the series of upgrades and updates.).

I'm not sure how to go about this, though.  I could just use Gparted to delete the Linux partition, but if anything goes wrong along the way I think I would be stuck with an unbootable machine, since Grub would no longer be able to find menu.lst.

I don't know if I could just install Feisty over Feisty, and if I could, I don't know how that would affect Grub and the MBR.

It seems that I know enough to know there might be problems, but don't know how to avoid them.

If anyone has guidance on how to do this (do a fresh reinstall of Feisty without disturbing Windows and without messing up my dual-boot configuration), I'd appreciate the advice.

(I'd get rid of Windows entirely, but I still use it as a DVR with a Happauge HVR-950 USB HDTV tuner.)

Thanks!

---

### Post by confused57 on 2007-07-29
You shouldn't have any problem installing a fresh Feisty on your current Ubuntu partitions...just choose manual partitioning, select your current partition(s), format(ext3 for root), set mountpoint(/ for root), primary or logical...do the same for your current swap(mountpoint swap, logical?, format as swap)...using the Feisty alternate install cd, which would be easier than the live cd.  If you have a separate /home partition & want to keep the current configurations & data, just select not to format, but select /home for mountpoint....just make sure not to format your Windows partition(you can probably leave everything "as is" in the partitioning step).

The new Feisty install should recognize your Windows, place an entry in grub, & install grub to the mbr for dual boot...

Added:  Excellent screenshots here installing with the alternate cd:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
Note:  When you're reinstalling over your / partition, there is an option to "keep existing data"...you definitely don't want to keep existing data for the root partition, I tried this one time & ended up with quite a mess on the new install.

---

### Post by A. J. Rimmer on 2007-07-29
Thanks for the quick and detailed reply!  ):P

I have the alternate CD available, and will take a look at the screen shots.  Probably will do a dry run first without actually pressing the "go" button just to make sure I understand the options.

Wish me luck!

-- "Smoke me a kipper, Skipper, I'll be back for breakfast."  -- "Ace" Rimmer

Edit: OK, I just opened the "Illustrated Dual Boot Site" in another tab.  Looks like a terrific resource.  By the way, my system is currently set up with Windows on NTFS, Ubuntu on EXT3, and a 4GB FAT32 partition so that I can pass files between the two OSs.

---

