---
title: "Vaio usb boot stuck"
date: 2015-02-17
forum: General Help
---

### Post by wouter7 on 2015-02-17
First of all I am not that good in English.
My problem when I use my usb drive(32 gb, 3.0)where I used rufus to get ubuntu on it. It gets stuck on the boot screen when I start my laptop. It stays stuck until I remove the usb and it will then start windows 8.1. 
my laptop= sony vaio SVE1511w1eb
I think I have done everything in the bios(the priority).
I also did this with Kali linux and that had the same results.
I just tried using it on our asus laptop. And it also stays stuck but after 5 seconds it says boot error. So did i forget something or is this usb drive useless as ****. 
Full specs usb: v3 usb drive
Verbatim
32 gb

already thx for the help

---

### Post by oldfred on 2015-02-17
Is your Windows installed in UEFI or BIOS boot mode?
And then are you booting installer in BIOS or UEFI boot mode. 
You want to boot installer in same boot mode as Windows is installed.
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you have the AMD video card/chip, you probably need nomodeset for video issues.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by wouter7 on 2015-02-17
now i am gettting crazy. I was looking for the bios mode in msinfo32. and it says ''verouderd'' that is dutch for oudated............
My laptop was first windows 7 and I upgrade him to windows 8. So what do I need to do???

---

### Post by oldfred on 2015-02-17
Most Windows 7 systems were in BIOS mode, only a few with new hardware just before Windows 8 came out had UEFI but not secure boot.

But most Windows 7 systems with BIOS and MBR partitioning used all 4 primary MBR partitions.

But with Windows 8 you still need to turn off the always on hibernation or fast boot setting.
       WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
If issues you may need these?
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked 
powercfg /h off

      
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by wouter7 on 2015-02-18
Oke I have disabled fast boot with no succes. When I start the latop with the usb in it. It is still stuck on the vaio screen. Pls help, I have search on the internet and couldn't find the answer

---

### Post by wouter7 on 2015-02-18
solved this issue is that my usb is bad as hell. So buy a good usb

---

