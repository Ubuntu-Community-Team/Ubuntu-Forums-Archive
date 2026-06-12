---
title: "'Unrecognised Partition Table'"
date: 2007-09-01
forum: General Help
---

### Post by Wired2k7 on 2007-09-01
I've just installed Ubuntu with the latest Wubi, but when I try and boot Ubuntu, it just says this:

```
(hd0,1)
Filesystem type is ntfs, partition type 0x7

Unrecognised partition table for drive 80.
Please rebuild it using a Microsoft-compatible FDISK tool  (err = 26).
Current C/H/S=155217/255/63.

```

Then some stuff about the device not accepting the address a few times. Then it says:

```
No RAID disks
```

I've googled Microsoft FDISK tool and had a look around but it looks like its only useful for ME and lower, but I am running XP Home on my laptop.

Thanks in advance :)

-Wired

---

### Post by tinybit on 2007-09-01
> 
Unrecognised partition table for drive 80.
Please rebuild it using a Microsoft-compatible FDISK tool  (err = 26).
Current C/H/S=155217/255/63.


This is a warning. It is not a serious problem. You can ignore it for now.

---

### Post by Wired2k7 on 2007-09-01
Even if I ignore that part, I still can't actually use Ubuntu because I'm stuck on the screen with the warning.

---

### Post by tuxcantfly on 2007-09-01
if you need access to fdisk or chkdsk, boot a windows xp install cd, and go into recovery mode using "r"

first, I'd do this:

```
chkdsk /r
```

that'll fix the errors on the drive, then I'd do that fdisk command (though back everything up before using fdisk)

---

### Post by Wired2k7 on 2007-09-02
Thanks, i'll try it as soon as I can back everything up :D

But when you say about then I should do that fdisk command, does that mean that there is an fdisk command on the screen that I can select, or is there a command I have to type in to use fdisk?

---

### Post by tuxcantfly on 2007-09-02
nevermind, I don't think that using fdisk is necessary, just use these 2 commands, after the chkdsk /r

fixboot

fixmbr

---

### Post by Wired2k7 on 2007-09-03
Thanks for the help :D

But I managed to install it from an alt. CD.

---

