---
title: "Trying to resize partitions again"
date: 2013-07-08
forum: General Help
---

### Post by sports fan Matt on 2013-07-08
I had deleted 12.04 in order to make a new partition for 13.04 (since I don't like to dualboot more then 2 OS) I got rid of all my partitions so GParted only shows Windows 7.  Think is I still get a grb rescue prompt so it won't boot into W7.  Anything I can try to help boot until I get the disk for 13.04 burned?

---

### Post by 1clue on 2013-07-08
You might want to consider the names of your threads a little better.  You're going to collect people who know about partitioning, not people who know how to fix a Windows dual-boot.

I could help with resizing partitions, but I have no idea how to get your dual boot working.  I haven't done that for over 10 years, not even with two linux partitions.

---

### Post by DeathByDenim on 2013-07-08
By deleting the partitions, you deleted parts of the bootloader. The easiest thing is of course to install 13.04, which reinstates the boot menu like you mentioned.
To restore the Windows 7 bootmanager, you might want to follow the instructions here: [http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)
It tells you how to use the Windows 7 CD to reinstall the Windows bootmanager.

(By the way, I don't know if your computer supports it, but you can also boot from a USB key, which will save you the trouble of burning a CD)

---

### Post by sports fan Matt on 2013-07-08
Point taken :)

---

### Post by Irihapeti on 2013-07-08
sports fan Matt: what did you boot in order to run Gparted?

---

### Post by sports fan Matt on 2013-07-08
Honestly I had forgotten I had a disc of 13.04, which had Gparted.  Everything went smoothly.  Tomorrow I shall install 13.04 so this is resolved :)

---

### Post by oldfred on 2013-07-09
You should have a repairCD or flash drive for the current version of every install you have.

 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Also these tools are useful.
      
 Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

