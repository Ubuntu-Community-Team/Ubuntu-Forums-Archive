---
title: "Disk Usage reporting is wrong"
date: 2007-01-03
forum: General Help
---

### Post by petermck on 2007-01-03
Hi All,
I have an odd problem. I have a dual boot system. This is what fstab looks like.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4 -- converted during upgrade to edgy
UUID=1dd4ba53-b277-49ad-9f7c-27533b0446fa	/	ext3 defaults,errors=remount-ro	0	1
# /dev/hda1 -- converted during upgrade to edgy
UUID=3DE07A08C2FB6950	/media/hda1	ntfs-3g defaults	0	2
# /dev/hda5 -- converted during upgrade to edgyUUID=6844e0a0-9b9d-4a49-bf34-52cc94e4f249	none	swap sw 0 0
/dev/hdc	/media/cdrom0	udf,iso9660 user,noauto     0       0
```

When I upgraded I reduced the size of hda1 (holds the WinXP OS) and due to the inability of GParted to move a ext3 partition (at the time this was slashroot mounted on hda2) I had to create hda4 in the unallocated space between hda1 and hda2, copy hda2 to hda4, delete hda2 and then expand hda4. This all seemed to work quite well and I just had to update menu.1st and fstab. Everything booted up with no problems.
However, I have now noticed that for some reason both df and GParted are reporting my disk usage on slashroot incorrectly. They seem to include the ntfs partition hda1 mounted on /media/hda1 in the overall usage for /. Hence I loose the use of space on / equal to that used on hda1.
This is what df reports.
bitt3@bitt3:~$ df
```
Filesystem           1K-blocks      Used         Available   Use% Mounted on
/dev/hda4           34189616     24433788  9755828   72%   /
/dev/hda1           22932752     11377836  11554916  50% /media/hda1
```

Note that /media/hda1 is 50% used and / is 72% used. This is wrong. / should be about 11 GB less than this (the amount used on hda1). 
It appears that the usage on hda1 is included in the calculation for usage on /. That is, it's being reported twice and as a consequence I seem to have lost the use of a space on hda4 equal to the space used on hda1!!
Here is a screen shot from Disk Usage Analyser of the filesystem / **with** hda1 mounted....
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=22197&stc=1&d=1167851631[/IMG]
...and here's one **without** hda1 mounted.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=22198&stc=1&d=1167852343[/IMG]
Note the difference in the size of 'media'. This pretty much confirms what I'm thinking; that the distinction between space available on disk and the space available on a particular partition is not being handled properly.
Gparted shows this...
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=22201&stc=1&d=1167852374[/IMG]
...**in both cases**; with hda1 mounted and unmounted. The same is true of df.
/dev/hda1 is correct, but /dev/hda4 should show about 12GB used and 21GB free.
This has to be caused by some error in disk/partition usage reporting at a lower level (or perhaps df??), but I'm not sure where to look for the problem.:-k 
Can anyone shed some light on this? I don't think this was a problem in Dapper.

---

### Post by petermck on 2007-01-03
A minor typo in my previous post.
fstab looks like this;
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4 -- converted during upgrade to edgy
UUID=1dd4ba53-b277-49ad-9f7c-27533b0446fa	/	ext3 defaults,errors=remount-ro	0	1
# /dev/hda1 -- converted during upgrade to edgy
UUID=3DE07A08C2FB6950	/media/hda1	ntfs-3g defaults	0	2
# /dev/hda5 -- converted during upgrade to edgy
UUID=6844e0a0-9b9d-4a49-bf34-52cc94e4f249	none	swap sw 0 0
/dev/hdc	/media/cdrom0	udf,iso9660 user,noauto     0       0


```

---

