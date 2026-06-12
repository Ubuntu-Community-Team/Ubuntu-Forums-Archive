---
title: "Swap issue after running tune2fs"
date: 2012-10-21
forum: General Help
---

### Post by astralth on 2012-10-21
Hello,

I am running an AO722 under xubuntu 12.04.

I tried to make the noatime and data=writeback changes to my / and /home partitions running as a first step tune2fs -o journal_data_writeback on sda7 and sda5 which fstab designated ad my / and /home partitions.

(On a side note, by researching my issue I read that these changes are no longer useful with the relatime option as default)

However, using the blkid and lsblk -f and fdisk -lu commands I see that sda5 is in fact my swap partition.


Now, running the check all filesystem part of the recovery mode, the system has an issue mounting swap, and swapon -s has no output. Moreover, even though my system is seemingly working fine, gparted sees my sda disk as unallocated.

So my guess is that running tune2fs on my swap partition has corrupted it and that it leads gparted to see my entire disk as corrupted. How can I fix this ?


Thank you for your time in advance, and please do not hesitate to ask me to reformulate my issue.

Thibaud Ruelle

---

### Post by ankspo71 on 2012-10-22
Have you tried using the live cd yet? The live cd will allow you to make changes/corrections to the partitions that would normally be in use on a running system. 

First, check all UUIDs and mount options in the /etc/fstab file on the hard drive. 

Then open the terminal and check the partitions for errors with fsck.

```
sudo fsck -f /dev/sda5
sudo fsck -f /dev/sda6
sudo fsck -f /dev/sda7
etc (see fsck --help for more info)
```

Delete and re-create the swap partition if necessary using gparted. Then recheck the newly created swap partition's UUID to see if it still matches the UUID in fstab on the hard drive.

I haven't used tune2fs in a while because I haven't seen much of any performance gains in the last couple of *ubuntu releases, but more importantly I kept loosing some of my documents during power outages and improper shutdowns.

---

### Post by astralth on 2012-10-23
Hello, thank you for your reply. Here are some updates :

First, my fstab file (it seems according to man fsck that error 2 means that the system needs reboot, however I already rebooted many times since the problem appeared) :

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=55400cc5-9eef-4870-99d7-9833e982092b /               ext4    noatime,errors=remount-ro 0       1
#UUID=55400cc5-9eef-4870-99d7-9833e982092b /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
#UUID=65748ab1-d032-4413-b7f7-0798e74a0692 /home           ext4    noatime,data=writeback       0       2
UUID=65748ab1-d032-4413-b7f7-0798e74a0692 /home           ext4    noatime       0       2
# /windows was on /dev/sda3 during installation
UUID=E2223E75223E4F33 /windows        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda6 during installation
UUID=6f597bd3-e9bc-4265-a4e1-08713e47ea54 none            swap    sw              0       0
#tmpfs
tmpfs    /home/thibaud/.cache/chromium    tmpfs    defaults,noatime,mode=1777,size=512M    0    0
tmpfs    /tmp    tmpfs    defaults,noatime,mode=1777,size=256M    0    0
```Here is the output of blkid (as you can see fstab thinks sda5 is /home while its actually the swap partition) :

```
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="122d23c0-2c64-40b8-831f-1260b1a8e6d7" TYPE="ext3" 
/dev/sda1: LABEL="PQSERVICE" UUID="DC483C3A483C162C" TYPE="ntfs" 
/dev/sda2: LABEL="SYSTEM RESERVED" UUID="CCA83CB8A83CA2BE" TYPE="ntfs" 
/dev/sda3: LABEL="Acer" UUID="E2223E75223E4F33" TYPE="ntfs" 
/dev/sda5: UUID="6f597bd3-e9bc-4265-a4e1-08713e47ea54" TYPE="swap" 
/dev/sda6: UUID="55400cc5-9eef-4870-99d7-9833e982092b" TYPE="ext4" 
/dev/sda7: UUID="65748ab1-d032-4413-b7f7-0798e74a0692" TYPE="ext4" 
/dev/sdb1: UUID="68F6-B59F" TYPE="vfat" 
```And finally the fsck outputs :

```
xubuntu@xubuntu:~$ sudo fsck -f /dev/sda5
fsck de util-linux 2.20.1
fsck: fsck.swap: not found
fsck: error 2 while executing fsck.swap for /dev/sda5

``````

xubuntu@xubuntu:~$ sudo fsck -f /dev/sda6
fsck de util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
Passe 1 : vérification des i-noeuds, des blocs et des tailles
Passe 2 : vérification de la structure des répertoires
Passe 3 : vérification de la connectivité des répertoires
Passe 4 : vérification des compteurs de référence
Passe 5 : vérification de l'information du sommaire de groupe
/dev/sda6 : 327232/1220608 fichiers (0.1% non contigüs), 2652140/4882432 blocs

``````

xubuntu@xubuntu:~$ sudo fsck -f /dev/sda7
fsck de util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
Passe 1 : vérification des i-noeuds, des blocs et des tailles
Passe 2 : vérification de la structure des répertoires
Passe 3 : vérification de la connectivité des répertoires
Passe 4 : vérification des compteurs de référence
Passe 5 : vérification de l'information du sommaire de groupe
/dev/sda7 : 261990/15351808 fichiers (0.7% non contigüs), 30985482/61395712 blocs

```Unfortunately, I cannot use gparted to delete and recreate the swap partition because it sees the whole sda disk as unallocated ...

Thank you for your help !

---

