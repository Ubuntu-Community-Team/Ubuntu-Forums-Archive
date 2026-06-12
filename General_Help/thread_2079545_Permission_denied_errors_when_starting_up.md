---
title: "Permission denied errors when starting up"
date: 2012-11-02
forum: General Help
---

### Post by Predictability on 2012-11-02
When I try to start my computer I get the following errors:

```
Unlcoking the disk /dev/disk/by-uuid/6e270a39-52ff-4db3-9676-41feae30037 (sda5_crypt)
Enter passphrase:
cryptsetup: sda5_crypt set up successfully
fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
/dev/sda1: clean, 251/124496 files, 168770/248832 blocks
/dev/mapper/sda5_crypt: clean, 236020/45776896 files, 24057030/183080192 blocks
udev[895]: failed to execute '/sbin/modprobe' '/sbin/modprobe -bv input:b0019v0000p0000ee0000-e0,3,kra0,1,2,mlsfw': Permission denied

mountall: mount / [896]: Permission denied
udevd[895]: failed to execute '/lib/udev/accelerometer' 'accelerometer /devices/platform/lis31vo2d/input/inputt12/js0': Permission denied

udevd[898]: failed to execute '/lib/udev/accelerometer' 'accelerometer /devices/platform/lis31vo2d/input/input12/event12': Permission denied

udevd[904]: failed to execute '/lib/udev/udisks-part-id' 'udisks-part-id /dev/sda1': Permission denied

[  24.576881] Bad LUN (0:1)
[  24.577017] Bad target number (1:0)
[  24.577181] Bad target number (2:0)
[  24.577311] Bad target number (3:0)
[  24.577440] Bad target number (4:0)
[  24.577570] Bad target number (5:0)
[  24.577688] Bad target number (6:0)
[  24.577728] Bad target number (7:0
udevd[906]: failed to execute '/lib/udev/scsi_id' 'scsi_id --export --whitelisted -d /dev/sdb': Permission denied

udevd[907]: failed to execute '/sbin/blkid' '/sbin/blkid -o udev -p /dev/sdb': Permission denied

udevd[908]: failed to execute '/lib/udev/udisks-part-id' 'udisks-part-i /dev/sbd': Permission denied

udevd[909]: failed to execute '/lib/udev/hdparm' '/lib/udeb/hdparm': Permission denied

udevd[910]: failed to execute '/lib/udev/scsi_id' 'scsi_id --export --whitelisted -d /dev/sdb': Permission denied

udevd[911]: failed to execute '/sbin/blkid' '/sbin/blkid -o udev -p /dev/sdb': Permission denied

udevd[9012]: failed to execute '/lib/udev/udisks-part-id' 'udisks-part-i /dev/sbd': Permission denied
```

From here it just hangs.  Is there any way to fix this without reinstalling?

---

### Post by Predictability on 2012-11-08
bump

---

### Post by Predictability on 2012-11-17
bump

---

### Post by Lightstar on 2012-11-17
Doh, that doesn't look good.

Happened to me once when my whole system's permission had changed.
After I had fixed the few files I was able to catch on that log, a dozen more appeared..

I imagine you'll have to fix this by booting up a Live CD, whether you decide to reinstall everything or try fixing permissions.

Sorry I don't have a solution (I chose to reinstall).
I'm going to follow the thread, I'd like to know if there's good tricks to fix this problem.

---

### Post by Predictability on 2012-11-23
bump

---

### Post by Predictability on 2012-11-25
I went into recovery mode to try to change permissions with visudo, but I get these errors when I run visudo:
```
visudo: /etc/sudoers: Read-only file system
visudo: /etc/sudoers: Read-only file system
```

---

### Post by pikpik on 2013-02-02
Hello.

I just ran into quite the same problem as you did.
Did you have any chance to fix it?

I used a disk manager utility from synaptics which probably screwed up my boot files.

After checking disks, here are the last messages:
> mountall: mount / [852] : Permission denied

udevd[859]: failed to execute '/sbin/blkid' '/sbin/blkid -o udev -p /dev/sdb': Permission denied
udevd[860]: failed to execute '/lib/udev/udisks-part-id' 'udisks-part-id /dev/sdb': Permission denied

Thanks,

Pikpik

---

### Post by rnerwein on 2013-02-02
> **Predictability said:**
> I went into recovery mode to try to change permissions with visudo, but I get these errors when I run visudo:
```
visudo: /etc/sudoers: Read-only file system
visudo: /etc/sudoers: Read-only file system
```
hi
you have to mount your orginal root-fs with: mount -o rw ......
and then please give us an output of: ls -l /etc/sudoers /etc/passwd and /etc/shadow !!!!
ciao

---

