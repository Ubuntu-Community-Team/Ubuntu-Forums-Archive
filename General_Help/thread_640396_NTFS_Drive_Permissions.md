---
title: "NTFS Drive Permissions"
date: 2007-12-14
forum: General Help
---

### Post by d4rkpri35t on 2007-12-14
Hello,
 I have Ubuntu 7.04 and I was wondering how to change read, write, and edit privliges on a file formatted with ntfs. I can't format the drive because it's used as storage for Windows and Ubuntu and has alot of space used.

I looked through the threads and the closest thing I found was a link for [MountingWindowsPartitions/ThirdPartyNTFS3G]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G")

I installed the ntfs-config but when I go to access it, the file only allowed me to change permissions to an external drive not for internal drives. 

Any help would be greatly appreciated. Thanks

---

### Post by PmDematagoda on 2007-12-14
I'm sorry but there should be a checkbox in ntfs-config to enable you to read and write to internal volumes, just check it again.

---

### Post by d4rkpri35t on 2007-12-14
> **PmDematagoda said:**
> I'm sorry but there should be a checkbox in ntfs-config to enable you to read and write to internal volumes, just check it again.

Please look at this [screenshot]("http://www.fullcaliber.be/images/ntfsconfig.png")

---

### Post by PmDematagoda on 2007-12-14
That is rather strange. Could you please post the results of:-
```

cat /etc/mtab
```

and:-

```
sudo fdisk -l
```

---

### Post by d4rkpri35t on 2007-12-14
```
shelbz@shelbz-desktop:~$ cat /etc/mtab
/dev/sdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-15-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
tmpfs /lib/modules/2.6.20-16-generic/volatile tmpfs rw,mode=0755 0 0
/dev/sda5 /media/Storage ntfs rw,nosuid,nodev,umask=222,utf8 0 0
/dev/sda1 /media/Windows ntfs rw,nosuid,nodev,umask=222,utf8 0 0

```

```
shelbz@shelbz-desktop:~$ sudo fdisk -1
Password:
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

```

BTW..  I'm not sure if this matters but this is a Secondary hard drive. It's not the drive Ubuntu is installed on.

---

### Post by PmDematagoda on 2007-12-14
In sudo fdisk -l, l is simple L not the number 1.

---

