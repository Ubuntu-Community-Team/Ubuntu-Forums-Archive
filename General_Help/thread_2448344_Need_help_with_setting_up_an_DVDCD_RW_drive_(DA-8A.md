---
title: "Need help with setting up an DVD/CD RW drive (DA-8A6SH) with Ubuntu 20.04"
date: 2020-08-06
forum: General Help
---

### Post by sormazi on 2020-08-06
[SIZE=2][FONT=arial][COLOR=#1A1A1B]Trying to find a driver for this internal DVD drive that I'm using with a slimline SATA to USB cable. Cable/drive is working properly as I tried this setup on a windows computer. It showed up [/COLOR][COLOR=#1A1A1B]under removable devices and I could use right click -> eject to eject the drive to put a disc in. I couldn't get this to work[/COLOR][COLOR=#1A1A1B] with Ubuntu 20.04. Drive is showing up as CD/DVD Drive [/COLOR]PLDS DVD-RW DA8A6SH (GL61) in Gnome Disks. Thanks for any help in advance. 
Image of the drive I'm trying to use: [/FONT][/SIZE][https://imgur.com/P4efptA](https://imgur.com/P4efptA)
[SIZE=2][FONT=arial]Screenshot of Gnome DIsks: [/FONT][/SIZE][https://imgur.com/a/4WDaDa0](https://imgur.com/a/4WDaDa0)[SIZE=2][FONT=arial]
[/FONT][/SIZE][IMG]https://imgur.com/P4efptA[/IMG]

---

### Post by Autodave on 2020-08-06
Is the drive working normally other than getting the tray to open?

---

### Post by ActionParsnip on 2020-08-06
You can open the tray with:
```

sudo eject /dev/sr0

```

---

### Post by CelticWarrior on 2020-08-06
Welcome.

Drivers for all optical drives are already included. No user action needed.
You need to get out of the Windows mentality and understand that different OSes work differently.

---

