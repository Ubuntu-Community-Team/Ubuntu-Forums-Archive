---
title: "xbmcbuntu lost simple dual boot"
date: 2014-09-22
forum: General Help
---

### Post by barry7 on 2014-09-22
total noob here so bear with me i only know enough to be dangerous which why im here. i removed the old hard drive from wifes old netbook swapped into mine and loaded xbmcbuntu on it as a clean install full windows wipe. removed and placed into a external case. and re installed original windows 7 starter hard drive to computer. setup boot sequence from bios to run from usb first then internal hard drive. no external plugged in straight to windows. external plugged in straight to xbmcubuntu. so now the problems i backed out of xbmc to terminal ran an sudo apt get to an update to ubuntu. thats when grub came into play now unless i have the external plugged in i can no longer boot straight to windows. i want the ability to seperate the 2 systems back out. no windows disk to use no disk drive since its a netbook any help would be great.

---

### Post by CantankRus on 2014-09-22
Sounds like you wrote grub to the mbr of the windows 7 disk.
I suggest you use [**_[COLOR="#B22222"]Boot-Repair[/COLOR]_**]("https://help.ubuntu.com/community/Boot-Repair")
to create a bootinfo summary to help diagnose and fix.

---

### Post by grahammechanical on 2014-09-22
My guess is that the BIOS is seeing the Ubuntu drive not as a USB stick but as a removable hard drive. And therefore, the boot priority settings are being ignored. That is what happens on my machine. I have two HDs and I can use the BIOS to change which HD loads and if I plug in a USB stick with Ubuntu installed I have to use the same BIOS option to tell the machine to load from the removable drive instead of either hard disk. It is like having 3 hard disks. The setting for boot priority is ignored except for CD/DVD.

You are in the situation of having 2 hard disks and not one hard disk and a USB stick. Boot Repair will solve this by installing Grub into the MBR of both hard disk.

If Grub was in the MBR of the windows disk then you would have an option to load Windows. It seems that Grub only loads when the external disk is plugged in. And that is when you get a menu that includes Windows 7. And the BIOS is set to load from the external hard drive. It occurs to me that there may be a setting in the USB section of the BIOS that be a solution.

Regards.

---

### Post by barry7 on 2014-09-22
Getting late will get and run the boot loader tomorrow and post an update thank you both for the responses.

---

### Post by barry7 on 2014-09-24
Well as usual i broke it super broke don't ask how i don't know. So down loading and making a win 7 recovery usb to reset the system. After i will do another hard drive swap and clean install of xbmcubuntu yeah kind of caveman tactics but if it work so be it. All info worth keeping has been already placed on a external hd used only for media purposes

---

