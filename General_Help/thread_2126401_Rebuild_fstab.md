---
title: "Rebuild fstab"
date: 2013-03-17
forum: General Help
---

### Post by Paleskin on 2013-03-17
Everytime I boot into ubuntu, on my triple boot OS, I always being greeted by the message

"ignore, skip mount partition or manual recovery"

I tried the option auto,nofail,nobootwait in the fstab, but still being greeted by this message at the boot sequence, I had to press I then S just to get into ubuntu

So I tried to rebuild my fstab, but I dunno how

This is my current setup

```
sudo blkid

/dev/loop0: UUID="7d6d1c1d-a213-485a-bbe7-d7e169df941e" TYPE="ext3" 
/dev/sda1: UUID="fd2dba10-a6b3-4e9c-84e7-ec427ea66f6a" TYPE="ext4" 
/dev/sda2: LABEL="System Reserved" UUID="B89E10EC9E10A4C2" TYPE="ntfs" 
/dev/sda3: UUID="C4FA1255FA124458" TYPE="ntfs" 
/dev/sda4: UUID="1311BEBB7EA19549" TYPE="ntfs" 
/dev/sdb1: UUID="F2026B9C026B6517" TYPE="ntfs" 
/dev/sdb2: LABEL="Backuped" UUID="D623-5F19" TYPE="exfat" 
```


```
cat /etc/mtab
/dev/sda1 / ext4 rw 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sdb2 /media/sdb2 fuseblk rw,noexec,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda2 /media/sda2 fuseblk ro,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sda3 /media/sda3 fuseblk ro,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sda4 /media/sda4 fuseblk ro,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sdb1 /media/sdb1 fuseblk ro,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/loop0 /var/spool/havp ext3 rw,mand 0 0
cgroup /dev/cgroup/cpu cgroup rw,cpu 0 0
gvfs-fuse-daemon /home/forest/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=forest 0 0

```


Can somebody help me ?




Thanks

---

### Post by coffeecat on 2013-03-17
You need to post the contents if /etc/fstab for someone to help you. All the partitions listed in your blkid output are represented in your /etc/mtab output so we need to see /etc/fstab to see why you are getting that message.

Also - you lose whitespace if you use quote tags. Terminal output and contents of config files need to go in code tags in order to preserve formatting. I've replaced your quote tags with code tags, although it doesn't make that much difference with those two outputs, but it will be important with /etc/fstab.

---

