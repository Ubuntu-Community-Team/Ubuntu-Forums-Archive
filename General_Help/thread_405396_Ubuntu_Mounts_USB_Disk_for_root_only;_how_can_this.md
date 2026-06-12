---
title: "Ubuntu Mounts USB Disk for root only; how can this be changed?"
date: 2007-04-09
forum: General Help
---

### Post by cdrom600 on 2007-04-09
I have a USB disk that I recently formatted in Ubuntu to the ext3 filesystem.  Whenever I plug it in, Ubuntu automounts it and its icon appears on the Gnome desktop (with the name usbdisk).  However, only root has permission to write to it.  Obviously, this isn't very useful to me.  *How can I make it so that I have full access to USB disks which are automatically mounted?*

It's worth noting that I followed [this guide]("http://ubuntuforums.org/showthread.php?t=217009") to allow me to fully access and write to NTFS-formatted external drives.  Might this have something to do with my current issue?

Other possibly useful information:
I'm using Ubuntu Edgy (6.10)
uname -r:
```
2.6.17-10-generic
```
dmesg | tail (after plugging in the drive):
```
[17181355.268000] sdb: assuming drive cache: write through
[17181355.268000] SCSI device sdb: 39070080 512-byte hdwr sectors (20004 MB)
[17181355.272000] sdb: test WP failed, assume Write Enabled
[17181355.272000] sdb: assuming drive cache: write through
[17181355.272000]  sdb: sdb1
[17181355.368000] sd 11:0:0:0: Attached scsi disk sdb
[17181355.368000] sd 11:0:0:0: Attached scsi generic sg1 type 0
[17181355.604000] kjournald starting.  Commit interval 5 seconds
[17181355.616000] EXT3 FS on sdb1, internal journal
[17181355.616000] EXT3-fs: mounted filesystem with ordered data mode.
```
mount (after plugging in the drive):
```
/dev/sda4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
/dev/hdb1 on /home/cdzombak/Documents type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda1 on /media/winsys type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/usbdisk type ext3 (rw,nosuid,nodev)
```

---

### Post by bettlebrox on 2007-04-09
Add yourself to the plugdev group

---

### Post by lionel47 on 2007-04-10
> **bettlebrox said:**
> Add yourself to the plugdev group

OK, so how does one do this through CLI?  I don't see such a group under Users & Groups.  Thanks. :(

---

### Post by Austin_KW on 2007-04-10
You can edit the /etc/group file

or the GUI is trying to be clever, select the user, properties, privileges and it is called something like access external devices 

Remember you need a new login to get the new rights

---

### Post by bettlebrox on 2007-04-11
> **Austin_KW said:**
> You can edit the /etc/group file

or the GUI is trying to be clever, select the user, properties, privileges and it is called something like access external devices 

Remember you need a new login to get the new rights
Unless U know what your doing I would recommend not editing the /etc/group file by hand. If you make a mistake you could break your system. Usermod should do the trick. But, are you already a member of the plugdev group? The command "id" will show what groups your a member of. If your not a member of the plugdev group, use the usermod command like so:

sudo usermod -G plugdev [plus all the other groups your a member of] USERID

Then logout and login.

---

### Post by cdrom600 on 2007-04-11
> **Austin_KW said:**
> or the GUI is trying to be clever, select the user, properties, privileges and it is called something like access external devices 

Remember you need a new login to get the new rights
This works - thank you!

---

### Post by EarlGrey on 2008-04-15
Hello, I have the exact same problem, but I am a member of plugdev group and still it does not work.
 Do you please have any suggetsions?

Thank you very much.

---

