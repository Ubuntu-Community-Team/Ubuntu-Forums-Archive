---
title: "CD-ROM drive won't work"
date: 2007-12-12
forum: General Help
---

### Post by maybeway36 on 2007-12-12
My CD-ROM drive is on /dev/sdb. My system has no /dev/cdrom, and the CD drive won't work.
Here is some output:
```
$ mount /media/cdrom
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
```
$ ls /dev/s* /dev/h*
/dev/hpet   /dev/sda   /dev/sda2  /dev/sda5  /dev/sequencer   /dev/sg0  /dev/snapshot  /dev/stderr  /dev/stdout
/dev/hwrng  /dev/sda1  /dev/sda3  /dev/sdb   /dev/sequencer2  /dev/sg1  /dev/sndstat   /dev/stdin

/dev/shm:

/dev/snd:
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1c  seq  timer
```
From dmesg:
```
[ 1725.998407] UDF-fs: No partition found (1)
[ 1725.998883] isofs_fill_super: bread failed, dev=sdb, iso_blknum=16, block=32
```
And my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1deed501-4dca-476a-b124-ef86e94f4ff3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=90140fcd-71fa-4267-9368-cabac9a03611 /media/sda2     ext2    defaults        0       2
# /dev/sda5
UUID=66319664-1bc8-4f9f-9915-2b53c375c523 none            swap    sw              0       0
/dev/sdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

---

### Post by geraldm on 2007-12-13
# in the mount command, use cdrom0 where you used cdrom, to match the fstab mount-point
# try using the full mount command as root, and maybe try each filesystem type: udf, iso9660
```

mount -t iso9660 /dev/sdb /media/cdrom0

```

Gerald

---

### Post by maybeway36 on 2007-12-13
The CD drive is IDE secondary master. I'll try this mounting when I get home. I'm pretty sure the computer thinks it's a hard drive - otherwise it would be on /dev/scd0.

---

### Post by maybeway36 on 2007-12-13
Nope, both just give me the same error as before. I'll try replacing the CD-ROM drive and changing the fstab a little (sdb > scd0) and see if it works.

---

### Post by Pumalite on 2007-12-13
Check your BIOS. In some boards (chipsets), as example, Intel, is good to set as AHCI. Asus: Advanced Support For PATA+SATA.
Also, 2nd Master is good.

---

### Post by maybeway36 on 2007-12-13
I just replaced the CD drive and set the fstab entry to /dev/scd0, and now everything works. Go figure. :P

---

### Post by Pumalite on 2007-12-13
Bad drive, or cable, or connection. Go figure.

---

