---
title: "ntfs making movies choppy?"
date: 2008-05-10
forum: General Help
---

### Post by oddworld on 2008-05-10
I have a few movies on my NTFS hard drive, and when I play them the audio is choppy every minute or so.
If I copy the movie to EXT3 linux drive then the playback is fine.
Is there any way to correct this without reformatting my NTFS data drive?
Any idea what might be causing this?

If it is of any use, included is fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=361f8cb3-db7f-43aa-b6e4-cb287921e5bd /               ext3    relatime,erro$
# /dev/sda5
UUID=49c29a34-e9d6-40ea-9346-47579870fee4 none            swap    sw           $
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdc1       /media/400gb    auto    rw 0 0
/dev/sdb5       /media/video500 auto    rw 0 0

```
The computer I am running on is "Computer 2" in my signature... should be fast enough?
Movies are NOT high def, just a standard DVD.iso I ripped myself.
Thanks

---

### Post by articpenguin on 2008-05-10
try defragging the ntfs partition. If it plays back fine on ext3 it probably means the file on the ntfs partition is fragmented.

---

### Post by oddworld on 2008-05-10
Ok I will try that, but I don't have XP anymore because I was liking ubuntu so much.
Is there any way to defrag it in ubuntu?

---

### Post by Gina on 2008-05-10
I wondered about [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") but on checking the documentation, there is no reference to defragmenting (though it will recover NTFS formatted disks) so guess it won't.

One way, of course, is to copy/move all the data from the NTFS partition to somewhere else then reformat to ext3 and copy/move all the data back.  (Often quicker than defragmenting anyway if the drive is very fragmented)

---

### Post by oddworld on 2008-05-10
I would do that, but its a large hard drive with almost one TB of data and I don't have anywhere to put it.

---

### Post by ghost_ryder35 on 2008-05-10
download [ubcd4win]("http://www.ubcd4win.com/downloads.htm"), it has a defragger :)

---

