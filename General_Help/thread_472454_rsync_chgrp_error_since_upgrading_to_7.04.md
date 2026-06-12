---
title: "rsync chgrp error since upgrading to 7.04"
date: 2007-06-13
forum: General Help
---

### Post by andy gee on 2007-06-13
Ever since reinstalling for Ubuntu 7.04, whenever I rsync (to either a USB drive or another internal drive, or even within the same drive) I get an error with chgrp, which I think is a tool that rsync uses. It changes group ownership in (according to its man page, in much the same way as chown does) and this means that group permissions are not passed on.

An example (same results if I use sudo) using rsync -av is below. I've only copied a section of it, not the whole lot:
```

rsync -av ~/music-2go /media/disk
......
music-2go/2go-ogg/The Breeders/title TK/
rsync: chgrp "/media/disk/music-2go/2go-ogg/The Breeders/title TK" failed: Operation not permitted (1)
music-2go/2go-ogg/The Breeders/title TK/The Breeders-title-TK_01_Little Fury.2go.ogg
rsync: chgrp "/media/disk/music-2go/2go-ogg/The Breeders/title TK/The Breeders-title-TK_02_London Song.2go.ogg" failed: Operation not permitted (1)
rsync: chgrp "/media/disk/music-2go/2go-ogg/The Breeders/title TK/The Breeders-title-TK_03_Off You.2go.ogg" failed: Operation not permitted (1)
music-2go/2go-ogg/The Breeders/title TK/The Breeders-title-TK_04_The She.2go.ogg
music-2go/2go-ogg/The Breeders/title TK/The Breeders-title-TK_05_Too Alive.2go.ogg
rsync: chgrp "/media/disk/music-2go/2go-ogg/The Breeders/title TK/The Breeders-title-TK_06_Son of Three.2go.ogg" failed: Operation not permitted (1)
music-2go/2go-ogg/The Breeders/title TK/The Breeders-title-TK_07_Put On A Side.2go.ogg
music-2go/2go-ogg/The Breeders/title TK/The Breeders-title-TK_08_Full On Idle.2go.ogg
music-2go/2go-ogg/The Breeders/title TK/The Breeders-title-TK_09_Sinister Foxy.2go.ogg
music-2go/2go-ogg/The Breeders/title TK/The Breeders-title-TK_10_Forced to Drive.2go.ogg
music-2go/2go-ogg/The Breeders/title TK/The Breeders-title-TK_11_T and T.2go.ogg
rsync: chgrp "/media/disk/music-2go/2go-ogg/The Breeders/title TK/The Breeders-title-TK_12_Huffer.2go.ogg" failed: Operation not permitted (1)
rsync: chgrp "/media/disk/music-2go/2go-ogg/The Breeders/title TK/.The Breeders-title-TK_01_Little Fury.2go.ogg.OOtOa1" failed: Operation not permitted (1)
rsync: chgrp "/media/disk/music-2go/2go-ogg/The Breeders/title TK/.The Breeders-title-TK_04_The She.2go.ogg.Z0QuWt" failed: Operation not permitted (1)
rsync: chgrp "/media/disk/music-2go/2go-ogg/The Breeders/title TK/.The Breeders-title-TK_05_Too Alive.2go.ogg.cwtGbX" failed: Operation not permitted (1)
rsync: chgrp "/media/disk/music-2go/2go-ogg/The Breeders/title TK/.The Breeders-title-TK_07_Put On A Side.2go.ogg.L4njMq" failed: Operation not permitted (1)
rsync: chgrp "/media/disk/music-2go/2go-ogg/The Breeders/title TK/.The Breeders-title-TK_08_Full On Idle.2go.ogg.IJwLGU" failed: Operation not permitted (1)
rsync: chgrp "/media/disk/music-2go/2go-ogg/The Breeders/title TK/.The Breeders-title-TK_09_Sinister Foxy.2go.ogg.Pt9uOp" failed: Operation not permitted (1)
rsync: chgrp "/media/disk/music-2go/2go-ogg/The Breeders/title TK/.The Breeders-title-TK_10_Forced to Drive.2go.ogg.CVdLWV" failed: Operation not permitted (1)
rsync: chgrp "/media/disk/music-2go/2go-ogg/The Breeders/title TK/.The Breeders-title-TK_11_T and T.2go.ogg.LmyFos" failed: Operation not permitted (1)
........

```
and the permissions end up being:
```
drwx------ 
```
but should have been:
```
drwxr-xr-x
```


It means I have to go through and chmod everything afterwards and that's a pain. Any help out there?

Ta

---

### Post by andy gee on 2007-06-14
bump-diddly-bump-bump! :biggrin:

---

### Post by mdurham on 2007-06-14
what of you 'sudo rsync...', would that help?

---

### Post by andy gee on 2007-06-14
> what of you 'sudo rsync...', would that help?

Hey mdurham - thanks, but nah - tried that already, and get same results if I use sudo. Any other ideas? Pleeeeease?

---

### Post by mdurham on 2007-06-14
what format is the destination ext3 fat32 or what?
I had trouble rsyncing to fat32

---

### Post by andy gee on 2007-06-14
Both FAT32 and ext3. Haven't tried ext2, but I don't think that would make a difference. Certainly, I had no problems with rsync in 6.10. Maybe I should go to launchpad and report it as a bug?

---

### Post by mdurham on 2007-06-14
I had the same problem, Edgy worked ok on fat32 but not on Feisty. I have no problem with ext3 on either though. I don't think fat32 can have owners and permissions etc. so it's probably not a bug, just rsync being a bit more picky. (and correct)

---

### Post by andy gee on 2007-06-14
but chgrp error this happens on both ext3 and FAT32.

---

### Post by jeepescu on 2007-09-11
Did anyone find a fix for this error ?

---

### Post by roderikk on 2007-09-22
I still have this error as well. Trying to upload to a Fat32 usb drive.

---

### Post by takayuki on 2008-01-23
yep, i got the same errors trying to backup to a fat32 sd card.  is there a workaround?

---

### Post by jashore on 2008-02-12
replace "-av" with "-rltDv" for the rsync options.
That will remove the preserve user/group/other options condition.

Which I read on anther thread: [HTML]http://ubuntuforums.org/archive/index.php/t-624198.html[/HTML]

---

### Post by pingnak on 2008-02-17
Try adding the following flags to your invocation of rsync: **--no-o --no-g**

The '--no' option turns a flag OFF, and the -o and -g options are the set-owner and set group flags.  Adding these flags made the problem 'go away' for my flash-based (SDHC) backup.

For whatever reason, contrary to the documented behavior, these flags appear to behave like they're turned ON by default when it writes to a FAT32 drive, such as a FLASH drive that will be used to play MP3 files on some backwards device that only recognizes FAT32.

What's worse, it does so INTERMITTENTLY.  It succeeds for hundreds of files and fails for dozens of files, but if you run it again, it succeeds for some of the files it previously failed.  

In other words, it acts a lot more like a bug than a 'feature'.

---

### Post by joneall on 2008-06-08
I have the same problem in Kubuntu Feisty. I noticed something odd tho, which I also see in your listing. The files it cannot chgrp all start with a period (or dot, for americans). Maybe this is something clever on the part of rsync, but in my case at least, there are no such files. 

Why does it show them?

---

### Post by roderikk on 2008-06-09
The problem I found, way later, is that FAT32 does not know about permissions and stuff. So I reformatted the drive as Ext3 and now it works perfectly.

I reformatted it using gparted, which is just in one of the repositories.

---

