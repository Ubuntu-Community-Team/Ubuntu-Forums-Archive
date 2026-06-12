---
title: "fstab question"
date: 2006-10-31
forum: General Help
---

### Post by jordilin on 2006-10-31
I have just installed Edgy and when looking at my fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
**UUID=d04e1b0c-6295-4f47-b6ec-fec3c4b5b813** /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=5a96becc-c287-4d72-8db0-eb345c743851 /boot           ext3    defaults        0       2
# /dev/hda3
UUID=85f7a16d-a311-4ed8-bb82-c9f95fca93d5 /home           ext3    defaults        0       2
# /dev/hda4
UUID=e8268977-f6bd-41fd-8aa5-669e0d3e275c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


What's the meaning of these UUID, Do you have the same?

---

### Post by yota on 2006-10-31
Hi, from 'man fstab'

[INDENT]Instead of giving the device explicitly, one may indicate the (ext2  or
       xfs)  filesystem that is to be mounted by its UUID or volume label (cf.
       e2label(8) or  xfs_admin(8)),  writing  LABEL=<label>  or  UUID=<uuid>,
       e.g.,   ‘LABEL=Boot’   or  ‘UUID=3e6be9de-8139-11d1-9106-a43f08d823a6’.
       This will make the system more robust: adding or removing a  SCSI  disk
       changes the disk device name but not the filesystem volume label.

[/INDENT]
UUIDs are unique identifiers that can be set with 'tune2fs -U' and checked with 'tune2fs -l'
[INDENT]
yota@one:/etc$ sudo tune2fs -l /dev/md0
tune2fs 1.39 (29-May-2006)
Filesystem volume name:   root
Last mounted on:          <not available>
Filesystem UUID:          8a877a6d-a933-4560-8602-5ccc36ded4c1
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
...
[/INDENT]

---

### Post by jordilin on 2006-10-31
Thanks, then I understand there's nothing wrong with my system and that this was predefined by my Edgy clean install, is that right?

---

### Post by yota on 2006-10-31
Exactly, in edgy the default switched to the more robust UUIDs filesystems identifications, it's absolutely normal and anyway it's just an 'option': the old way with explicit device reference still works, if you like it more.

Anyway i think that the "if it isn't broken, don't fix it" applies! ;)

---

### Post by jordilin on 2006-10-31
> **yota said:**
> Exactly, in edgy the default switched to the more robust UUIDs filesystems identifications, it's absolutely normal and anyway it's just an 'option': the old way with explicit device reference still works, if you like it more.

Anyway i think that the "if it isn't broken, don't fix it" applies! ;)

thanks, indeed.

---

