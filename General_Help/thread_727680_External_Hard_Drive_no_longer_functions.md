---
title: "External Hard Drive no longer functions"
date: 2008-03-18
forum: General Help
---

### Post by CD27 on 2008-03-18
Ever since my computer crashed and i had to reinstall linux, my External hard drive has been completely unfunctional. It turns on, but it won't show up.

Also, my backed up list of software isn't installing when i put in the function

```
sudo dpkg --set-selections < dpkglist.txt
sudo apt-get -y update
sudo apt-get dselect-upgrade
```

i have my list in a text file, but it won't work. The upgrade worked, but I dunno bout the update.

---

### Post by adult swim on 2008-03-18
with your external HD plugged in, go to the terminal and type
```
sudo fdisk -l
```
then post the output you get
EDIT: i may have gotten in here a little bit over my head.  what i was going to tell you to do next wont work.  
let me bring it back down to my level.
alternatively, go to places/computer
if it shows up there when its plugged in you can right click it and select mount, then you should be able to access it.

---

### Post by CD27 on 2008-03-18
```
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2f1f2f1

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4700    37752718+  83  Linux
/dev/hda2            4701        4864     1317330    5  Extended
/dev/hda5            4701        4864     1317298+  82  Linux swap / Solaris

```

It's a 500 GB External Hard Drive.

---

### Post by adult swim on 2008-03-18
is your external HD formatted in ntfs or fat32?

---

### Post by CD27 on 2008-03-18
i don't know

---

### Post by adult swim on 2008-03-18
have you used the hd in windows? and if so, the last time you unplugged it did you eject it first?

---

### Post by CD27 on 2008-03-18
i only have linux, i used to use it in windows, but that's been almost a month and i've used it alot in linux since then

---

### Post by CD27 on 2008-03-19
anyone?

---

### Post by enchantedsky on 2008-03-19
I am hypothesizing your situation........you should troubleshoot as if your hard drive broke also, even though you think that it's Linux's fault.

1) Plug in *any* other flash drive you may have. Does Ubuntu recognize it? If it does, it implies something is wrong with your hard drive

2) Plug in your hard drive in another computer's USB port, and see if its operating system recognizes it. If it isn't recognized, then it implies something is wrong with your hard drive.

Honestly, if it were Ubuntu's fault, and this happened to me, I would reinstall the OS, thinking that something is corrupt, but don't have the time to go through setup files to see what's wrong. Unless someone else has a better idea...

---

### Post by CD27 on 2008-03-22
okay, it's fixed now. Lol, it was the dumbest thing. All i had to do was restard my computer (i haven't restarted the computer in a long time since the crash, and i guess it just needed to reboot itself after the crash....lol, duh!)

Thanks guys.

---

