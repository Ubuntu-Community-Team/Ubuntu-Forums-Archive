---
title: "Can I create a copy of 12.04"
date: 2014-11-19
forum: General Help
---

### Post by bobmac on 2014-11-19
Folks,

I have 12.04 installed on my machine. I also have a disk of 12.04 that was originally downloaded from a mirror site and was used to install 12.04 on my system.

I have a friend that would like to try ubuntu but doesn't want to install it on their machine. Is there any way that I can copy 12.04 from so that I can create a disk or use a flash drive such that 12.04 can be run from that disk or flash drive.

Be grateful for any assistance,

Regards,

Bob

---

### Post by westie457 on 2014-11-19
> [COLOR=#000000] I also have a disk of 12.04 that was originally downloaded from a mirror site and was used to install 12.04 on my system.[/COLOR]


Is this disk a DVD that contains the ISO file?

If so, just let your friend use the DVD.

---

### Post by matt_symes on 2014-11-19
Hi

You can just install it on a USB stick. It'll be slow though.

Another option is to create a live USB so they can use it in a live session. Obviously they'll lose any changes when they exit the live session.

A third option is to install it to an external hard drive if they have a spare or you are feeling generous. You can set that up yourself for them. Just make sure to install grub to the external drive and then your friend will need to change the boot order to boot it.

if installing to an external hard drive or USB, gpt vs mbr may or may not be an issue.

Kind regards

---

### Post by bobmac on 2014-11-19
Westie457,

My disk has a folder named isolinux that contains files with .hlp, .fnt, .tr, cat files among others. It does not contain any files that look executable.

Under a folder named ubuntu there is an executable file named wubi.exe. It also has a file named autorun.inf that contains the following

[autorun]
open=wubi.exe
icon=wubi.exe,0
label=Install Ubuntu

[Content]
MusicFiles=false
PictureFiles=false
VideoFiles=false

When I try the wubi.exe file, it only asks if I want to install ubuntu. It doesn't seem to allow me to run ubuntu from the disk.

Bob

---

### Post by oldfred on 2014-11-19
Do not run wubi, it is being discontinued.

You do not run live system from inside Windows, you have to reboot and with BIOS or UEFI choose to boot flash drive.

You can put a full install on a flash drive. Better to use USB3 as even on my old USB2 ports it was 10% quicker.
And you can change some settings to reduce writes which are very slow. If system has a fair amount of RAM, and Linux caches activity in RAM it runs reasonably well. But flash drives have shorter lives than other types of drives.
 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

      
 Full install - C.S.Cameron post #2
[http://ubuntuforums.org/showthread.php?t=2116798](http://ubuntuforums.org/showthread.php?t=2116798)
Full install of 12.04 to 64GB USB device C.S.Cameron post #3
[http://ubuntuforums.org/showthread.php?t=2092077](http://ubuntuforums.org/showthread.php?t=2092077)

It really is just like any install to an external drive. You must use something else as that is the only install option that lets you choose where to install the grub2 boot loader and you want that on the flash drive, often sdb or sdf. All default installs, put grub in MBR of sda, which usually is internal drive.
      
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by bobmac on 2014-11-19
oldfred,

I'm now somewhat confused. I should have mentioned that I'm not much good with all the techo stuff. It's just that I seem to remember when I first downloaded 12.04 from the mirror site that, when I created and inserted the disk I had the option of a sort of demo version as well as being able to install.

What I really meant by a copy was to be able to put the demo on a disk or flash drive so that my friend could run it from their disk drive. I appreciate that anything that was done would not be saved at the end of the session. But that doesn't matter until he makes up his mind whether to install it for real.

Regards,

Bob

---

### Post by yancek on 2014-11-19
> When I try the wubi.exe file, it only asks if I want to install ubuntu. It doesn't seem to allow me to run ubuntu from the disk.

That's all the wubi.exe file is used for.  It installs Ubuntu inside windows as a program which you can delete the way you can delete any program/application.  If you actually have the CD/DVD with 12.04 on it, then you can let your friend use it as a Live CD by selecting the Try Ubuntu option.  If you don't actually have the CD/DVD but only downloaded and installed with wuib, that won't work.  Wubi was designed to be used by people who were interested in testing Ubuntu and was not meant to be used on a permanent basis.  It is also not a standard installation of Ubuntu and as oldfred indicated above, it is not supported any longer.

So if you have the DVD for Ubuntu, loan it to your friend.  If not, you or he can download it and burn it to a DVD or use the appropriate software to put it on a flash drive and run it the same way you do a Live CD/DVD.

---

### Post by bobmac on 2014-11-19
Folks,

I have downloaded the file 'ubuntu-14.04.1-desktop-amd64.iso' to a flash drive from the ubuntu site. I have changed the boot setup to have usb as the first disk. However, no matter which option of usb I try, when I boot from scratch, my system still goes to the installed version (12.04). 

Can someone please tell me where I'm going wrong wrong.

Bob

---

### Post by oldfred on 2014-11-19
The ISO must be extracted & drive converted to be bootable. So you must use tools to install it to a flash drive.

 [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[URL="https://wiki.ubuntu.com/LiveUsbPendrivePersistent"]https://wiki.ubuntu.com/LiveUsbPendrivePersistent
      [/URL] How to create a bootable Ubuntu USB Flash Drive - unetbootin
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

    [       ]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") Note issues with 14.10 and older versions.
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801)
And these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

    [URL="https://wiki.ubuntu.com/LiveUsbPendrivePersistent"]
[/URL]

---

### Post by carl4926 on 2014-11-19
To make a copy of the disk
Insert it in your machine
Open with k3b or Brasero
Copy > Create Image only
You can then burn said image or write to USB

---

### Post by sudodus on 2014-11-20
Maybe the following link and links from it will help you boot your computer and your friends boot their computers from a USB pendrive.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

