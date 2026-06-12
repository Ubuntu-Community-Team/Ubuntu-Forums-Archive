---
title: "[SOLVED] SD card reports full, but should still be half empty"
date: 2007-12-26
forum: General Help
---

### Post by sciencewhiz on 2007-12-26
I have a 1 GB SD card (formatted FAT32) that I occasionally use in Ubuntu 7.10 (it's normally in my palm).

Yesterday, I copied some stuff over to it in linux and accidentally filled the card up. I then deleted one of the big files. Now, it still complains that the disk is full whenever I try to copy something to it.

df and the nautilus properties show it is full

> Filesystem            Size  Used Avail Use% Mounted on
/dev/mmcblk0p1        981M  981M     0 100% /media/SECOND1GB

however, du shows plenty of space

> 125K    ./PALM/Launcher
4.1K    ./PALM/programs/DXTG
544M    ./PALM/programs/BackupMan
544M    ./PALM/programs
657K    ./PALM/Blazer/Download
661K    ./PALM/Blazer
545M    ./PALM
4.0K    ./DCIM/Palm
8.4K    ./DCIM
327K    ./Documents
545M    .

I don't notice anything funny in dmesg.

The mount settings are as follows (from /etc/mtab):

> /dev/sdd1 /media/SECOND1GB vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree 0 0

ls -al does not show any hidden trash files or anything similar (when searching, I found that was a common problem with this type of issue).


Both windows and my palm show the true free space, and I am able to write to it in both windows and in my palm.

Anyone have any ideas?

---

### Post by taurus on 2007-12-26
Did you remember to empty your trash bin?

Also, you can unmount it and mount it again and see what happens.

```
sudo umount /dev/sdd1
sudo mount -a
df -h
```

---

### Post by sciencewhiz on 2007-12-26
> **taurus said:**
> Did you remember to empty your trash bin?

Also, you can unmount it and mount it again and see what happens.

```
sudo umount /dev/sdd1
sudo mount -a
df -h
```

I don't see a trash bin in nautilus (and the file was deleted on the command line). Mounting it and remounting it does not change anything. I also get the same result when using a different card reader (with a different driver).

Thanks for the input.

---

### Post by dannyboy79 on 2007-12-26
since it's only 1GB, just copy everything to a temporary location. Reformat it with gparted, then put your stuff back on it. That should settle it. It sure sounds very weird that this is occuring. I am also curious as to why you have an fstab entry for removable media? If you want it to always mount to the same location then you should use dev rules because when you turn on your computer it'll try to mount everything in fstab (unless you have noauto option) I also see many options (usefree) that aren't even valid vfat mount options. You can read the man page for mount to find out.

Good luck

---

### Post by sciencewhiz on 2007-12-26
> **dannyboy79 said:**
> I am also curious as to why you have an fstab entry for removable media? If you want it to always mount to the same location then you should use dev rules because when you turn on your computer it'll try to mount everything in fstab (unless you have noauto option) I also see many options (usefree) that aren't even valid vfat mount options. You can read the man page for mount to find out.

Good luck

That was actually the mtab entry. It does automount normally, and does not have an entry in fstab.

---

### Post by sciencewhiz on 2007-12-26
> **dannyboy79 said:**
> since it's only 1GB, just copy everything to a temporary location. Reformat it with gparted, then put your stuff back on it. That should settle it. It sure sounds very weird that this is occuring.

Interesting...

gparted reports the space as being unallocated, but fdisk shows a fat16 partition.

---

### Post by sciencewhiz on 2007-12-26
I ran fsck and it found two errors

"There are differences between boot sector and its backup." and "Free cluster summary wrong (0 vs. really 111485)"

After fixing those, everything is fine.

It's interesting that a disk check in windows didn't find anything wrong.

---

### Post by dannyboy79 on 2007-12-26
glad it's fixed. fat16 is outdated. why don't you reformat it to vfat or fat32?

---

