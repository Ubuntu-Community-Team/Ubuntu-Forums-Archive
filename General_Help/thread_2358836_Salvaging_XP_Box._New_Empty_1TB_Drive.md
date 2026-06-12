---
title: "Salvaging XP Box. New Empty 1TB Drive"
date: 2017-04-17
forum: General Help
---

### Post by asker3 on 2017-04-17
Hello,

I am trying to put Ubuntu on to an old XP. The hard drive died so I installed a new blank 1TB hard drive. The computer will not recognize the original Windows CD for some reason.

Ubuntu starts just fine and can be run from the "Try Ubuntu" option but trying to install Ubuntu it gives an error that I need at least 8.6 GB space to install Ubuntu and that this computer only has 8.0 GB. I have tried playing with the boot options but nothing changed.

What is going on?

Thank you.

---

### Post by Futant on 2017-04-17
Are you sure the new hard drive is being recognised and that the rest of the computer is functioning properly? Some more information about the hardware might help. Also look at your partitions - from the live environment ('Try Ubuntu'), have a look in GParted and post what it shows here, probably don't mess with anything yet though.

---

### Post by asker3 on 2017-04-17
Looks like it is only showing the flash drive in Gparted...

/dev/sda1  fat32  /cdrom  Ubuntu 16_0  7.45 GiB

---

### Post by oldfred on 2017-04-18
Does BIOS see drive.
Is BIOS set to AHCI, old BIOS may be IDE mode and that may not support larger drives.

---

### Post by asker3 on 2017-04-18
It says "Configure SATA as <IDE>" 
There is an option to change it to AHCI

---

### Post by asker3 on 2017-04-21
So how do you do this? How do you install Ubuntu to a new blank drive? It seems like it should be easy but apparently not. Any hints or clues?

---

### Post by oldfred on 2017-04-21
Is BIOS seeing drive correctly now that you changed to AHCI mode?
You may  still have an old BIOS and should keep / (root) smaller or within the first 137 GB of drive. Use rest of drive as /home or /mnt/data.

I normally partition in advance with gparted and then use Something Else to choose (change) which partition is / (root) and its format. If swap already exists on drive then installer auto finds that.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

