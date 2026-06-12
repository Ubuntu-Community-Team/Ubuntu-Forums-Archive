---
title: "Ubuntu Server 14.04 RAID Array Issue"
date: 2015-10-22
forum: General Help
---

### Post by jason_smith3 on 2015-10-22
Hello! 

This is my first post and I am pretty new to Linux/Ubuntu. I am a huge fan of the OS, but I don't know that much about it yet. 

I have an Ubuntu server (No GUI) in my home. It has 3 drives. 1 Primary HDD containing the OS, and two other HDD that are set up as a RAID 1 Array using mdadm. I use the two drives as my primary storage for all of my devices. I usually SFTP into it, or if I am at home I will access it with samba. Very recently my primary HDD containing Ubuntu failed. I could not clone the drive so I bought a new primary and did a fresh install. Now when I run -l fdisk the array is no longer mounted under /dev/md0 like I had set it. It is mounted under /dev/ followed by some ridiculously long name (I am not near my server at the moment but I will post it if necessary. This is expected but I was wondering how I could remount the RAID without formatting the drives, because they are full of important data.

If I can't mount them without formatting, can I take just one of the drives from the array and copy the data to another computer?

Thanks!

---

### Post by SeijiSensei on 2015-10-22
Are you mounting the array from [/etc/fstab]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")?  Something like
```
/dev/md0     /media/data   ext4 defaults 0 0
```

---

