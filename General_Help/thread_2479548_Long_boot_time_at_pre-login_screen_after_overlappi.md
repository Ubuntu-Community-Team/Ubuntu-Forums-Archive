---
title: "Long boot time at pre-login screen after overlapping partitions with GParted"
date: 2022-09-28
forum: General Help
---

### Post by xanizen on 2022-09-28
I tried to use GParted to move a deleted swap partition to the right side of 32GB ext4 partition. I decided to terminate the operation, since the progress bar stayed at 1/3rd completion.

I launched the Ubuntu Live CD and used Fdisk to delete the swap partition and the 32GB ext4 partition. Yet Ubuntu will take 3 minutes in stead of 10 seconds to reach the Login screen prompting for Username/Password.

I generated the following output with [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"): 
[URL="https://pastebin.ubuntu.com/p/hrQxHMDkpw/"]https://pastebin.ubuntu.com/p/hrQxHMDkpw/
[/URL]Thi

This is the /etc/fstab file, after making a new swap partition through fdisk and mkswap commands. It seems the UUID is referring to the old swap partition I deleted. I'll report back.
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=e859f894-d531-4638-8a0d-472fa69556ad /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=92c4670b-a6cd-489b-bd73-8aaf6b8ac865 none            swap    sw              0       0


```

Updating the UUID in /etc/fstab seems to have fixed the problem.

---

