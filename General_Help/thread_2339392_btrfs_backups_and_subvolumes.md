---
title: "btrfs backups and subvolumes?"
date: 2016-10-08
forum: General Help
---

### Post by ubudabi on 2016-10-08
Hi all,

I've recently installed Kubuntu 16.04 with btrfs coming from 14.04 with ext4 on a SSD 256 GB. Without knowing much about btrfs I have proceeded with the installation like I did with ext4. I have formatted with GParted a partition with 100 GB for root and left the home partition as is (ext4) and installed Kubuntu on the root partition. Now I am able to boot into the system but I have the following issue: I want to do backups of the root partition so I tried with "Timeshift BTRFS" ([http://www.teejeetech.in/2014/10/introducing-timeshift-btrfs.html](http://www.teejeetech.in/2014/10/introducing-timeshift-btrfs.html)) 
Unfortunately when I try to backup I get the following error:
> BTRFS partition '/dev/sdd1' has an unsupported subvolume layout. Only ubuntu-type layouts with @ and @home subvolumes are currently supported
This error was already mentioned in this blog but the solution > sudo btrfs subvol set-default 5 / didn't help.
I also tried with another tool (btrbk) but I get a similar error.

With:
[I]$ sudo btrfs subvolume list /
I get:
ID 257 gen 2748 top level 5 path @ [/I]

1. So where is the problem? Why these errors? Is not my root in a @ subvolume?
2. What is the general procedure for installing Ubuntu on a btrfs partition?
3. Since I don't want to install Kubuntu again soon what are my options now? (I have another free btrfs partition formatted with GParted. Can I somehow use this partition to correct the errors by moving root to this partition without loosing my configurations e.g. with cloning?)


Any suggestions?
Thanks in advance!

---

### Post by The Cog on 2016-10-08
Having let the installer install to a single btrfs partition before now, I have always seen that it creates two subvolumes with names @ which is mounts as the root partition (subvol=@ is one of the mount options) and @home which is mounts as the home partition (subvol=@home).
This of course means two lines in fstab. I usually add a compress option to the @home subvolume.

The real btrfs volume is not mounted at all in this setup, so I always create a /mnt/btrfs mount point where I can mount the real volume if I want to. I think you need this if you want to create snapshots of /home, like this: 
```
mount -t btrfs /dev/sda5 /mnt/btrfs
cd /mnt/btrfs
btrfs sub snap @home home-snap-oct-2016
```

P.S. You can rename the subvolumes when you want to restore an old snapshot, and then reboot:
```
cd /mnt/btrfs
mv @home home-knackered
mv home-snap-jun-2016 @home
```
but don't confuse creating folders/directories with creating subvolumes. They look the same but they are not.

---

### Post by ubudabi on 2016-10-08
@The Cog: Many thanks for the quick response!
Does it make any any difference that it is the root partition I want to backup and not the home partition following the way you suggested? I did try like you said and it has indeed created a folder with the whole structure of root almost instantly. (Wow!) The generated backup has in comparison to the mounted partition 4 files less. I have tried to create a new snapshot to an external hard disk with ext4 with:
*$ sudo btrfs sub snap @ /media/nick/BACKUPS/mysnapshots/rootpartition-snap-20161008b*
 but I got an error:
*R: not a btrfs filesystem: /media/nick/BACKUPS/mysnapshots*
So, snapshots can only be created on btrfs? Can I simply move the created backup to my external hard disk without issues?

If I can make backups this way is OK for me now. But did I something wrong during the installation? Why are these tools (timeshift BTRFS and btrbk) complaining?

---

### Post by The Cog on 2016-10-08
A btrfs snapshot is a subvolume on the same volume as the volume it is snapshotting. It has tt be on the same volume because it doesn't make a copy of the data it is snapshotting - it makes another directory pointing to the same data. Then when either the data or the snapshot is written to, new data is written to disk and the two images begin to have their own independent copies that can be different to each other. But initially, the snapshot shares its data completely with the original. Clearly, this can only happen within a single volume.

---

