---
title: "USB drive"
date: 2007-09-25
forum: General Help
---

### Post by FarmerJo on 2007-09-25
Hi,

Can anyone tell me how to determine if ubuntu has detected by pen drive? It is formatted as FAT32. Should it show in the Places|Computer page where all the other storage devices are located?

FarmerJo

---

### Post by PmDematagoda on 2007-09-25
Yes, it should, if it's mounted properly, if it isn't then it may not be, though I remember seeing my NTFS USB drive even after unmounting it, but usually if it has mounted properly, the USB's drive icon should appear on the desktop as well.

---

### Post by FarmerJo on 2007-09-25
I am new to ubuntu and would like to know how the pen drive should be mounted. Is it normally mounted automatically when the device is plugged in (like windows) or does this need to be manually performed each time it is plugged in?

Does it matter that it is formatted as FAT32?

FarmerJo

---

### Post by LaRoza on 2007-09-25
> **FarmerJo said:**
> I am new to ubuntu and would like to know how the pen drive should be mounted. Is it normally mounted automatically when the device is plugged in (like windows) or does this need to be manually performed each time it is plugged in?

Does it matter that it is formatted as FAT32?


Automatically.

FAT32 is a good format for a USB drive.

---

### Post by FarmerJo on 2007-09-25
Where exactly should it appear when it is inserted into the USB port. I cannot find it anywhere?

FarmerJo

---

### Post by LaRoza on 2007-09-25
If it lights up, it should be mounted under /media/<deviceName>

I use Fluxbox, and am not sure exactly it will be in GNOME, but it should appear on the desktop.

---

### Post by FarmerJo on 2007-09-25
Thanks.

It doesn't light up when it is plugged in to a USB port for some reason. I have tried plugging it in after ubuntu has started up and also starting ubuntu up after it has been plugged in.

The mouse is USB so I tried plugging the pen drive in at the back of the PC. This time it worked. Returning it to a front USB connector it was not recognized.

The USB ports at the front of the PC work because the pen drive is visible under windows xp. Looking under the Device Manager I can see two USB controllers. The one that works is USB 2.0 and the one that doesn't is USB 1.1.

Should this combination of USB controllers work with ubuntu? If so any ideas why neither of the two USB 1.1 ports are functional?

FarmerJo

---

