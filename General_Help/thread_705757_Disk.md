---
title: "Disk"
date: 2008-02-23
forum: General Help
---

### Post by gmlinux on 2008-02-23
I have two hard drives in my computer, one has XP and the other has UBUNTU.
I am using the KDE desktop and I cannot find my other hard disk anywhere. How do I find it and put an icon on my desktop for it/
Murry

---

### Post by free beer and brats on 2008-02-23
Hi Murry - is the drive mounted?  try opening a terminal and typing: ```
less /etc/fstab
``` to see if the drive is listed there (hda is one drive, hdb will be the other).  The other drive may be b or a, depending on which one you are running the Linux install on.  If you figure out which one it is, mount it with ```
mount /dev/hdb
``` assuming it is hdb, of course... I will probably mount in /media/<drive name here>.  hope that helps.

---

### Post by taurus on 2008-02-23
You just need to add an entry in /etc/fstab to mount your windows harddrive.  Why don't you open a terminal and post the output of this command here?

```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
That is an upper case letter L.

---

### Post by gmlinux on 2008-02-25
Thanks for the suggestions, found it, needed root privelidges.

---

