---
title: "cdrom not mounting correctly"
date: 2008-01-30
forum: General Help
---

### Post by russo.mic on 2008-01-30
So,  Need some help here.  

My CDROM won't mount or unmount any cd, dvd, data cd, audio cd or otherwise unless it's there at the time of boot up.  If I boot up with a cd, then eject it, the icon still stays on the desktop.  I'm confused.  any ideas?

MBP running 7.10.  Thanks!

Russo

---

### Post by rune0077 on 2008-01-30
EDIT: before trying the below, check this. System > Preferences > Removable Drives and Media. Under the first banner, make sure that "Mount removable media when inserted" is checked.

What happens when you insert the CD/DVD, then right-click on the drive and select mount?

Alternatively, try to mount it through the terminal:

```
mount <NameOfDrive> <PathToDriveFolder>
```

NameOfDrive: should be the name of the drive (typically /dev/hda or some such)

PathToDriveFolder: usually this will be /media/cdrom0, but check your /media folder for the right name.

---

### Post by russo.mic on 2008-01-31
So,

I didn't even think to try to right click on the Drive icon and mount that way.  It works, however, How do I mount audio CD's?

Thanks again!

Russo

---

### Post by russo.mic on 2008-01-31
So,

I didn't even think to try to right click on the Drive icon and mount that way.  It works, however, How do I mount audio CD's?  secondary, I've got the auto-mount option checked, so why isn't it auto-mounting?

Thanks again!

Russo

---

### Post by russo.mic on 2008-01-31
Oh, and if I play an audio CD with VLC or something, it seems as though the program is playing it, however, nothing comes out of the speakers.

Russo

---

### Post by rune0077 on 2008-01-31
> **russo.mic said:**
> Oh, and if I play an audio CD with VLC or something, it seems as though the program is playing it, however, nothing comes out of the speakers.

Russo

Weird. Do your get sound under other circumstances?

---

### Post by russo.mic on 2008-02-05
Sorry,  Went out of town.

Yeah, I get sound under normal circumstances.  My main problem is simply that if I eject the CD, the icon still stays on the desktop.

Russo

---

