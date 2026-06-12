---
title: "USB volume awol"
date: 2024-09-01
forum: General Help
---

### Post by peter228 on 2024-09-01
Any suggestions please, I do not understand .......   (If relevant, a day ago I ran the upgrade from 22.04 to 24.04.)

I was using a file manager to copy files off a USB memory stick to the hdd.  All was working well.  Went away and came back to find that the copy had failed and the USB device was no longer listed.    I unplugged the USB stick and inserted again the the same port and tried in a different  port but in both cases the memory stick did not appear in the list of Devices.    So I ran lsusb and found that the device was listed there.   I tried another file manager to make sure there was nothing strange in the app but nothing different.

So the device is detected by lsusb but the device and volume is no longer listed in the file manager.

How to fix?

---

### Post by tea for one on 2024-09-01
Attach the USB stick.
Open a terminal and enter:-
```
sudo parted -l
```
Please post the command and output within code tags.

---

