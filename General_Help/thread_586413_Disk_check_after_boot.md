---
title: "Disk check after boot"
date: 2007-10-22
forum: General Help
---

### Post by stevesutt89 on 2007-10-22
Hi All!
Great to be Back in Ubuntu,
Just one problem. I have fsck configured to check the disks every 20 boots, however every time i boot fsck runs "checking" the file systems for 14 seconds (a long time considering boot only takes 52 seconds into xfce) beofre proceding with the boot

the problem is not that fsck is fully checking the filesystem on everyboot, it just seems to be doing a "quick" on every boot check every boot which consumes an annoying 14 seconds

Anyhow, since i wanted to get the system booting asap i disabled fsck permanently by changing the last number in the /etc/fstab file to 0 for all partitions.  

Now, since i don't want to go without checking the file systems ever, i was wondering if there is a way to manually do this once the computer is loaded?

Thanks

---

### Post by kosmic on 2007-10-22
Yes you can use the  "e2fsck" command to check a Linux ext2/ext3 file system.

Just make a cronjob to run it or put it in init.d, to start after your Gnome or kde

---

