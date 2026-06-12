---
title: "GNU GRUB showing an OS that is not installed"
date: 2014-06-19
forum: General Help
---

### Post by travis21 on 2014-06-19
Hello! 

I have just installed Ubuntu 14.04 without any issues. When turning on my machine for the first time after doing so, I realized the GNU GRUB shows Windows 7 listed as an option to boot to. The odd thing about that is I do not have Windows 7 installed on my machine, rather Windows 8.1. Would anyone know a resolution to remove this from the list? I have attached a picture of what I am trying to explain. Thanks!

---

### Post by yancek on 2014-06-19
The image you posted shows windows 8 on the first partition of the second drive.  The windows 7 is the first partition on the third drive.  What do you have on the third drive?  Did you previously have windows 7 installed?  If all you want to do is remove the entry from the boot menu and you don't have windows 7 anywhere, running sudo update-grub should do it.  Or you could delete the entry from the /boot/grub/i386-pc/grub.cfg file.

---

### Post by oldfred on 2014-06-20
Grub2's os-prober looks for NTFS partitions with the files bootmgr and /boot/BCD as those are the Windows Vista/7/8 boot files in BIOS mode.

Do you have those files in a partition in sdc1?

Windows also uses a boot flag or active partition to know which partition to boot from. But BIOS sets which MBR/drive to boot from and then boot loader in MBR looks for bootable partition. 
Grub does nto use boot flag, but has info internally to know partition to boot from on any drive.

---

### Post by travis21 on 2014-06-20
I previously had Windows 7 installed on the same partition that Windows 8 is now installed on. I have three drives total; one SSD (which has Windows 8 on it now), and two disk drives. I'm not sure if something happened when I recently installed Windows 8 (overwriting Windows 7), but I do not have Windows 7 installed on any drive. I will run sudo update-grub command when I get home. Will deleting that config file hurt anything? And would you happen to know if there is something I am supposed to do in Windows? Thanks for the help!

---

### Post by oldfred on 2014-06-20
Both Windows 7 and Windows 8 create a separate 100MB boot partition on the drive specified as boot in BIOS. So if you install c: drive to sdb, and BIOS says to boot from sda, then you get a 100MB boot partition on sda.
So do you still have another 100MB boot partition somewhere. 
Windows will install to one partition if it exists in advance as NTFS primary partition with boot flag and same drive is boot in BIOS.

---

