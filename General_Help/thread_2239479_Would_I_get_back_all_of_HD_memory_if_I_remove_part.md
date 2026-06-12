---
title: "Would I get back all of HD memory if I remove partitioned-Ubuntu from my Windows 32-b"
date: 2014-08-14
forum: General Help
---

### Post by prajithpillai on 2014-08-14
I've a system with this configuration : 
- Dell Vostro 1015 laptop built Sept 2011 
- Intel Core2 Duo processor @ 2 Ghz frequency 
- 64-bit memory 
- 320 GB HDD 
- integrated graphics 
- WiFi & bluetooth enabled 
 
I'm currently using Windows 7 Ultimate OS since I bought it. I'm fed up  of using Windows 7 on my system (& Windows 8 wont work !) so I  wanted to install Ubuntu 12.04. 
I've 2 questions : 
 
- If I install it in partition with my current OS, and then after some  time, if I need to remove Ubuntu from the system (without removing  windows), will I get back all the HDD memory used by the Ubuntu OS and  make it accessible to the Windows system (again) ? 
 
- Can I use both the Operating Systems in such a way that I can access  the hard disk data equally among both the OSes, that is, I can access  the same HD data by both the OSes ? 
 
(P.S. : I don't want to use Virtual OS software) 
 
Thanks in advance ! ;)

---

### Post by prajithpillai on 2014-08-14
I've a system with this configuration : 
- Dell Vostro 1015 laptop built Sept 2011 
- Intel Core2 Duo processor @ 2 Ghz frequency 
- 64-bit memory 
- 320 GB HDD 
- integrated graphics 
- WiFi & bluetooth enabled 
 
I'm currently using Windows 7 Ultimate OS since I bought it. I'm fed up  of using Windows 7 on my system (& Windows 8 wont work !) so I  wanted to install Ubuntu 12.04. 
I've 2 questions : 
 
- If I install it in partition with my current OS, and then after some  time, if I need to remove Ubuntu from the system (without removing  windows), will I get back all the HDD memory used by the Ubuntu OS and  make it accessible to the Windows system (again) ? 
 
- Can I use both the Operating Systems in such a way that I can access  the hard disk data equally among both the OSes, that is, I can access  the same HD data by both the OSes ? 
 
(P.S. : I don't want to use Virtual OS software) 
 
Thanks in advance ! :)

---

### Post by guccimucci on 2014-08-14
Why would you want to remove Ubuntu? :(

The space on your HDD won't disappear and you can delete the volume from disk management so it'll just turn into unallocated space (then extend it to Windows). It is important to have back-ups as you never know what can get wrong, but the process should be simple. I think that the guide for your question is here: [http://www.lifehacker.com/how-to-uninstall-windows-or-linux-after-dual-booting-508710422](http://www.lifehacker.com/how-to-uninstall-windows-or-linux-after-dual-booting-508710422)

You can share your hard disk equally between the OSes (or any way you want to), but you can not access Windows info from Ubuntu and the opposite.

---

### Post by prajithpillai on 2014-08-14
I don't think I would remove Ubuntu, but, if some problem arises on using Ubuntu, then, what I should do, that's why I asked. 
I meant by my question that can I access the files (which I use in Windows) by using Ubuntu ?

---

### Post by mörgæs on 2014-08-14
Why do you want Ubuntu 12.04 and not 14.04.1?

---

### Post by ian-weisser on 2014-08-14
> **prajithpillai said:**
> If I install it in partition with my current OS, and then after some  time, if I need to remove Ubuntu from the system (without removing  windows), will I get back all the HDD memory used by the Ubuntu OS and  make it accessible to the Windows system (again) ? 

Yes. You use Windows' disk manager to recover the former Ubuntu partition.

 
> **prajithpillai said:**
> Can I use both the Operating Systems in such a way that I can access  the hard disk data equally among both the OSes, that is, I can access  the same HD data by both the OSes ? 
 
Yes. Store and access shared data safely in a third data-only (non-Ubuntu, non-Windows) partition, or add-on (USB) storage.
It is unwise to access one OS partition directly from the other OS.  Neither OS expects it, and that can lead to unpredictable results...like  a broken system.

---

### Post by 3rdalbum on 2014-08-14
Use Ubuntu 14.04, not 12.04. You want to be running a recent Ubuntu not one that's two years old.

Yes, you can erase the Ubuntu partitions and merge them back into the Windows partition. Before doing any partitioning, ensure you have a backup of all data.

Ubuntu can access your Windows drive read/write, but Windows can't even read the Ubuntu partition.

---

### Post by coffeecat on 2014-08-14
Threads merged.

---

### Post by oldfred on 2014-08-14
You want to have a good full image backup of Windows and a Windows repairCD or flash drive.
Use Windows to shrink the Windows NTFS partition to make unallocated space for Ubuntu. And reboot so it can run chkdsk and update to new size. Make sure hibernation is off.
If you have used all 4 primary partitions, you will have to backup and delete a partition, typically the vendor partition is small and easily backed up.
Then you can install Ubuntu. Default install is just / (root) and swap, but as suggested above much better to create a shared NTFS data partition and set Windows as read/only.

       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)

 [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
[/URL]
 Lots of detail, screenshots and essential info.14.04  Something Else example
[URL="http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html"]http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html
[/URL]
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
    [URL="http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html"]
[/URL]

[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by prajithpillai on 2014-08-14
My system is a Dell Vostro 1015. And as far as I know, my system would support only Ubuntu 12.04 LTS and not any other Ubuntu higher than that. That's why, I asked for Ubuntu 12.04 LTS and not any other Ubuntu.

---

### Post by sotiris2 on 2014-08-14
What makes you say so? In fact I think 14.04 is a bit more responsive than 12.04 on the same hardware. I will also insist you make backups of your data and make the windows 7 repair disk. Unistalling an OS isn't as simple as unistalling a program but if you are prepared before rushing in you will have no problems.

---

