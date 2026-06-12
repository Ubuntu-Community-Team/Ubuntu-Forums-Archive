---
title: "flush disk"
date: 2019-11-23
forum: General Help
---

### Post by bjlockie on 2019-11-23
I have a script that mounts and unmounts:
/dev/sdc1 on /media/me/USB_backup

I was getting /dev/sdc1 on /media/me/USB_backup mounted automatically until I manually created /media/me/USB_backup.
Now I automatically get:
/dev/sdc1 on /media/me/USB_backup1 type ext2 (rw,nosuid,nodev,relatime,uhelper=udisks2)

I forced the mount/unmount because I read that force the writing of the buffers out.

My question is if I unmount /media/me/USB_backup but /media/me/USB_backup1 is still mounted will it still flush the buffers?

---

### Post by TheFu on 2019-11-23
sync is the normal way to flush buffers. Manually typing it 3 times is an old sysadmin trick because by the time you do that, the first sync should have actually flushed everything to disk.  This only works for file systems that don't do some sort of double-buffering, so SAN devices and probably ZFS are exempt, is my guess.  Also, devices with hardware caching would have received the data, but not necessarily written it to the physical storage.

The things we setup to get better performance.

BTW, mounting by using the direct device name is dangerous.  Always best to use the UUID, LABEL, or a specific by-path/ link.  Look under /dev/disks/by-* for some other options.   A few weeks ago, I wiped out my /boot partition using an NTFS format script that assumed a specific device.  I had left a USB stick plugged in at the prior reboot a few weeks earlier, so at the next reboot, all the device order was different and device names had changed.
Be very careful assuming /dev/sdc1 is really the partition you want.

```
$ lsblk -o name,size,type,fstype,mountpoint
```

would be helpful.

---

### Post by bjlockie on 2019-11-23
mount shows:
/dev/sdc1 on /media/me/USB_backup1 type ext2 (rw,nosuid,nodev,relatime,uhelper=udisks2)
/dev/sda1 on /media/me/seagate_backup1 type ext4 (rw,nosuid,nodev,relatime,uhelper=udisks2)

$ blkid /dev/sdc1
$ blkid /dev/sda1
/dev/sda1: LABEL="seagate_backup" UUID="d76b927c-4d1d-4a5b-bdcb-9498d3a14669" TYPE="ext4" PARTUUID="2c6b7aeb-01"

Why doesn't blkid work for my USB flash drive but it works for my USB hard drive?

---

### Post by Impavidus on 2019-11-24
**sync** will flush the buffers, by default all of them, but you can be specific. **umount** will flush the buffers for the device to be unmounted, then unmount it.

/media/username/label/ is where devices get mounted automatically. It's best to avoid it when mounting manually. As you had manually created /media/me/USB_backup, the file manager mounting the device automatically could no longer use that and created /media/me/USB_backup1 instead.

---

