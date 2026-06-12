---
title: "Edgy &quot;Buffer I/O error on device hdc...&quot; w/LVM"
date: 2007-01-29
forum: General Help
---

### Post by StarsAndBars14 on 2007-01-29
Okay I've had a problem for the past couple of days that I need some opinions on.  When Edgy stars to boot I get this little message before the "Reading files needed for boot" part that says like so:

> 
Buffer I/O error on device hdc, logical block 64480
Buffer I/O error on device hdc, logical block 64481
Buffer I/O error on device hdc, logical block 64480
Buffer I/O error on device hdc, logical block 64481


and when I get to the step in the boot process that it wants to start LVM:

> 
Buffer I/O error on device hdc, logical block 0
Buffer I/O error on device hdc, logical block 1
Buffer I/O error on device hdc, logical block 2
Buffer I/O error on device hdc, logical block 3
Buffer I/O error on device hdc, logical block 4
Buffer I/O error on device hdc, logical block 5
Buffer I/O error on device hdc, logical block 6
Buffer I/O error on device hdc, logical block 7
Buffer I/O error on device hdc, logical block 0

The first thing I thought was that the hard drive is going bad.  After all this is a computer that I've had for 5 years and the HD hasn't been replaced once.  So I reboot and run fsck - the file system is clean. Then I run every kinda diagnostic you can think of - yes, including the full one that takes an hour and a half - from the HD manufacturer's tools (Its a Seagate ST380020A) and all come back "passed."

I doubt that the MBR is corrupt cos if it was I wouldn't be able to boot in Windows (this is a dual boot XP/Ubuntu comp) and the file system passes on XP too via chkdsk.  Quite honestly, I don't think my comp would be able to get past the blue HP screen at startup if the MBR was gone.

When I go to my logs though (through F7) I find 

> 
invalid KERNEL operation - /etc/udev/rules/40-fuse.rules.1


and this repeats 10 times.

If all else fails and I can't find some advice that ends up fixing this issue, I'm thinking of replacing the HD in the near future (upgrading so I don't have to buy a new box) anyway.

If this isn't against board etiquette, thanks for any help in advance.

---

