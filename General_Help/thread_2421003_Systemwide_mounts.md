---
title: "Systemwide mounts"
date: 2019-06-14
forum: General Help
---

### Post by caterhamfan on 2019-06-14
Dropbox keeps asking me to relink on reboot the same as this post - [https://ubuntuforums.org/showthread.php?t=2111361&p=12515286#post12515286](https://ubuntuforums.org/showthread.php?t=2111361&p=12515286#post12515286)

The systemwide mounts option seems to be the solution - [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

**pysdm **doesn't exist anymore.

These two options, I do not know what to do in Ubuntu 19.04: 


[LIST=1]
[*]The first method is manually editing Ubuntu's filesystem table. This sounds more complex than it really is. 
[/LIST]
     2. The second method, for versions 6.06 and later, is described at [MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions"). 


I am unsure how to do this to stop this issue upon reboot. If someone can provide the steps I'd be eternally grateful.

Thank you,

---

### Post by TheFu on 2019-06-14
I don't use dropbox, but if all you need it help with the fstab to mount a local, permanently connected disk, please ask a specific question or answer these questions:

* What file system type do you want to mount?  ext4 is the most common. ZFS, XFS are the next most common. NTFS is possible, but the mount options get ugly.

* What is the UUID for the partition where that file system is?  **blkid** is the program to get that.

* What is the "mount point" - i.e. the empty directory where you want it?  It can be almost anywhere, but shouldn't be where Linux thinks the OS is or in your HOME. Many people like to use a separate partition for all HOME directories. If that is desired, then only Linux file systems can be used, not NTFS, not FAT32 or exFAT.  The "mount point" directory, must exist.  Usually, you should create it, then manually mount the partition there and lastly, change the ownership and permissions to be what you need.

* If you choose to use LVM during the install, then we need slightly different information, though the UUID can still be used.

If the storage is a new disk, there is some pre-mount work needed.
a) it should be partitioned.  At least 1 partition is required. Sometimes more are handy.
b) the partition you want to mount must have a compatible filesystem created on it.  The **mkfs** command does that. If you don't have a specific reason to choose a specific file system, then use ext4.
c) If you want to use more advanced file systems, the creation of the file system changes, but the mount changes only with the "type" - file system type on the mount line.

There are no GUI tools to edit the fstab file.  Use the system-file editor, sudoedit.
The format used by the ftab hasn't changed in decades, so almost any guide you find is good enough.  The only real issue comes when picking 

Each line is a different mount. Don't touch any existing lines.
Comments begin with a # on the line.  For format and example is:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation - 
UUID=df8c97db-e552-4117-a088-7e4309e37e92 /  ext4  noatime,errors=remount-ro    0     1
```
the same result would be caused from:
```
 /dev/sda1    /  ext4  noatime,errors=remount-ro     0     1
```
This shows the UUID (or partition device), mount point, ext4 file system, typical options, and the last 2 fields are for backups and file system checking.  At least 1 space is required between the different parts. No spaces are allowed inside the different ports. Space is the delimiter.  All items are case sensitive.

Remember, the UUID to use is unique for every partition. The **blkid** command shows the UUID to device mapping.

---

