---
title: "Uninstalling Windows 7"
date: 2013-01-18
forum: General Help
---

### Post by userfriendly1992 on 2013-01-18
Which one should I do? 

And after I click whichever I need to click, what additional things do I need to do?

---

### Post by oldfred on 2013-01-18
DO NOT UNINSTALL!!

It is saying you have wubi. And even though wubi may be on a separate partition, it uses Windows to boot and is in a NTFS partition. It is not a full partitioned install.

Also we see many users come back later and say they have that one game or app that just does not work in Linux and they want to dual boot. Best to make full backup of Windows. 

And you need a full partitioned install of Ubuntu before uninstalling Windows.

       From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

    
       HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

    
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by userfriendly1992 on 2013-01-18
I have Windows 7 STARTER. I have not downloaded anything. (I just bought this laptop 2 days ago.) I want to be done with windows. How can I get a full installation and how do I do that?

---

### Post by Impavidus on 2013-01-19
Assuming you haven't put anything important yet on your computer, you can put in a live dvd/usb and reboot. You may have to enter the BIOS  to instruct it to boot from dvd or usb. Then you can select "install ubuntu" and when it askes where to install (alongside windows, entire disk or something else), choose "entire disk". This should wipe windows of your disk. Instead, you can also select "something else" to have more manual control over disk partitioning.

---

### Post by oldfred on 2013-01-19
It is up to you if you want to dual boot or just install Ubuntu. If you choose the entire disk option it will also overwrite the recovery partition and unless you have make the recovery set of DVDs will not be able to reinstall Windows.

       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

    
       Install options, Do not use erase entire drive unless that is really what you want.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

