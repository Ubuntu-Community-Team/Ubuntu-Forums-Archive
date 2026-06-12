---
title: "[SOLVED] Bunch of dirs &amp;amp; files disappeared off my XFS drive?!"
date: 2007-11-10
forum: General Help
---

### Post by snek on 2007-11-10
**EDIT:** It has been **solved,** I made a stupid mistake and found the files again.. I won't even tell you what it was, it was too stupid to mention here ;)


Ok, so I have this 500gb drive I setup as an XFS partition under: /media/500gb
Now, for some weird reason I seem to be missing a LOT of files all of a sudden!
Lets say I have the series South Park on my hard drive with a structure which looked like this:

(bold = directory, italic = file)

- **South_Park**
|----**Season 1**
|-------*south.park.s01e01.avi*
|-----[I]--south.park.s01e02.avi
[/I]|-----*--etc*
|----[B]Season 2
[/B]|-------*south.park.s02e01.avi*
|-------[I]south.park.s02e02.avi
[/I] |-------*etc*
|-*south.park.s11e01.avi*
|-*south.park.s11e02.avi*
... etc

For some weird reason, all the directories have disappeared except for the main South_Park directory and the season 11 files which were in that dir (not sorted yet). ALL the other directories (season 1->10) have disappeared! 
However, if I check munin for diskspace usage nothing seems to have changed, it still reports the same amount of space used.

I have tried unmounting and using xfs_check & xfs_repair, but no difference.
Here is my fstab:

```
# /etc/fstab: static file system information.
proc            /proc           proc    defaults        0       0
# /dev/hdc2
UUID=9f4d2d67-ae4c-4375-a4a4-4ccd818d3e12 /             ext3    defaults,errors=remount-ro,data=writeback,noatime 0       1

# /dev/sdb1
UUID=d0ff935d-ac73-4e21-a929-c44d76411d40 /media/500gb  xfs     noatime,nodiratime,logbufs=8                    0       2

# /dev/hdc1
UUID=066CF7F36CF7DB7F /media/hdc1                       ntfs    defaults,umask=007,gid=46                       0       1

# /dev/sda5
UUID=6C68E65968E62216 /media/sda5                       ntfs    defaults,umask=007,gid=46                       0       1

# /dev/sda6
UUID=84c9c5c4-bf12-4bda-8a0a-c66c9856c5f2 /media/250gb  xfs    noatime,nodiratime,logbufs=8                     0       1

# /dev/hdc3
UUID=599130b5-25ec-4fe9-8d78-c1e0df2002de none          swap    sw                                              0       0

# /dev/sdc1
UUID=42B0A9D0B0A9CAAD /media/MP3_DUMP                   ntfs    defaults,umask=007,gid=46                       0       1

#/dev/hda
/dev/hda        /media/cdrom0                           udf,iso9660 user,noauto,exec                            0       0

#/dev/fd0
/dev/fd0        /media/floppy0                          auto    rw,user,noauto,exec                             0       0

```

---

