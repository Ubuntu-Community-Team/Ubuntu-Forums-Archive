---
title: "Can't rename partitions in Hardy"
date: 2008-04-26
forum: General Help
---

### Post by Shampyon on 2008-04-26
I've done a fresh install of 8.04 rather than upgrade. Always best to start with a clean slate, I say. It's not much of a problem because before installing I back up my Firefox and Thunderbird profiles and place them on one of the four other partitions on my SATA drive.

I noticed that in a fresh install those partitions wouldn't automount at startup, so I added them to fstab. They're all the same size, so I'd like to rename them to their mount point names to make them easier to tell apart in Nautilus' "Places" pane. Unfortunately when I try to rename them I get this error:

> The item could not be renamed.
Sorry, couldn't rename "47.0 GB Media" to "sdb8": Operation not supported by backend

I'm reasonably sure it's not a permissions problem, as it doesn't work whether I try as a user or root.

My fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=283aa65d-1ec8-41fb-8858-ab1a89001afb /               reiserfs notail,relatime 0       1
# /dev/sdb9
UUID=6180b5f7-152f-4942-b253-02631555ae18 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#Shampyon's Edits
#sdb5
UUID=8a3a9f51-7010-4bbe-8f07-40d4b2e6f6d3	/media/sdb5	reiserfs	auto,users,rw	0	2
#sdb6
UUID=9e3a4932-795c-41e4-b96a-4c33ba032c74	/media/sdb6	reiserfs	auto,users,rw	0	2
#sdb7
UUID=e35621df-059d-4288-b99c-8917ba917848	/media/sdb7	reiserfs	auto,users,rw	0	2
#sdb8
UUID=e6df3e16-1257-46a8-aa93-2718b84102a4	/media/sdb8	reiserfs	auto,users,rw	0	2
```

---

### Post by steve_4802 on 2008-04-26
Exactly the same issue here. I upgraded from gutsy, not a fresh install.

In gutsy I just ensured the directory I was mounting to in fstab was the name that I wanted the partition to be called - but as you've also discovered this doesn't seem to work.

Does anyone know of a way to name the partitions to anything other than the default XXGB Media?

---

### Post by Somnus07 on 2008-04-26
Hi,

You might be looking for 'Storage Device Manager' which you can install from add/remove... it then appears under system>administration>Storage Device Manager
or from terminal: gksudo pysdm

Or what you probably want to do is to edit the label in partion editor or manually, eg from here: [http://ubuntuforums.org/showthread.php?t=283131&highlight=set+disk+label](http://ubuntuforums.org/showthread.php?t=283131&highlight=set+disk+label) under How to Label

---

### Post by Shampyon on 2008-04-26
Storage Device Manager doesn't seem to have worked for me. My partitions are all still named by their size. Does it require a restart to kick in?

I also tried ReiserFSTune, but got this error:

```
:~$ reiserfstune --l sdb5 /media/sdb5/
bread: Cannot read the block (2): (Is a directory).
reiserfs_open: bread failed reading block 2
bread: Cannot read the block (16): (Is a directory).
reiserfs_open: bread failed reading block 16

reiserfs_open: the reiserfs superblock cannot be found on /media/sdb5/.
reiserfstune: Cannot open reiserfs on /media/sdb5/

```

I've got a whole lot of data on these partitions so I can't use any destructive means.

---

### Post by gb5757870 on 2008-04-26
Glad to see I'm not the only one. Have spent the whole morning changing fstab entries and other methods to rename. Hopefully some guru will enlighten us

---

### Post by Somnus07 on 2008-04-27
It looks like the Storage Device Manager doesnt actually change the labels only the mount points.

when doing the reiserfstune you need to point it to the device rather than the mount point, eg:

```

sudo reiserfstune --l sdb5 /dev/sdb5

```

although the output after that is a problem; about the superblock.  As far as I can tell, the different types of code are for different filesystems. eg ext3, ReiserFS, ntfs ... 
So you will have to make sure you are using the right one.

---

### Post by louieb on 2008-04-27
I get the partition names to be what I want by giving the partition a label.
For ext3 you can use [B]e2label.
[/B]```
 e2label device [ new-label ]
```
or VisParted  available on the [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic") can set labels on other file system types too.

---

### Post by Shampyon on 2008-04-27
> **Somnus07 said:**
> 
sudo reiserfstune --l sdb5 /dev/sdb5


That did the trick! Thanks!

---

