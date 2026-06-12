---
title: "Startup Disk Creator..."
date: 2018-05-11
forum: General Help
---

### Post by ddenney on 2018-05-11
Hello. I'm needing to know how to burn a Windows 10 .iso to a thumbdrive using either Xubuntu or Ubuntu MATE. I currently can't boot up Windows, so I need to reinstall it, and I have the .iso on my Xubuntu partition. I also have Ubuntu MATE, if that makes a difference. I'm very familiar with *Startup Disk Creator*, but it will only burn Ubuntu flavors to a USB thumbdrive. If it's possible in Terminal, please explain the commands. Thanks.

DDenney

---

### Post by yancek on 2018-05-11
Why not just burn it to a DVD in the standard manner?  If you want to create a bootable windows iso which you can boot from Grub on your installed system, first navigate to the directory where the windows iso file is stored and right click it and select Disk Image Mounter and mount it.  If you get an error saying the iso is too large, you will need to do it manually which involves first creating a mount point, second doing a loop mount of the iso to the mount point and then copying the files to the usb and creating a proper boot entry in the Ubuntu grub.cfg menu.  Because you have Ubuntu and Grub already installed, there is no point in going through the process of installing it to the usb as explained at the link, just skip those steps.  This is all explained in detail at the link below.

  [http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by ddenney on 2018-05-11
Very good info and link w/video. Thanks!

---

