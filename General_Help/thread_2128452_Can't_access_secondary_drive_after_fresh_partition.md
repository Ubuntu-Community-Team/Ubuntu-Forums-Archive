---
title: "Can't access secondary drive after fresh partitioning/format (wrong permissions)"
date: 2013-03-23
forum: General Help
---

### Post by nortexoid on 2013-03-23
I just bought a new SSD. I set up Kubuntu 13.04 beta on it and now want to use my old 1GB HDD as secondary storage. I've partitioned it using both a liveCD (opensuse), Kubuntu 13.04's KDE partition manager and gparted. Using each of these methods, I can't access my disk: the permissions seem to be wrong, and I can't set them to the correct user.

Can anyone tell me how to wipe a secondary (whether USB or SATA) drive under a given account to use with said account? I would most grateful!

---

### Post by Bashing-om on 2013-03-23
nortexoid;

This tutorial is what I use -from the command line.
[http://help.ubuntu.com/community/InstallingANewHardDrive](http://help.ubuntu.com/community/InstallingANewHardDrive)[INDENT=3]
works for me

[/INDENT]

---

### Post by oldfred on 2013-03-24
I think the link from bashing-om has the commands, but quickly and not for NTFS formatted partitions.

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo fdisk -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
chmod -R a+rwX,o-w /mnt/data
 # Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
 #All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown $USER:$USER /mnt/data

If an internal drive then you want to permanently mount with fstab.
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

More info:
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by nortexoid on 2013-03-25
Many thanks. I managed to get it sorted by mounting with fstab, running a kdesu dolphin and changing the user/group there to the correct one. I wish the standard partition managers (or a newly written app) would automate all this stuff or present it to the user in a transparent and understandable way.

---

