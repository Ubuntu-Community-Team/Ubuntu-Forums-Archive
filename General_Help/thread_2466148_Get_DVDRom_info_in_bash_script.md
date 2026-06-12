---
title: "Get DVDRom info in bash script"
date: 2021-08-21
forum: General Help
---

### Post by jamesdank8 on 2021-08-21
I can get my dvd rom drive info but I'm unsure how to assign the drive name to a variable in bash.

This is the output from cat /proc/sys/dev/cdrom/info
```

CD-ROM information, Id: cdrom.c 3.20 2003/12/17

drive name:        sr0
drive speed:        24
drive # of slots:    1
Can close tray:        1
Can open tray:        1
Can lock tray:        1
Can change speed:    1
Can select disk:    0
Can read multisession:    1
Can read MCN:        1
Reports media changed:    1
Can play audio:        1
Can write CD-R:        1
Can write CD-RW:    1
Can read DVD:        1
Can write DVD-R:    1
Can write DVD-RAM:    1
Can read MRW:        0
Can write MRW:        0
Can write RAM:        1

```

---

### Post by TheFu on 2021-08-21
What do you mean by "assign the drive name to a variable in bash"?
The normal device for optical drives is /dev/srX, where X is numerically increased by 1 for each new device of the same type.

Wouldn't it be easier to just automatically mount the media in the drive to /cdrom or /dvd?  Autofs can do that.

But perhaps you are trying to re-invent some wheel that already exists?

---

