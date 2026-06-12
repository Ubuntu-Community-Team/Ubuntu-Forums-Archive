---
title: "Installed Wubi from D drive; C drive not automounting in /media/"
date: 2008-06-09
forum: General Help
---

### Post by fang2415 on 2008-06-09
The subject pretty much says it all.  I run Windows off of C: but installed Wubi from D:.  The D drive automatically mounts at /host no problem, but the C drive doesn't mount at all.  I can manually mount the C drive to /mnt with no problems, but this is my technophobe girlfriend's computer, so doing that every time it boots isn't an option.

I've seen a lot of people who just haven't known where to look (like me, at first), but I can't find any posts where the thing just clearly isn't mounting.  Does anyone have any ideas?

If anybody needs more info, just let me know and I'd be happy to post fstab/mount/fdisk -l/logs/whatever.

Thanks so much in advance!

F2

---

### Post by ago on 2008-06-09
I think that the default behavior is to not mount other volumes by default. This is nothing to do with wubi.

You should be able to access them under places > removable media

---

### Post by fang2415 on 2008-06-10
> You should be able to access them under places > removable media

Thanks for the reply -- I don't see a removable media entry under places though.  Just home, trash, desktop, file system, floppy, and recent docs.

You could be right that this isn't a Wubi problem, of course; I run a stripped-down Ubuntu/IceWM installation on my other machine, so I don't know the official desktop settings very well.  I should also mention that the Wubi install is running Xubuntu --  if you don't think it's a Wubi problem then I could try the Xubuntu forum.

---

### Post by rohitsb on 2008-06-10
Do this:
```

sudo nano /etc/fstab

```
This should display the current fstab file showing all the automounting details. The add the following line at the end:

```

/dev/sdaXX    /media/Cdrive    ntfs    user,rw,auto     0      0

```

Where,
XX represents the partition number (1,2,3 etc)
/media/Cdrive represent the folder where it will be mounted

Assumptions:
1. You have a sata disk (sda and not hda)
2. The /media/Cdrive is present  (if not, create - mkdir /media/Cdrive)
3. You want to write to disk
4. The disk is ntfs

Ctrl+X to exit and answer Y to save the file, keep file name as fstab.

You can choose any name instead of "Cdrive".
For a more detailed treatment of fstab, look [here]("http://ubuntuforums.org/showthread.php?t=283131").

Cheers

RSB

---

