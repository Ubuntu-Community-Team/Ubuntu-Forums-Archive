---
title: "Mounted FAT32 partition owned by root/plugdev"
date: 2007-11-21
forum: General Help
---

### Post by chochem on 2007-11-21
I found this post which deals with the same problem I have, but the ubuntuguide link's broken (refers to old version): [http://ubuntuforums.org/showthread.php?t=95950](http://ubuntuforums.org/showthread.php?t=95950)

Basically, during installation I set things up so that my FAT32 partition (/dev/hda5) would be mounted as /shared. ls -l informs me that it (and all subdirectories) is owned by root of plugdev group. I've tried
```
sudo chown mads:mads /shared
``` (mads:mads being the ownership of my home directory)
but I just get told that it's not permitted. I believe I need to switch ownership in order to do some chmod operations that will allow me to write to some directories there.

---

### Post by KiXeR on 2007-11-21
Try;

sudo chown -R mads:mads /shared

than to give permission to read/write

sudo chmod -R 755 /shared

Hope it helps! :)

/K

---

### Post by chochem on 2007-11-21
No, unfortunately, all that does is attempt to change ownership for /shared and all subdirectories. So I get a long list of "Operation not permitted"....

---

### Post by mesocal on 2007-11-21
I have the same problem.  By chance are you trying to setup /home on a vfat?

---

### Post by mesocal on 2007-11-21
Not that i know,  but i feel this is all from how i mount the partition.  Whatever i am doing, is only allowing root the ability to rw.  

The problem with this is, when i create my new /home by issuing "**$find . -depth -print0 | cpio –null –sparse -pvd**" i get an error.  but obviously when i issue "**$find . -depth -print0 |sudo  cpio –null –sparse -pvd**" everything is copied - but now is has been copied with the root:root ownership.  i have not figured out any way to change to ownership sudo chown -R doesnt work,  nothing does.  anyone have a suggestion?

---

### Post by johonbravo on 2008-02-20
I have a fat32 storage partition with the same problem (being owned by root/plugdev).

I tried using root to chown or chgrp the directory and it returns "Operation not permitted".

Same issue...

---

### Post by johonbravo on 2008-02-20
Hmmm after a little research:

VFAT does not store owner information, so it is set by default in ubuntu to root.

I just installed win/ubuntu and all partitions on this brand new clean 250gb harddrive to upgrade from my 60gb. on my 60gb I used a fat32 shared storage partition no problem, with reading & writing to it. Now on my 250GB it assigns the wrong user & wont let me change it.

---

### Post by mesocal on 2008-02-21
i cant remember what i did, but i did solve this - well, kind of.  i think i SU and then changed the ownerships. but i ran into another problem with that dealing with ICE.  after a few days,  i ended up formating my VFAT to an EXT 83 and now everything is fine. tomorrow, i'll look more into this.

---

### Post by chochem on 2008-02-21
I kinda wish I could chip in here, seeing as I started it, but I abandoned the shared FAT32 partition in favor of an external harddrive that I formatted as NTFS from Windows (it's still root's but permissions are 777 as seems fitting for an external drive). Seeing as NTFS can be read/written from Ubuntu, maybe that's a better option for a shared partition? Else I believe there are some ways to [make Windows see the light]("http://del.icio.us/search/?fr=del_icio_us&p=ext3+windows&type=all") :)

---

### Post by bastubis on 2008-04-15
Also driving me up the wall. My Freecom USB pen drive was mounting absolutely fine until some files got corrupted during an OOo crash. It then started mounting as root with plugdev group and I couldn't write to it. 

I formatted the drive and remounted it -- exactly the same problem. Ran fsck, no errors on the drive. CHMODded and CHOWNed -- no apparent effect. The thing is still showing up read only in Nautilus. Then I checked the actual media folder using ls -l and realised the drive is actually mounted with the correct user and group and is writable. 

It's only when accessed from the side panel of Nautilus that it's read-only. If you either use a terminal or navigate through it's 'real' path in Nautilus (/media/disk) you can write to it. 

Anyone know how I can persuade it to behave properly in the side-panel of Nautilus?

---

