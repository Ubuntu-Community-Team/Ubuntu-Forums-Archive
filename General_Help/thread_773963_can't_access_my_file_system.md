---
title: "can't access my file system"
date: 2008-04-29
forum: General Help
---

### Post by alantony on 2008-04-29
Ubuntu 7.10 on /dev/hda2
Intel P4 1.5GHz
RAM 1G

I was attempting to mount a drive and now

I am having a hard time moving my files around in my file system. 
I am getting a lot of "file is read-only" errors.  Also, I can't create any files with vi.

here is the output of #more /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=7ada29a5-0b0a-4811-957d-8276c3c6401f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=7c8ee388-b611-4cdd-a0dd-75bc9406a7aa none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

I believe that there is a mount error. If you can help me regain my file system I would be very grateful.
aka

---

### Post by ryanhaigh on 2008-04-29
The output of the command dmesg should give you an indication as to what is going on but it sounds like the ext3 partition may be corrupted.

```

dmesg
#or use this for info regarding hda2 specifically
dmesg | grep hda2

```

---

### Post by alantony on 2008-04-29
the system was humming like a charm. it is possible that I messed it up with the mount command.
thanks

---

### Post by alantony on 2008-04-29
Hi,
I have entered the command the the output is posted.

#dmesg | grep hda2

```


[    8.450000]  hda: hda1 hda2 hda3 < hda5 >
[   12.640000] EXT3-fs: hda2: orphan cleanup on readonly fs
[   12.640000] EXT3-fs: hda2: 6 orphan inodes deleted
[   22.830000] EXT3 FS on hda2, internal journal
[436447.220000] hda2: rw=0, want=17179869192, limit=426798855
[436447.220000] EXT3-fs error (device hda2): ext3_free_branches: Read failure, inode=14583126, block=2147483648
[436447.220000] Aborting journal on device hda2.
[436447.220000] EXT3-fs error (device hda2) in ext3_reserve_inode_write: Journal has aborted
[436447.220000] EXT3-fs error (device hda2) in ext3_truncate: Journal has aborted
[436447.220000] EXT3-fs error (device hda2) in ext3_reserve_inode_write: Journal has aborted
[436447.220000] EXT3-fs error (device hda2) in ext3_orphan_del: Journal has aborted
[436447.220000] EXT3-fs error (device hda2) in ext3_reserve_inode_write: Journal has aborted


```

---

### Post by ryanhaigh on 2008-04-29
Perhaps run a filesystem check on the drive, open system>help and support and enter man fsck for info on how to run the check, there may also be info online about this.

I would also google for these specific messages
> 
ext3_reserve_inode_write: Journal has aborted
ext3_truncate: Journal has aborted
 etc. 
Also check the connections to the drive and maybe run diagnostics from the manufacturers website to ensure you don't have a bad drive.

---

