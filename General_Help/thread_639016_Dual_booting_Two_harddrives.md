---
title: "Dual booting Two harddrives"
date: 2007-12-12
forum: General Help
---

### Post by ACrazyGerman on 2007-12-12
I just got a 15 gig harddrive and installed Ubuntu on it I also have a 40 gig hard drive with XP on it I took the XP hard drive out of my computer while I installed Ubuntu. I have both hard drives on Cable Select, XP master Ubuntu Slave. I want to be able to select which one boots at start up. but when I turn on the computer it boots directly to XP.

---

### Post by scott_g on 2007-12-12
Hi,

You need to change the default boot system to your Ubuntu drive.  This is done through your computer's BIOS (hit F1/F10/Esc --different for every computer -- on the initial splash screen).  Next, you're going to have to add entries for your windows drives into GRUB's configuration file.  There may be a GUI, but I prefer to use the config file.  The file is located in /boot/grub/menu.lst.  There are some example lines in the file to help you boot a Windows HD.  If not, I can post mine.  You'll likely need to know what hard drive you are booting from; it can be found in the Gnome system monitor, in the HD tab; it lists the path; should be /dev/hda or /dev/sda, etc...

To edit the grub config file, type:
```

sudo gedit /boot/grub/menu.lst

```

If you need more help, I can give more details....

Thanks,
Scott

---

### Post by ACrazyGerman on 2007-12-13
What if I have both hard drives in the computer and reinstall Ubuntu?

---

### Post by scott_g on 2007-12-13
If you did that, Ubuntu would set up GRUB for you, but you would still have to change the default drive that is booted....

Scott

---

### Post by ACrazyGerman on 2007-12-13
So how do I set it up so XP boots up first without going to grub and still having an option to switch to ubuntu one of my friends she wants to boot by default to XP but still have an option to boot to ubuntu.

---

