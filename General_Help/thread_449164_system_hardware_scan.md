---
title: "system hardware scan?"
date: 2007-05-19
forum: General Help
---

### Post by Maniac Matt on 2007-05-19
Is there any way to scan my computer for hardware? 

I recently switched this hard drive to this computer from another one, and i kept kubuntu on it. There is a problem  that  occurs when i try to use Adept_Installer, and it asks me to put the Kubuntu Feisty Fawn disc into the drive "/cdrom/ . So i put it in the drive, but when i click continue, it keeps asking me to put the Cd into the /cdrom/ drive, so i was wondering if i did a hardware scan, it would pick up the cd drive. 

I am Very new to linux, so I dont know how to do much.

---

### Post by mbradlcu on 2007-05-20
```
lspci
```
will tell you what pci hardware you have.
```
sudo fdisk -l
```
will tell you what drives are listed.
If you're running gnome,, select "system" -> "preferences" -> "Hardware Information" for a gui display.

sometimes programs won't recognize the cdrom supermount,, if you just place a cd in the drive does an icon display on the desktop?

you can manually mount the cdrom device if you'd like with the following command:
```
sudo mount /dev/cdrom /mnt
```

if you don't have /dev/cdrom then the kernel isn't seeing your cdrom device.

have fun!

---

### Post by zvacet on 2007-05-20
```
lshw
```

---

### Post by mbradlcu on 2007-05-21
wow! that's one to add to the play book! thanks!!!

---

### Post by scorpioiscariot on 2008-06-27
[HTML]dmesg[/HTML]
This might be useful for some who need a little more detailed information.

---

