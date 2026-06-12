---
title: "DVD-RW not working in Feisty"
date: 2007-04-29
forum: General Help
---

### Post by Rogue Jedi X on 2007-04-29
After I've upgraded my system to Kubuntu Feisty Fawn, my DVD-RW stopped working correctly (although strangely enough, my CD-RW works just fine). It's a Sony DVD-RW DW-Q30A.
Whenever I put in a DVD, be it full or blank, a box pops up, like it normally does, asking me whether I want to do nothing, look at it in Konqueror, or if it's a blank medium, if I want to burn it with K3B. If I click "Open in new window", Konqueror opens, but nothing shows up, like it's empty, although I know for a fact that the discs I've tried, aren't.
If I try burning blank DVDs, they just come out ruined. I think it just writes the lead-in and gives me an error.
CDs seem to work fine.
Here's my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=5f37e7b6-0df2-4784-a963-f59206082bb4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=cb9acc4a-aee9-4839-9cae-7fdddaf14263 /home           ext3    defaults        0       2
# /dev/sda1
UUID=141CE3001CE2DC2C /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=cab7479b-14e8-42ac-8206-4259c630e260 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```
And here's what happens when I try to mount it with a DVD in it:
```
roguejedix@rogga-alpha:~$ sudo mount /dev/scd0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: Not a directory

```
Any ideas? Thoughts?

---

