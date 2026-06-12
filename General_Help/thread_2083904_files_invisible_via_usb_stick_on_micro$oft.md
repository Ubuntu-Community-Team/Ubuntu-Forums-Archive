---
title: "files invisible via usb stick on micro$oft"
date: 2012-11-13
forum: General Help
---

### Post by jon zendatta on 2012-11-13
Hi All

JPG files loaded on to USB stick via Ubuntu 12.04 are invisible on Micro$oft box. Why this? I can't test it as we only have Ubuntu at home.:KS

---

### Post by sammiev on 2012-11-13
What format is your USB stick? Likely not NTS or fat32.

---

### Post by gerowen on 2012-11-13
Are other files on the drive visible, and just not the JPG images, or are all files on the drive invisible to Windows?  Does it mount when you plug it into Windows, and just display an empty folder, or does it not even appear in "Computer" at all?  If the drive does not appear at all when you plug it into a Windows machine, it may be formatted in EXT4 or some other filesystem Windows does not recognize.

---

### Post by oldfred on 2012-11-13
Also with flash devices Windows only reads the first partition. Normally if you want Linux format & compatibilty with Windows you have to have the first partition be FAT32 or NTFS, then have any Linux partitions that you want.

Post this - change sda to whatever your flash drive is:

sudo parted /dev/sda unit s print
sudo fdisk -lu

---

### Post by dcstar on 2012-11-14
> **jon zendatta said:**
> Hi All

JPG files loaded on to USB stick via Ubuntu 12.04 are invisible on Micro$oft box. Why this? I can't test it as we only have Ubuntu at home.:KS

Did you correctly use the "Safely Remove Drive" option AFTER all the data had been copied to the USB or were you impatient and just pulled it out?

---

