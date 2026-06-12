---
title: "How to automount a extern USB ntfs drive in read/write mode?"
date: 2007-07-28
forum: General Help
---

### Post by Archmage on 2007-07-28
I just bought a usb extern USB harddrive (Teca 80GB HD-15 PUK-A-80) and want to use it.

At the moment it is formated in NTFS - that is exactly I want it to be, so that I can use the files also on a Windows PC.

Unfortunately my Ubuntu Feisty is mounting this in read-only mode, when I plug the drive in, although I want to write on the drive, too.

Is there any way that it will be automatical mounted in read/write mode? (I think mounting it with ntf-g3 would do the trick, but I don't know where I could change the setting for this drive so that it will do this automatical.)

Here is what is coming when I type *mount* in the comandoline.

```
mount
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hdb2 on /homeo type xfs (rw)
/dev/disk/by-uuid/24407ED9407EB162 on /windows type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/Volume type ntfs (rw,nosuid,nodev,umask=222,utf8)
```

---

### Post by logos34 on 2007-07-28
Get ntfs-config:

sudo apt-get install ntfs-config

Then start it up and enable write support on **external** device (your internal mounting at /windows is already mounting read-write ('fuseblk')

---

