---
title: "want to end dual boot without loosing second distro."
date: 2018-06-03
forum: General Help
---

### Post by joel93442 on 2018-06-03
I have been running Mint XFCE dual booted with Ubuntu. I want to devote my entire disc to ubuntu but don't want to reinstall totally. Can I just delete the partition in gparted then expand ubuntu partition or will I need to do a clean install of Ubuntu?

---

### Post by oldfred on 2018-06-03
Depending on where partitions are on drive, it could be easy, or difficult.
You expand partitions right.
But if you have space on left, you have to move it left first and that can take a long time. And any interruption corrupts data totally, so be sure to have good backups.
And if the older BIOS/MBR configuration, partition and unallocated space has to be either all primary or all logical inside extended.

Post this:
sudo parted -l

Another alternative is to just reformat Mint and use that partition as /mnt/data or if large /home/

---

### Post by TheFu on 2018-06-04
This would be a good opportunity to test your backup and restore plans.  In a real situation, say the HDD fails, what will you do?  With the current situation, you'd have a chance to test everything.  ;)

I'm assuming you have backups and didn't do whole disk imaging.  If the backups are at the partition level or file level, you should be fine.  Some manual intervention will be needed, but you'll need to know how to do that for a real disk failure too.

---

### Post by Dennis N on 2018-06-04
> Can I just delete the partition in gparted...

No, it may not be as simple as that. You could lose the ability to boot the computer.
The correct procedure depends on:
Are you using UEFI or BIOS?
Which OS displays the grub menu when you start up your computer?

---

### Post by joel93442 on 2018-06-04
Thanks guys. I have pretty complete backups of my files, which is all I'm really concerned about, so I guess I will just reinstall. Not really a big deal either way. Thanks again.

---

