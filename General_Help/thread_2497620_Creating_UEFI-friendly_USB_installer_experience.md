---
title: "Creating UEFI-friendly USB installer experience"
date: 2024-05-12
forum: General Help
---

### Post by currentshaft on 2024-05-12
1

---

### Post by BBQdave on 2024-05-12
This is the current recommended method to create a bootable USB Stick for Ubuntu: [https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

---

### Post by oldfred on 2024-05-12
I do not like dd as we see too many users specify wrong device & destroy data on drive they really want to keep. And of course those users never have backups.

Many have suggested all of these:
balenaEtcher, rufus, & Startup Disk Creator
mkusb
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) 
Some of above are dd with some extra questions to make it a bit safer.
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

If only UEFI boot required, you can just extract ISO into a FAT32 formatted flash drive with esp,boot flags.
I created a temp partition (sdb2) as ESP on a much larger drive where I did not want dd to erase it.
```
sudo apt-get install p7zip-full
p7zip Note no space after -o 
7z x [ISO_NAME]  -o[DESTINATION_FOLDER]
sudo mkdir /media/fred/temp
sudo mount /dev/sdb2 /media/fred/temp
sudo 7z x ~/ISO/kubuntu-22.04.1-desktop-amd64.iso -o/media/fred/temp
sudo umount  /media/fred/temp

```

But I normally use grub2's loop mount to boot ISO in my ISO folder. I have multiple ISO and do not then have to create a flash drive for separate partition for each.
ISO boot & link to examples
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
more examples
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
Originally getting path & boot parameters correct were the biggest issues.

---

### Post by currentshaft on 2024-05-13
2

---

