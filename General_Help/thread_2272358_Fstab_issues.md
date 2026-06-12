---
title: "Fstab issues"
date: 2015-04-06
forum: General Help
---

### Post by john364 on 2015-04-06
I have just rebuilt my linux machine with a new mobo and hard drives.

I did a fresh install of Lubuntu 14.10

I have made folders for where I want my drives to mount.
/media/storage1 , /media/storage2 etc etc

I can use mount -a and the drive will mount find to that directory.
when i reboot linux just hangs at the lubuntu screen.

FSTAB below:
[INDENT][I]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=2ca5684a-5130-437a-8026-b8c575b41e7d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=4d29240e-bd7e-47c1-bbb8-a121486d6695 none            swap    sw              0       0
/dev/sda1 /media/stuff   ext4  defaults       0  2 
/dev/sdb1 /media/stuff2  ext4  defaults       0  2 
/dev/sdc1 /media/stuff3  ext4  defaults       0  2
[/I][/INDENT]


When I remove all the /dev/.... lines from the fstab linux will boot fine...

Any ideas what could be wrong?

---

### Post by buzzingrobot on 2015-04-06
You can only mount partitions, not folders.

---

### Post by plucky on 2015-04-06
> I have made folders for where I want my drives to mount.
/media/storage1 , /media/storage2 etc etc

That does no equate to > /dev/sda1 /media/stuff ext4 defaults 0 2
/dev/sdb1 /media/stuff2 ext4 defaults 0 2
/dev/sdc1 /media/stuff3 ext4 defaults 0 2


Probably why the boot is hanging as it cannot find the directories.

Are you editing /etc/fstab?

Read [Fstab](https://help.ubuntu.com/community/Fstab)

and [Auto-Mount](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

Are the drives internal or connected via USB?

Good Luck

---

### Post by ajgreeny on 2015-04-06
You will probably do better to use UUIDs in fstab.
Run command ```
sudo blkid -c /dev/null
```with all the disks attached and then edit your fstab file to use UUIDs from that command's output instead of /dev/sdx# using the same format as the lines already present in fstab for the root and swap partitions.

Your problem may be caused by the way that /dev/sdx# numbers can change at boot time depending on the timing of detection of the disks, whereas UUIDs will not change.

EDIT:
Well done plucky, I didn't notice the inconsistency in the folder name compared with mountpoint names, however, the problem would also be seen when running **sudo mount-a** if that was really the case, so that may be a typo.

---

