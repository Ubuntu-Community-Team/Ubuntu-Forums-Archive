---
title: "Lubuntu or Ubuntu on laptop?"
date: 2016-05-07
forum: General Help
---

### Post by Voylin on 2016-05-07
Hey guys, At the moment I have a HP Stream 11 because it is a cheap and lightweight laptop. 
   	But in windows it can be quite laggy sometimes. 
   	  
   	I was wondering if it would be possible to install Lubuntu or Ubuntu on  my HP stream, or will I have problems with my keyboard, trackpad, sd  card reader, Wifi, and other driver related stuff? 

   	Also can I install lubuntu or ubuntu on my external ssd because the  main storage only has 10 GB left. And when installing, won't I have  problems if it defragments my ssd because it isn't healthy for an ssd xs

	And what would you advise for the laptop I have, Ubuntu or Lubuntu? 

It is mainly because I like ubuntu more but I still want to be able to have windows on my laptop. I use wevideo for my video editing that I do while travelling and Ubuntu and Lubuntu consume less and are for me as easy to use as windows.

---

### Post by grahammechanical on 2016-05-07
I am not familiar with the hardware specification of that machine. Amount of RAM? Video adapter & amount of video memory? BIOS or UEFI boot system? Version of Windows? So, I cannot advise you.

> will I have problems with my keyboard, trackpad, sd  card reader, Wifi, and other driver related stuff?

Lubuntu is built on Ubuntu and Ubuntu uses the Linux kernel. So, if Ubuntu has problems with hardware compatibility so will Lubuntu. As a general rule the latest hardware requires the latest Linux kernel which is in the latest versions of Ubuntu and the latest versions of those "flavours" that are built on Ubuntu.

The Ubuntu/Lubuntu installer does not defrag the hard disk during installation. If you install Linux on a disk with Windows already on it you will have to create space for Linux. That means using Windows tools to defrag the disk and do it more than once making is sure that Windows loads each time. You then use Windows tools to move/resize Windows partitions to create unallocated space that the Ubuntu installer can use to install Ubuntu into.

The installer defaults to putting the Linux boot loader (Grub) on to the first internal disk (sda). So, if you install Ubuntu/Lubuntu to the external disk make sure that the Grub bootloader is being installed on the external disk (sdb).

You can download the ISO image of both Lubuntu & Ubuntu & burn it to a DVD or USB memory stick and run live sessions to test that all the hardware is recognised and that the operating system runs suitably well on that machine.

Regards.

---

### Post by Voylin on 2016-05-07
> **grahammechanical said:**
> I am not familiar with the hardware specification of that machine. Amount of RAM? Video adapter & amount of video memory? BIOS or UEFI boot system? Version of Windows? So, I cannot advise you.



Lubuntu is built on Ubuntu and Ubuntu uses the Linux kernel. So, if Ubuntu has problems with hardware compatibility so will Lubuntu. As a general rule the latest hardware requires the latest Linux kernel which is in the latest versions of Ubuntu and the latest versions of those "flavours" that are built on Ubuntu.

The Ubuntu/Lubuntu installer does not defrag the hard disk during installation. If you install Linux on a disk with Windows already on it you will have to create space for Linux. That means using Windows tools to defrag the disk and do it more than once making is sure that Windows loads each time. You then use Windows tools to move/resize Windows partitions to create unallocated space that the Ubuntu installer can use to install Ubuntu into.

The installer defaults to putting the Linux boot loader (Grub) on to the first internal disk (sda). So, if you install Ubuntu/Lubuntu to the external disk make sure that the Grub bootloader is being installed on the external disk (sdb).

You can download the ISO image of both Lubuntu & Ubuntu & burn it to a DVD or USB memory stick and run live sessions to test that all the hardware is recognised and that the operating system runs suitably well on that machine.

Regards.
  
It only has 2 cores, 1,6Ghz, 2GB ram, intel HD graphics

---

### Post by DuckHook on 2016-05-07
> **Voylin said:**
> ...in windows it can be quite laggy sometimes...> It only has 2 cores, 1,6Ghz, 2GB ram, intel HD graphicsIf it is already laggy in Windows, you will not enjoy the experience in Ubuntu. Best to stick with Lubuntu. You could also try Xubuntu or Ubuntu-Mate. All are much lighter than Ubuntu.

To see if your peripherals will all work, try out each flavour as a LiveUSB. If no problems in LiveUSB mode, then it should work likewise once installed.

---

