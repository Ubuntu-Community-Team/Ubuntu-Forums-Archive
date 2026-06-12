---
title: "Is it possible to use 2 pertitions/disks as one partition/disk in Ubuntu? and also"
date: 2019-11-09
forum: General Help
---

### Post by jasper99 on 2019-11-09
the ROOT? and how?
As in Windows:[URL="https://www.howtogeek.com/235348/how-to-combine-multiple-partitions-into-a-single-partition/"]
https://www.howtogeek.com/235348/how-to-combine-multiple-partitions-into-a-single-partition/[/URL]

(don't know of this can with the ROOT in Windows)

---

### Post by The Cog on 2019-11-09
Yes it can use two partitions as one. The traditional method would be ot use LVM (Logical Volume Manager), [https://www.digitalocean.com/community/tutorials/an-introduction-to-lvm-concepts-terminology-and-operations](https://www.digitalocean.com/community/tutorials/an-introduction-to-lvm-concepts-terminology-and-operations)
It's somewhat easier to understand (I think) if you format them as btrfs [https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices](https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices)
I bet zfs can do it as well, but I am not familiar with it.

The article you link does not describe using two partitions as one. It describes deleting one and expanding the other to encompass the freed space. The easiest way to do that in Linux is (to my mind) to use gparted, which looks rather like the tool the article uses, and do the same procedure. But I don't thnk gparted can do it to windows partitions any more than windows could do it to Linux partitions.

---

### Post by CatKiller on 2019-11-09
> **The Cog said:**
> But I don't thnk gparted can do it to windows partitions any more than windows could do it to Linux partitions.

Gparted *can* manipulate Windows partitions but, because support for them has been reverse-engineered, it's less capable of fixing things with Windows partitions than native Windows tools if something unexpected happens. Windows partitions also degrade over time, which Linux tools can't fix, so you need Windows tools available anyway if you're messing around with Windows partitions.

---

### Post by CatKiller on 2019-11-09
> **jasper99 said:**
> the ROOT? and how?
As in Windows:[URL="https://www.howtogeek.com/235348/how-to-combine-multiple-partitions-into-a-single-partition/"]
https://www.howtogeek.com/235348/how-to-combine-multiple-partitions-into-a-single-partition/[/URL]

(don't know of this can with the ROOT in Windows)

Linux doesn't use drive letters and partitions like Windows does. The filesystem is one unified tree already. You access partitions through their mount points, which you can set to be anywhere in the filesystem tree.

---

### Post by TheFu on 2019-11-09
The term "ROOT" can be confusing, since there are at least 3 different meanings for it.

[LIST]
[*]"root" is the username of the required administration account on all Unix systems. root has a uid of 0.
[*]/ is the root directory. The only directory on any Unix system that doesn't have a parent.
[*]/root is the home directory for the root account.
[/LIST]


Most users think of **su** and **sudo** as a way to elevate their current privilege level to that of the root account, though both commands can do so very much more. People usually say they need 'root', which means they want to change to the *privilege level* of the root userid.

On Unix-like systems, including Linux systems, any disk object can be formatted with a file system and mounted to any directory.  Any file system objects under that mount point, already existing, are hidden when the other file system is mounted on top.
[LIST]
[*]/ - is the only required file system/partition/LV
[*]/boot - is often a file system/partition/LV used for booting Linux.
[*]/boot/EFI - is a FAT32 file system/partition used for UEFI files and boot information.
[*]/home - is often a separate file system/partition/LV which holds user HOME directories. This is a best practice to allow OS upgrades to only impact the / partition, leaving /home untouched.
[/LIST]
For example, here's how mounts are handled on my laptop:
```
$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem                      Type  Size  Used Avail Use% Mounted on 
/dev/mapper/ubuntu--vg-root     ext4   25G   14G  9.3G  61% /
/dev/sda2                       ext2  721M  185M  500M  27% /boot
/dev/sda1                       vfat  511M  3.7M  508M   1% /boot/efi
/dev/mapper/ubuntu--vg-home--lv ext4   74G   21G   51G  29% /home
/dev/mapper/ubuntu--vg-stuff    ext4   99G  367M   93G   1% /stuff
lxd/containers/devoted-sunbird  zfs    15G  421M   14G   3% /var/lib/lxd/containers/devoted-sunbird.zfs
istar:/D                        nfs   3.5T  3.5T   41G  99% /D 
```
Don't worry, the options to **df** above are just to hide things that show up, but aren't real storage.
My example above shows different file systems, ext2/4, vfat, zfs, nfs and how things can be mounted for different purposes at both top directories like /boot, /stuff, /home and deeper locations like /var/lib/lxd/containers/devoted-sunbird.zfs.  It also shows how NFS (network file systems) are shown as local storage when mounted with the last line.  I use LVM too.

There's only 1 local disk (500GB SSD) and 1 remote disk in output above.

Fun stuff.  Extremely flexible.

---

