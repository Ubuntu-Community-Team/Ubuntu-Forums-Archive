---
title: "Unable to mount new ext3 partition"
date: 2006-10-28
forum: General Help
---

### Post by onuca on 2006-10-28
Hi,

I have just reformatted my NTFS partition and changed it to EXT3. It has been formatted ok and I can see it under Windows XP with EXT3 driver, but I CANNOT  SEE IT IN UBUNTU!!! It simply does not mount!

I have tried to mount it from the command line but I get this output:
```

cropka@cropka-desktop:~$ sudo mount /dev/sda8
mount: can't find /dev/sda8 in /etc/fstab or /etc/mtab
```

When I check my fstab /dev/sda8 is listed, but it still seems to be NTFS formatted:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=d06dfc0b-d12b-40c5-b616-e8854db87bc5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=0024B1B024B1A8D4 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=4400389800389342 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=1494FD4294FD2740 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=4A58EB7058EB58E9 /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=A6AC3870AC383CDD /media/sda8     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda10
UUID=cca34cd4-c835-4d95-ac75-516aeb93edb4 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


```
And when I check mtab it ain't there!

```
/dev/sda9 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-10-generic/volatile tmpfs rw 0 0
/dev/sda1 /media/sda1 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/sda5 /media/sda5 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/sda6 /media/sda6 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/sda7 /media/sda7 ntfs rw,nls=utf8,umask=007,gid=46 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0


```

I have tried to add it to my mtab but it didn't help, who knows maybe I am doing smth wrong?

As I am running Edgy the disk manager doesn't exist...
I have also tried to use pysdm, but it displays only sda1 & sda10 partitions.

Anyone please help, I have wasted whole Saturday trying to resolve this :(

---

### Post by meng on 2006-10-28
Well one thing you are doing wrong is using a mount command without specifying a mountPOINT. As I understand it, your system will look for a mountpoint specified in fstab or mtab, and doesn't find one, therefore gives the error command.

Could you try:
sudo mount /dev/sda8 /media/sda8

and report what happens?

(assuming a directory /media/sda8 exists

---

### Post by onuca on 2006-10-28
I get:

```
cropka@cropka-desktop:~$ sudo mount /dev/sda8 /media/sda8
Password:
Cannot create link /etc/mtab~
Perhaps there is a stale lock file?
```

any ideas?

---

### Post by PriceChild on 2006-10-28
You need to change your fstab to tell your pc that its now a ext3 partition: [http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

Then try a```
sudo mount -a
``` and it should work fine :)

---

### Post by meng on 2006-10-28
Reboot and try again???

---

### Post by onuca on 2006-10-28
Hmmmm, wait!

It is mounted - when I go to /media/sda8 it is now located on the new EXT3 volume - great!

It only does not appear in computer:/// as a volume.

Can I do smth to add it in there?

---

### Post by onuca on 2006-10-28
Yeah - did like U and the tutorial said.

Everything works perfectly fine - yupppiee!!!!

Thanks a lot!!!  :D

---

