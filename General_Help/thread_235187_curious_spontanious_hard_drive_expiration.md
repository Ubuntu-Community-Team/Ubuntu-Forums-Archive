---
title: "curious spontanious hard drive expiration"
date: 2006-08-12
forum: General Help
---

### Post by Huffers on 2006-08-12
After leaving my PC idle for some hours I came back and found Gnome distorted and covered in vertical lines.

I restarted by switching to a terminal with "ctrl+alt+f1" and blindly typing "sudo shutdown -r now".

But instead of going into grub it said: "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"

So I downloaded a Linux live CD (Knoppix), and took a look in /dev. Instead of having sda, sda1, sda2 and sda3 (my drive, sda, had been partitioned into a ntfs, fat32, swap, and an ext3 partition) it just had /dev/sda.

"strings /dev/sda | less" gave strings that appeared to be from grub, then some from Windows (the ntfs partition). I didn't look further than that.

fdisk said no valid partition table found
sfdisk said no partition table present
cfdisk reported similar

What has happened?
What are the chances of this happening?
Shouldn't partition tables have some redundancy/error-recovery in them if becoming corrupt can happen at random and cause such catastrophic damage?
What should I do (I don't have a backup)?

If my data is unrecoverable, this should serve as a warning/reminder to others that drives can be completely and instantaniously lost at any time, even if you aren't doing anything considered 'dangerous' on it (eg repartitioning). 

Note: this drive was about 2 years old.

---

