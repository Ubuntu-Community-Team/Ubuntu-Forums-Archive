---
title: "Keep on mounting..."
date: 2008-06-14
forum: General Help
---

### Post by codeking on 2008-06-14
Every time I restart my computer, all the partitions on my hard drive (excluding filesystem) will have to be mounted again.  Why is it doing this, and can I stop it?

---

### Post by ChameleonDave on 2008-06-14
> **codeking said:**
> Every time I restart my computer, all the partitions on my hard drive (excluding filesystem) will have to be mounted again.  Why is it doing this, and can I stop it?

Normally, all filesystems listed in /etc/fstab are mounted at boot time.  Is this not happening?

---

### Post by codeking on 2008-06-14
Yep.  I have to manually mount them at each start up in order to use them.

---

### Post by geo909 on 2008-06-14
Try PYSDM (PYthon Storage Device Manager). You  will find it in synaptic.
It's a graphical tool that helps you handle easily your storage devices  like hard disks.
You just tick boxes and it actually adds lines in your fstab file.
You will also find automounting options, I guess that will do the job.

---

### Post by ChameleonDave on 2008-06-14
> **codeking said:**
> Yep.  I have to manually mount them at each start up in order to use them.
Paste the output of these commands here:

```
cat /etc/fstab
ls -l /dev/disk/*
```

---

### Post by codeking on 2008-06-14
```
theron@theron:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=7b8f7bd8-16d3-44bc-9f09-057c0a2d0afa /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
theron@theron:~$ ls -l /deb/disk/*
ls: cannot access /deb/disk/*: No such file or directory
theron@theron:~$ ls -l /dev/disk/*
/dev/disk/by-id:
total 0
lrwxrwxrwx 1 root root  9 2008-06-14 15:06 ata-WDC_WD2000JD-22HBB0_WD-WMAL81262348 -> ../../sda
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 ata-WDC_WD2000JD-22HBB0_WD-WMAL81262348-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 ata-WDC_WD2000JD-22HBB0_WD-WMAL81262348-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 ata-WDC_WD2000JD-22HBB0_WD-WMAL81262348-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 ata-WDC_WD2000JD-22HBB0_WD-WMAL81262348-part4 -> ../../sda4
lrwxrwxrwx 1 root root  9 2008-06-14 15:06 scsi-1ATA_WDC_WD2000JD-22HBB0_WD-WMAL81262348 -> ../../sda
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 scsi-1ATA_WDC_WD2000JD-22HBB0_WD-WMAL81262348-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 scsi-1ATA_WDC_WD2000JD-22HBB0_WD-WMAL81262348-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 scsi-1ATA_WDC_WD2000JD-22HBB0_WD-WMAL81262348-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 scsi-1ATA_WDC_WD2000JD-22HBB0_WD-WMAL81262348-part4 -> ../../sda4
lrwxrwxrwx 1 root root  9 2008-06-14 20:06 usb-eM_Bay_Reader_9203111-0:0 -> ../../sdb
lrwxrwxrwx 1 root root  9 2008-06-14 20:06 usb-eM_Bay_Reader_9203111-0:1 -> ../../sdc
lrwxrwxrwx 1 root root  9 2008-06-14 20:06 usb-eM_Bay_Reader_9203111-0:2 -> ../../sdd
lrwxrwxrwx 1 root root  9 2008-06-14 20:06 usb-eM_Bay_Reader_9203111-0:3 -> ../../sde

/dev/disk/by-label:
total 0
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 RESTORE -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 Shared -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 Windows -> ../../sda1

/dev/disk/by-path:
total 0
lrwxrwxrwx 1 root root  9 2008-06-14 20:06 pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:0 -> ../../sdb
lrwxrwxrwx 1 root root  9 2008-06-14 20:06 pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:1 -> ../../sdc
lrwxrwxrwx 1 root root  9 2008-06-14 20:06 pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:2 -> ../../sdd
lrwxrwxrwx 1 root root  9 2008-06-14 20:06 pci-0000:00:1d.3-usb-0:1:1.0-scsi-0:0:0:3 -> ../../sde
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 pci-0000:00:1f.1-scsi-0:0:0:0 -> ../../scd0
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 pci-0000:00:1f.1-scsi-0:0:1:0 -> ../../scd1
lrwxrwxrwx 1 root root  9 2008-06-14 15:06 pci-0000:00:1f.2-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 pci-0000:00:1f.2-scsi-0:0:0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 pci-0000:00:1f.2-scsi-0:0:0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 pci-0000:00:1f.2-scsi-0:0:0:0-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 pci-0000:00:1f.2-scsi-0:0:0:0-part4 -> ../../sda4

/dev/disk/by-uuid:
total 0
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 3A4858A653265941 -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 423B-2BDF -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 5488A94988A92A86 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-06-14 15:06 7b8f7bd8-16d3-44bc-9f09-057c0a2d0afa -> ../../sda3
theron@theron:~$ 

```

