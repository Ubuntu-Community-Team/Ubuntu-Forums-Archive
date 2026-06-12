---
title: "is there a way to add a command to a symbolic link?"
date: 2007-06-17
forum: General Help
---

### Post by pixeldotz on 2007-06-17
since 7.04 has such trouble with automounting thumb drives and such i decided the simplest way for me to get my stick and ipod working ( i use my ipod as a portable drive with rockbox).

for my ipod

```
pmount /dev/sdb2
nautilus /media/sdb2
```

for my thumb drive

> pmount /dev/sdb1
nautilus /media/sdb1

this little script of course mounts the drive and displays its contents.

i could do this no problem but i was wondering if there was a way to add this line to a symbolic link... nautilus /media/sdb1... this way i can keep the icon and everything looking pretty :).

thanks for any help.

---

### Post by Nate53085 on 2007-06-17
I *think* I understand what you want.

You want an icon on your desktop that will mount the drive?

If this is what you want, simple rightclick on the desktop and create a launcher that points to your script with the icon you want.

---

### Post by fragos on 2007-06-17
Try System-> Preferences-> "Removeable Drives and Media"-> Storage tab.  Chek the box "Browse removable media when inserted".  If I'm not mistaken, that should open in Nautilus any storage media when mounted.

---

### Post by pixeldotz on 2007-06-18
all those options are checked but nothing except my optical drive ever automounts.

i'll try the launcher script thing.

---

### Post by pixeldotz on 2007-06-18
the launcher worked; thanks for the help.

---

