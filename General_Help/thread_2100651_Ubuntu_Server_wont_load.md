---
title: "Ubuntu Server wont load"
date: 2013-01-02
forum: General Help
---

### Post by LuniTux on 2013-01-02
Hello,

One of my servers froze this morning. The mouse and keyboard would not work, it would not allow me to map to it and I could not ping  or ssh it. I held in the power button to shut it off, but when I tried to turn it back on, all I get is:

```
GRUB loading.
_
```

The line continues to blink but even after about 10 minutes, it does not load. I tried a live CD and it would load but I could not access the hard drive. Any help would be appreciated.

Thanks,

---

### Post by dino99 on 2013-01-02
looks like a hdd issue, need to check (powered off ?)

---

### Post by irv on 2013-01-02
If you can boot with the live OS DVD or USB, run gparted to see if it will read the HD.

---

### Post by sanderj on 2013-01-02
... and if you can't see the HDD from live-Ubuntu, reboot and go into the BIOS to see what the BIOS says about your HDD. If even the BIOS doesn't see it, check the cables.

---

### Post by LuniTux on 2013-01-02
The hdd was not appearing in the BIOS so I let the computer sit for a while. A few hours later it fully loaded for about 5 minutes then started showing message boxes with the red circle with the line through it and all of the text was appearing as boxes. I tried **ls** but it was showing that there was not any folders on the computer... I also tried putting the hdd in another computer as a slave drive but the other computer could not see the drive.

I think I need a new hdd... :o

---

### Post by sanderj on 2013-01-02
OK, too bad.

Related info: install and use GSmartControl to monitor the SMART health of your harddisks ...

---

### Post by LuniTux on 2013-01-02
> **sanderj said:**
> OK, too bad.

Related info: install and use GSmartControl to monitor the SMART health of your harddisks ...


gsmartcontrol is a nifty little program, I will have to remember that. :)

---