---

### Post by ChameleonDave on 2008-06-14
Only your root partition is mentioned in /etc/fstab, so it's normal that nothing else is mounted.

You will need to add a line starting with "LABEL=Shared" in order to mount your shared partition with your stuff on it.  I don't know what to put on the rest of the line because I don't know what sort of filesystem it is.  Please post the output of this:

```

sudo fdisk -l

```

---

### Post by codeking on 2008-06-14
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcba1b13a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         549       13338   102735675    7  HPFS/NTFS
/dev/sda2               1         548     4401778+   b  W95 FAT32
/dev/sda3           13339       17182    30876930   83  Linux
/dev/sda4           17183       24321    57344017+   7  HPFS/NTFS

Partition table entries are not in disk order
```

---

### Post by ChameleonDave on 2008-06-14
Open up fstab by typing the following:

```

sudo *nano* /etc/fstab

```

You may replace *nano* with *gedit*, *kwrite*, *kate*, *mousepad*, *vim*, *emacs*, or whatever your favourite text editor is.

Insert a line to mount your shared partition.  Put it before the ones about the CD drives.  Your file will end up looking something like this:

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0


# Ubuntu root partition.
# This could be referred to as /dev/sda3 instead of the UUID.
UUID=7b8f7bd8-16d3-44bc-9f09-057c0a2d0afa  /  ext3  relatime,errors=remount-ro  0  1


# Shared partition with personal stuff on.
# This could be referred to as /dev/sda4,
# or by UUID=3A4858A653265941, instead of by the label.
LABEL=Shared  vfat  defaults,auto,umask=007  0  2


#Optical drives
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0


```

The stuff after hash signs ("#") is commentary.  It helps to explain what things mean.  They are not read by the system.

We could also add a line to automount your recovery partition and your Windows partition, but I would advise you to leave these not mounted by default.

---

### Post by Victormd on 2008-06-14
> **codeking said:**
> Yep.  I have to manually mount them at each start up in order to use them.

Check out the [how to on my signature to automount your drives]("http://ubuntuforums.org/showthread.php?t=802699") when ubuntu starts...

---

### Post by ChameleonDave on 2008-06-14
> **Victormd said:**
> Check out the [how to on my signature to automount your drives]("http://ubuntuforums.org/showthread.php?t=802699") when ubuntu starts...

But that's for NTFS.  His drive is FAT.

---

### Post by codeking on 2008-06-14
@ChameleonDave:  That's the recovery drive, which I don't really care about.  Both the Shared and the Windows drives (the ones I want to mount) are NTFS

Solved.  Thanks Victormd and ChameleonDave!

---

### Post by Victormd on 2008-06-14
He also has 2 NTFS partitions (sda1 and sda4)... :)
For the FAT partition, simply change the NTFS term for FAT (applied to sda2)

---

### Post by ChameleonDave on 2008-06-14
Ah yes, sorry.  I mixed up sda2 and sda4.  But it seems you have been able to take what I advised and modify it to make it work for NTFS.  Glad that it worked out for you.

Change the title of your original post so that it says "[SOLVED]...".

---

