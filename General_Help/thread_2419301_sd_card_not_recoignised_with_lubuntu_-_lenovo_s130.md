---
title: "sd card not recoignised with lubuntu - lenovo s130"
date: 2019-05-19
forum: General Help
---

### Post by mtlinix on 2019-05-19
Hello i have a new netbook a lenovo s130, which doesn't seem to have much support from linux yet.
I managed to get the touchpad working by typing a few commands in  terminal and get wifi driver installed by downloading a driver and  running it from terminal after following instructions on this forum,


The SD card is not recognised, when i insert a microSD into the laptop nothing happens, theres no card being registered.
USB 3.0 ports are working with no issues.

After research online, i think the failure to read the microSD may also be a driver issue.

When i type lspci in the terminal it displays "rts5229 pci express card reader" among the results. i can see that driver on realtek website, and i saw some pages about compiling the driver but it was too technical for me and not quite on topic to what i was searching.


Does anyone have a solution for this? thanks

my netbook
[https://www.lenovo.com/gb/en/laptops/ideapad/s-series/Lenovo-ideapad-S130-14IGM/p/88IP10S1076](https://www.lenovo.com/gb/en/laptops/ideapad/s-series/Lenovo-ideapad-S130-14IGM/p/88IP10S1076)

---

### Post by DuckHook on 2019-05-19
If the problem really is a card reader driver issue, then you will have to wait for someone more knowledgeable to help you.

However, it could also be your card. If it is more than 32 GB then it is probably formatted to exfat, which Ubuntu will not recognize unless you install exfat drivers:```
sudo apt install exfat-fuse exfat-utils
```
Alternatively, since exfat is a propietary MS format, you can reformat the card to a filesystem that Ubuntu recognizes natively. Try ext2 or ext4 with journaling disabled. However, note that such native Linux formats will be unreadable to Windows.

---

### Post by mtlinix on 2019-05-20
hello, the card is operating fine.
and it is 32gb formatted to FAT32 already

if SD is not being read by linux i dont understand how i could perform a format to etx2 or etx4

---

### Post by DuckHook on 2019-05-20
> **mtlinix said:**
> …if SD is not being read by linux i dont understand how i could perform a format to etx2 or etx4

> **DuckHook said:**
> If the problem really is a card reader driver issue, then you will have to wait for someone more knowledgeable to help you.
i.e. Your problem is a HW issue and I don't have the knowledge to help you with that. Hopefully, someone will be along shortly who has experience with your equipment.

---

### Post by mtlinix on 2019-05-21
sure, thanks for the ideas anyway

---

### Post by mtlinix on 2019-06-15
the usb reader  was actualy faulty and i had it (the netbook)  repaired by lenovo.

---

### Post by tiger-jrsmit on 2020-02-17
> **mtlinix said:**
> the usb reader  was actualy faulty and i had it (the netbook)  repaired by lenovo.

When the laptop returned did the SD card work correctly? Another user and I are having issues with the s130 and the SD card under linux as can be seen here
[https://ubuntuforums.org/showthread.php?t=2435990](https://ubuntuforums.org/showthread.php?t=2435990)

---

### Post by mtlinix on 2020-03-12
actually no i dont think it did work afer the repair(?) but now it does, (as does wifi without requiring instal rt driver)
 
sd card reader works on my lenovo s130 and latest lubuntu 19.10

---

