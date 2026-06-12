---
title: "[SOLVED] dd or Norton Ghost for image-copy of my HD?"
date: 2008-02-08
forum: General Help
---

### Post by geo909 on 2008-02-08
Hello everybody,

 I recently purchased an external 500 GB USB Hard Disk, so I decided to make a backup, an image-copy of my entire Hard disk (the internal, of course!)

 I searched a little over and there and I realised that It's as simple as throwing in my Ubuntu live CD and doing:

```
dd if=/dev/{internal disk} of=/mnt/external/myImage.img
```

 OK. Well, as I am not an experienced linux user and have never used dd before (which seems to be a classic for the geek-guys) I would like to ask a few questions.


1) Is dd ...errr... safe? I mean, is it good? Is it possible that -for example- a bad sector created after the backup will cause the backup to be unrestorable? Are there any risks when using dd?
2) Would you recommend Norton Ghost or dd? (I am dual-booting)
3) A command such as the one above will backup everything, including MBR, right?
I mean, after the restoration, I will have dual-boot, GRUB, etc?

 If you have experience with dd  and HD-image-backingup, could you please comment on this?

---

### Post by freymann on 2008-02-08
I read somewhere about a program called CloneZilla that would make an "image" of your hard drive, much the way that Norton Ghost works. If you google for cloneZilla you'll find it. It's free too.

---

### Post by jasmuz on 2008-02-08
Hi,

Personally i've been using partimage, for creating a backup of my system.
And also for installing several machines with the same specs.

As for me, i havent done this kind of thing under double booting, but im really sure it will work. Do read the manpage for this.

Take care.

---

### Post by geo909 on 2008-02-08
@freymann 
Ok, I'll have that in mind. But I would feel more comfortable with something mainstream.
 dd seems to be used enough and I would like just some feedback to be sure.


@jasmuz
I know partimage and it seems to be very convenient but the thing is that its NTFS support is still experimental. Although it possibly won't have any problems, I don't know if I would like to experiment with my NTFS partition..

Has anyone tried dd for such a purpose?

---

### Post by geo909 on 2008-02-08
Any other opinions?
Anyone who has tried dd?

---

### Post by shaggy999 on 2008-02-08
Clonezilla is what you want as a previous person suggested. It is a full-featured disk duplication system for all sorts of file systems, including windows and linux partitions. The great thing about it is that it only copies sectors that have data in them (meaning it doesn't copy the free space, which using a command like dd will do) and it supports several levels of compression. There's even a clonezilla bootcd that's all automagical and stuff. After using ghost (both the corporate and consumer version) I can say that clonezilla is better than whatever symantec offers.

The only downside is that you can't "mount" images it creates to extract individual files. You have to restore an entire image to get at individual files. But extraction support should be coming eventually.

Seriously, use CloneZilla.

---

