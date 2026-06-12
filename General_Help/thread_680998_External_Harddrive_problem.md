---
title: "External Harddrive problem"
date: 2008-01-28
forum: General Help
---

### Post by hlmijendrix on 2008-01-28
I'm using a WD My Book ext hd with my acer laptop running gutsy. After a while of using it (I have all my music saved on the ext hd)..The music icons change to a blank page icon when you click on it and it doesn't play. It does this to my entire 50gb of music files...when I exit out of the hd folder and reopen it...it says not all the contents could be displayed.  Whats the deal?

---

### Post by taurus on 2008-01-28
Is it ntfs filesystem?  How would you normally mount it?

Post

```
sudo fdisk -l
mount
```

---

### Post by hlmijendrix on 2008-01-28
```
david@david-laptop:~$ sudo fdisk -l
[sudo] password for david:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce137229

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536   83  Linux
/dev/sda2            6080        7296     9775552+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    c  W95 FAT32 (LBA)
david@david-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/My Book type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)

```

---

### Post by taurus on 2008-01-28
Make sure nothing is accessing /media/My Book.  Then run

```
sudo umount /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
ls -la /media/sdb1
```
Now, all your stuff on /dev/sdb1 is in /media/sdb1.

---

### Post by hlmijendrix on 2008-01-28
It still says "Sorry, couldn't display all the contents of "sdb1". after I try to access the hd

Heres the results of the commands

```
david@david-laptop:~$ sudo umount /dev/sdb1
[sudo] password for david:
david@david-laptop:~$ sudo mkdir /media/sdb1
david@david-laptop:~$ sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
david@david-laptop:~$ ls -la /media/sdb1
total 228
drwxrwxrwx  7 root root 32768 1969-12-31 17:00 .
drwxr-xr-x  4 root root  4096 2008-01-28 15:25 ..
dr-xr-xr-x  2 root root 32768 2003-05-02 15:47 autorun
-r-xr-xr-x  1 root root    36 2002-10-17 09:56 autorun.inf
dr-xr-xr-x 11 root root 32768 2008-01-25 12:43 David's Music
drwxrwxrwx  2 root root 32768 2008-01-25 14:52 Recycled
drwxrwxrwx  3 root root 32768 2008-01-25 12:43 System Volume Information
drwxrwxrwx  3 root root 32768 2008-01-26 15:41 .Trash-david

```

---

### Post by gyrfalcon on 2008-01-28
Have you tried plugging it into a windows machine and doing a "chkdsk /f /x /r <driveletter>"?  I'm not great with Linux, but have noticed some weird things between Windows & Linux...especially with NTFS.

Also, do you happen to be using a 64bit distro?

Edit: When I mentioned NTFS, I knew you were using FAT32 in this instance.

---

### Post by hlmijendrix on 2008-01-28
I have the i386 bit distro of ubuntu 7.10

---

