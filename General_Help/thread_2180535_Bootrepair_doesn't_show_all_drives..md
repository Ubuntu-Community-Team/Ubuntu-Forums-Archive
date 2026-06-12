---
title: "Bootrepair doesn't show all drives."
date: 2013-10-13
forum: General Help
---

### Post by Yensa_Reyes on 2013-10-13
Hey guys, I'm trying to change the default partition from which to load. This is something I've done before, but this time around Boot Repair doesn't show sdb1 which is the one I want. How do I get it to show up in Boot Repair? Any pointers would be really appreciated.

---

### Post by oldfred on 2013-10-13
From grub can you boot into sdb1? You can easily just install grub to sdb from that.
       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

If not post link to the BootInfo report from Boot-Repair.

---

### Post by Yensa_Reyes on 2013-10-13
Thanks for answering. I tried that right from BootRepair. It's different if I do it in a terminal? Also, I'm trying to make windows be the default selection when booting. sdb1 in my case is win7. Does it matter in any way that I install in the same place?

---

### Post by oldfred on 2013-10-14
If you have multiple drives and Windows in sdb, do you have the Windows boot loader in sda or in sdb1? Often when installing Windows 7 to sdb, it installs its boot loader to a 100MB hidden partition on sda and sets it boot loader into the MBR of sda. That is because most systems have BIOS default boot set to sda.
If all of Windows boot files are in sdb1 then you can install your Windows boot loader to the MBR of sdb. You can use Boot-Repair. Just turn off auto update and check update MBR. Then in advanced settings choose Windows in sdb1 and install boot loader to sdb.

If not post link to BootInfo report.

---

### Post by Yensa_Reyes on 2013-10-14
I'm pretty sure it's the way you just described, I haven't made changes to the BIOS default settings. I want to make sure I do this right so here's the bootinfo report [http://paste.ubuntu.com/6231946/](http://paste.ubuntu.com/6231946/) 

I remember the first time I did this there were two options, one took me to win boot menu and the other directly to win7, which I prefer. Thanks again

---

### Post by oldfred on 2013-10-14
It looks like you have an old XP install in sda3, but it is missing boot.ini but also has the boot files for Windows 7. You also have all the boot files  in sdb1. Then you should just be able to install a Windows boot loader to sdb and set BIOS to boot sdb and directly boot into Windows 7. If updated BCD was in sda3 then your sdb1 BCD may need updating or repairs.

       Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

You are also showing /grldr in sdb1. That is grub4dos and is usually installed as part of EasyBCD. If not using EasyBCD you can just delete it.

If you set BIOS to boot sda, then the grub menu should give you the choice of Windows or Ubuntu.

---

### Post by Yensa_Reyes on 2013-10-14
Will I still be able to load Ubuntu that way?

---

### Post by oldfred on 2013-10-14
If you have grub2's boot loader in sdc and set BIOS to boot from the drive that is sdc, then grub will give you a choice of Ubuntu or Windows.
If you want to directly boot Windows you can use one time boot key (f12) on my system or change BIOS boot order to boot sda.

---

