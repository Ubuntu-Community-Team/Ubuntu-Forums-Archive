---
title: "Copy files from Playstation 3  (Hitachi) hard drive during Kubuntu Live"
date: 2018-11-23
forum: General Help
---

### Post by e-zombiehero on 2018-11-23
Hi, new to the forums and linux in general and I was wondering how (if at all possible) one would go about copying files from internally connected PlayStation 3 Hard Drive, while booted in Kubuntu Live (18.10). I have photos and music I'd like to extract, but atm I cannot use the system itself.

The drive is recognized by my laptop, (confirmed this by installing Kubuntu on my spare), but there doesn't seem to be a way to explore it in Dolphin. Thank you in advanced for your time.

---

### Post by ajgreeny on 2018-11-24
While connected to your Kubuntu system run command ```
sudo fdisk -l
``` to see what that tells us about the partitions and filesystems on the Playstation disk; maybe it uses a filesystem that can not be mounted without installing some other packages.

A search suggests it is a proprietary filesystem used which can not be read by PCs, and whilst PCs usually means Windows or Mac, I suspect you may have to use the USB connection suggested in the info at [https://whirlpool.net.au/wiki/ps3_hdd](https://whirlpool.net.au/wiki/ps3_hdd)

---

### Post by e-zombiehero on 2018-11-24
Thank you for the suggestion, unfortunately I booted up the laptop today and an error I had been receiving, that I mentioned in a different post, seems to have bricked the device.

---

### Post by SeijiSensei on 2018-11-25
Playstations use a proprietary, encrypted format that Linux cannot read.

---

