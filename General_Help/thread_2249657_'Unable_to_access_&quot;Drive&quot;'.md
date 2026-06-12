---
title: "'Unable to access &quot;Drive&quot;'"
date: 2014-10-23
forum: General Help
---

### Post by jmmrly on 2014-10-23
I am dual booting ubuntu and windows 8.1 on my ssd. I also have a secondary 500gb drive which i use for storage. It can easily see and access the windows partition of the ssd, but it gets a permission error when trying to access the secondary drive. When running 'sudo ntfsfix /dev/sda2' in terminal, i get the error that windows is hibernated and that it refused to mount the secondary drive. I have already tried disabling fast boot etc. But i don't think this is affecting it as i can access the windows partition, just not this secondary drive which has no os installed on it but i need to access it from ubuntu for data storage.
Help would be appreciated.

---

### Post by oldfred on 2014-10-23
Post this from terminal in Ubuntu:

sudo parted -l
mount

---

### Post by jmmrly on 2014-10-24
```

james@james-ubuntu:~$ sudo parted -l
Model: ATA WDC WD5000LPVX-1 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1076MB  2150MB  1074MB  fat32        CO    boot
 2      2286MB  500GB   498GB   ntfs               msftdata


Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  368MB   367MB   primary  ntfs         boot
 2      368MB   97.9GB  97.5GB  primary  ntfs
 3      97.9GB  112GB   14.0GB  primary  ext4
 4      112GB   120GB   8118MB  primary  ext4


james@james-ubuntu:~$ mount
/dev/sdb3 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sdb4 on /home type ext4 (rw)
/dev/sda1 on /boot/efi type vfat (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=james)


```

---

### Post by /ADM on 2014-10-24
Your secondary drive is formatted in NTFS which Linux cannot read correctly.  Permissions do not work with NTFS, you would need to reformat the drive (after backing up all data) to a native format (ext3 or 4) and then put your data back on it.

---

### Post by jmmrly on 2014-10-24
> **/ADM said:**
> Your secondary drive is formatted in NTFS which Linux cannot read correctly.  Permissions do not work with NTFS, you would need to reformat the drive (after backing up all data) to a native format (ext3 or 4) and then put your data back on it.

It's odd that my primary SSD is also formatted in NTFS but can be read in Linux. If i re-format it inside windows, what do i need to format it to so that both windows and Linux can read it?

---

### Post by oldfred on 2014-10-24
The Linux NTFS driver should be able to read any NTFS formatted partition.

But if you have resized or it has interal issues and then needs chkdsk, the NTFS driver will not let you use it to prevent further damage that a chkdsk may not then be able to fix.
I would run chkdsk on that partition from Windows.

Also if Windows was hibernated and that partition was included in Windows mount, then the NTFS driver will not mount the NTFS partition. Make sure hibernation is off. If Windows 8 hibernation is always on, as it uses a fast boot quick hibernation as a default.

---

### Post by jmmrly on 2014-10-24
Re-formatting the drive did the trick. Thanks guys.

---

