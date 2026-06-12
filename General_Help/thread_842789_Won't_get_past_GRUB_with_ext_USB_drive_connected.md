---
title: "Won't get past GRUB with ext USB drive connected"
date: 2008-06-27
forum: General Help
---

### Post by dartmusic on 2008-06-27
The title pretty much says it all!  At some point (possibly the upgrade from Edgy to Gutsy -- currently running Hardy), my system stopped being able to boot with my external USB drive connected.  I have to turn the drive off in order for it to get past the "Starting up..." point.

From my searches, I have the impression that it's something pretty simple, but I can't seem to find a definitive answer.

Any ideas?

Thanks in advance!

---

### Post by mitchell19 on 2008-06-27
post your /boot/grub/menu.lst and your /etc/fstab

---

### Post by dartmusic on 2008-06-27
/boot/grub/menu.lst

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6fb8cbab-a9ff-4090-b32c-be30ed17c954 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6fb8cbab-a9ff-4090-b32c-be30ed17c954 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=6fb8cbab-a9ff-4090-b32c-be30ed17c954 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=6fb8cbab-a9ff-4090-b32c-be30ed17c954 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=6fb8cbab-a9ff-4090-b32c-be30ed17c954 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=6fb8cbab-a9ff-4090-b32c-be30ed17c954 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6fb8cbab-a9ff-4090-b32c-be30ed17c954 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6fb8cbab-a9ff-4090-b32c-be30ed17c954 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6fb8cbab-a9ff-4090-b32c-be30ed17c954 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6fb8cbab-a9ff-4090-b32c-be30ed17c954 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=6fb8cbab-a9ff-4090-b32c-be30ed17c954 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=6fb8cbab-a9ff-4090-b32c-be30ed17c954 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6fb8cbab-a9ff-4090-b32c-be30ed17c954 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=67601e80-3db1-433c-b5dd-bcbd18db1867 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

THANKS!

---

### Post by mitchell19 on 2008-06-27
There' s no external drive in your fstab, but maybe it wasn' t on at the time.

Go under Ubuntu, start your external drive. Then take a look at your /etc/fstab (you should see a new entry for your drive), and post your /etc/fstab here.

---

### Post by mitchell19 on 2008-06-27
and post /etc/mtab as well

---

### Post by dartmusic on 2008-06-27
here my mtab:

/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
securityfs /sys/kernel/security securityfs rw 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sdb1 /media/Little_Big_Boy ext3 rw 0 0
/dev/sdc1 /media/Big_Boy ext3 rw,nosuid,nodev,uhelper=hal 0 0
/dev/sde1 /media/disk ext3 rw,nosuid,nodev,uhelper=hal 0 0
tmpfs /lib/modules/2.6.24-19-generic/volatile tmpfs rw,mode=0755 0 0

The drive in question is the one called /media/disk, though I can't say that it's at sde1.  I actually can't remember how to find that out.  Also, /media/Little_Big_Boy has been having problems mounting lately: after a reboot, it has an underscore appended to the name, and I have to manually umount it and force the /dev/sdb1 to mount in the right place.  I'm not sure why the options are different for that drive than for /media/Big_Boy.  I would think they should be the same...they are both PATA drives mounted in the enclosure.

I think that because I've upgraded twice or maybe even three times, these have gotten corrupted?

Thanks again for your help.

---

### Post by dartmusic on 2008-06-27
Oh...and yes, /media/disk is currently turned on and mounted.

---

### Post by dartmusic on 2008-07-01
No other thoughts on what might be causing this?

---

