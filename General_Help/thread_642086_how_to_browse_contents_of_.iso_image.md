---
title: "how to browse contents of .iso image"
date: 2007-12-16
forum: General Help
---

### Post by strungoutfan78 on 2007-12-16
is there a way that i can browse the contents and add files to an .iso image?  i know there has to be a way to do this, i just can't remember how.  

i installed acetoneISO2, but i can't seem to figure out exactly how to use it, or if it's even capable of doing what i want it to do.

any help appreciated. thx.:)

---

### Post by usien on 2007-12-16
perhaps you should have asked this on absolute beginner forum.

anyways, right click on the archive and select open with archive manager.

---

### Post by bulletxt on 2007-12-16
if you don't know how to use acetoneiso2 which has the simpliest gui I've ever seen....well....................

you can do what you want to do with your iso and a lot more:

[http://www.acetoneteam.org/latest-news.html](http://www.acetoneteam.org/latest-news.html)

be sure to have the latest 2.0 RC1 version.

---

### Post by strungoutfan78 on 2007-12-16
> **usien said:**
> perhaps you should have asked this on absolute beginner forum.

anyways, right click on the archive and select open with archive manager.

gosh i'm sorry for asking such a stupid question:rolleyes:
why didn't i think of that?
oh, wait, i already did....

maybe i could have mentioned that i have already done what you suggested, as i am not new to linux or ubuntu by any means.  unfortunately what is displayed is empty.  there appears to be nothing there when i know there is.

---

### Post by geraldm on 2007-12-16
Try mounting the iso image on a loop device.  Change the filename and mount point to suit you.
You may have to sudo or be root user.  Then you can browse in the mount point.
```

mount -t iso9660 -o ro,loop=/dev/loop0 cd_image00 /media/cdrom0

```
Gerald

---

### Post by strungoutfan78 on 2007-12-16
this is true, but i don't think i can add to the archive, can i?  i'll give it a shot. but i seem to recall trying this once before. thx.

---

### Post by geraldm on 2007-12-17
Excuse me for not making that clear.  To add a file, you may need to copy the files onto disk, add to that area, then make a new iso image, and write that.  Most CD and DVD drives do not allow overwriting. There is a way around that using a drive that has multi-session capability (and using software that can create a multiple session.  This appears to add, but really it is creating another image after the original; this adds the overhead of another table set for each session, so it is not very efficient, but it works.
With DVD, there is DVD-RAM, which also allows changes.

Gerald

---

### Post by strungoutfan78 on 2007-12-17
well i seems there is a problem with the archive maybe.  even when i mount it from the command line it appears to mount just fine but the contents of the folder are empty.  not even hidden, just empty.it only seems to happen with this particular .iso image, as i tried a different one  last night using acetoneISO2 as well as the cli and it worked just fine.

could it be something to do with the type of iso??  the only type of .iso i'm familiar with is 9660.  this particular image happens to be an MSDOS boot disk i'm trying to build to recover my fiancee's computer running WinXP.:rolleyes:

**EDIT** the only reason i'm trying to do this is because she works for a law firm and has alot of work related data i need to rescue from it.  other than that i have no intention of saving the OS.  i'm tansitioning her to ubuntu asap.

---

