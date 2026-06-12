---
title: "extra windows 8 loader being detected in grub"
date: 2013-10-27
forum: General Help
---

### Post by ShinigamiH4ck3r on 2013-10-27
i recently restored grub using boot repair after messing around with some burg themes on ubuntu 13.10. everything boots and works fine but now im seeing an extra windows 8 loader in grub. below is what i mean
sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 8 (loader) on /dev/sda1
Found Windows 8 (loader) on /dev/sda2

the one detected on /dev/sda1 is windows system reserved partition (the correct loader) and /dev/sda2 is my actual windows install partition (the "fake" loader) anyone know how to fix this?

---

### Post by oldfred on 2013-10-27
So many users did not know that sda1, the 100MB (hidden) Windows Boot partition was essential that they just delete it. 
So just to be safe  Boot-Repair copies your boot files into your main or c: drive. But then grub2's os-prober sees the boot files and creates boot entries for both.
If you have a Windows repairCD or flash drive and/or good backups you could remove boot files from Main install. Or you can turn off os-prober in grub and manually create your own entry in 40_custom.

From this file copy entry you want, you can also edit menu entry if you want better title in grub menu:
gedit /boot/grub/grub.cfg
        
 #Add menu entry to 40_custom
gksudo gedit /etc/grub.d/40_custom
#Turn off prober
gksudo gedit /etc/default/grub
#Add this line
GRUB_DISABLE_OS_PROBER=true
#update grub menu after any change
sudo update-grub

If you add another operating system and want to run the os-prober change to false.

---

### Post by ShinigamiH4ck3r on 2013-10-27
Thanks for the help, but all i did was boot into windows and delete the boot folder in the root directory of the c drive :p Didnt know boot repair just simply copied the boot files, so thanks for telling me that

---

