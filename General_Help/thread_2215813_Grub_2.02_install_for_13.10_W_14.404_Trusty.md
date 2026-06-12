---
title: "Grub 2.02 install for 13.10 W/ 14.404 Trusty"
date: 2014-04-08
forum: General Help
---

### Post by Redalien0304 on 2014-04-08
is Grub 2.02~beta2-8 Recommended for Ubuntu 13.10? Also have Ubuntu 14.04 Trusty Installed. grub-install -V shows that i have grub 2.02~beta2-8 Installed on Ubuntu 14.04 Trusty. grub-install -V on 13.10 gives me "Unrecognized option `-V' Usage: grub-install [OPTION] [INSTALL_DEVICE]
Install GRUB on your drive." Any help is appreciated thanks.

---

### Post by oldfred on 2014-04-08
You actually only boot with one grub in BIOS/MBR systems.

Usually last system installed has its grub in MBR. 
If 14.04 is first in grub menu then that is the version you are using to boot and it should also offer to boot your 13.10.

If you want the grub in 13.10 in control you can from booting your 13.10 install, then install grub2's boot loader to MBR, so that version of grub is in control. Then 13.10 should be in control and first in grub menu and it should add 14.04 to menu with a sudo update-grub.

But each install may overwrite MBR on a major grub update. Each remember default install drive and uses that if it thinks it needs to reinstall.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

Check default in each install and change the one you use less to not reinstall automatically.

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by Redalien0304 on 2014-04-08
ok thanks oldfred for the Info. now this also means if you use Boot-repair does that mean Boot-repair is out of date till newer Version now?

---

### Post by oldfred on 2014-04-08
I have not tried Boot-Repair with 14.04 yet. Some reported it did not install.

You can always run this just to get info, but it does not do fixes.
This is actually the first part of BootInfo report from Boot-Repair.
 Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

