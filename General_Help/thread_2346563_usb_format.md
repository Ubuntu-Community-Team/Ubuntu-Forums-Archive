---
title: "usb format"
date: 2016-12-16
forum: General Help
---

### Post by pete1977x on 2016-12-16
I have a usb drive that was stuck with data so I used Gparted to reformat. This is a common 4G Sandisk thumb drive. What is the correct format type for this?? I used 32 but I can change that..

---

### Post by howefield on 2016-12-16
If you mean fat32 then the thumb drive will be recognised by most file systems.

There is no "correct" format although fat32 is commonly used. If you only use the thumb drive in Linux then you can format it otherwise, eg ext4.

If this is related to your other thread about creating a Windows bootable USB, you probably need fat32 or at least a "Windows" file system.

---

### Post by pfeiffep on 2016-12-16
[COLOR=#800080]"What is the correct format type for this??[/COLOR]" Almost impossible to answer! What systems do you intend for this to be read? 
What I know:

[LIST]
[*]Sandisk's are shipped with fat32 which has a 4GB file size limitation.
[*]I overcame the 4gig limit by using exfat [rw by Linux, Windows7, Mac]
[/LIST]

---

### Post by sudodus on 2016-12-16
***An msdos partition table with the FAT32 file system is the standard.*** Gparted selects the msdos partition table by default, but you need to set the file system manually.

While doing it, you can also create a **label**, which makes it easier to identify the drive, when it it plugged in and seen by an operating system.

---

