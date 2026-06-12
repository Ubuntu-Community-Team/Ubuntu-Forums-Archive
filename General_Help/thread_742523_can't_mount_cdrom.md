---
title: "can't mount cdrom"
date: 2008-04-01
forum: General Help
---

### Post by tubunu on 2008-04-01
For some strange reason my CDROM drive isn't detected even though that's the very drive I used when installing the system an hour ago. When I type  the mount command here's what I get:

```
sudo mount cdrom
mount: can't find cdrom in /etc/fstab or /etc/mtab

```

But my CDROM is in fstab!!!

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=9346259d-8592-4a06-8c1c-924616ff6b89 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=c2d34d6c-86fb-447f-b714-49f83917b2ab /home           ext3    defaults        0       2
# /dev/hda3
UUID=745af07e-392e-487a-8201-ca91ffbcbb98 none            swap    sw              0       0
/dev/sda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0 
```

:confused:

---

### Post by ajmorris on 2008-04-01
> **tubunu said:**
> For some strange reason my CDROM drive isn't detected even though that's the very drive I used when installing the system an hour ago. When I type  the mount command here's what I get:

```
sudo mount cdrom
mount: can't find cdrom in /etc/fstab or /etc/mtab


hi there,
the command will be:
[code]sudo mount /media/cdrom
or
sudo mount /dev/sda
```
not sudo mount cdrom


AJ

---

### Post by tubunu on 2008-04-02
```
user@user:~$ sudo mount /media/cdrom
[sudo] password for user:
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

user@user:~$ sudo mount /dev/sda
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

And the output of **dmesg | tail** is:
```
dmesg | tail
[   64.352000] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[   64.352000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[   64.352000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[   64.688000] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[   64.688000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[   64.688000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[  296.872000] UDF-fs: No partition found (1)
[  297.140000] isofs_fill_super: bread failed, dev=sda, iso_blknum=16, block=32
[  322.564000] UDF-fs: No partition found (1)
[  322.564000] isofs_fill_super: bread failed, dev=sda, iso_blknum=16, block=32
```

I don't get it... :(

---

### Post by tubunu on 2008-04-03
Turned out I plugged it in the wrong slot on the motherboard. All solved now. :)

---

