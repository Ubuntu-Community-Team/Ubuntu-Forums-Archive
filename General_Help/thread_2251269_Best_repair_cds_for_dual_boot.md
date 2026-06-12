---
title: "Best repair cds for dual boot?"
date: 2014-11-03
forum: General Help
---

### Post by mandddam on 2014-11-03
Hi, I have recently been pretty much at hairs end with my ubuntu + windows 7 dual boot system on sony laptop  ](*,)  
This issue had happend before But I fixed with the fix mbr command when I had ubuntu 12.04 and managed to get windows and ubuntu on dual boot with the windows repair disk\\:D/
Now after upgrading to 14 LTS My windows boot stopped working :?. I ignored it as I hardly used windows anyway. But after two months now I need to use solidworks which can only run on windows.:icon_frown: So I tried the Fix mbr again Which removed grub and also left only a windows Which does not even boot!!:confused:    now I dont have ubuntu 14 or windows working. 
Luckily I had all my stuff backed up..and got ubuntu 12 installed from a cd and upgraded to ubuntu14.(again :cry:)...So now I have ubuntu working back at 14 LTS
but not windows.

My question is really simple.
How do I get windows back again now WITHOUT messing up the linux os which i've finally got running again,
Secondly,I intend to get a ubuntu14 live cd now ,
 But Id still like to know the best disks to get since I really dont want to format and reinstall OS'es AGAIN:???: ](*,) 
Can anyone suggest any good recovery disks and options Please. Any help is appreciated,!!!

---

### Post by sudodus on 2014-11-03
Try Boot Repair according to this link

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Mark Phelps on 2014-11-03
MBR problems might not be the ONLY reason that Windows doesn't boot.  You may have to rerun Startup Repair from the Win7 Repair CD several times to fix all the Windows boot problems.  One pass doesn't always work.

---

### Post by oldfred on 2014-11-03
You should always have a repairCD/DVD/Flash drive with a repair or live current version of every operating system you have installed. I also like to have a few others. I used to burn many liveCDs before reinstalling Ubuntu and found most to be a waste as new version was out by the next time I reinstalled. 
I now use flash drives as they are reuseable. And I can put more than one ISO on a flash drive and directly boot with grub2's loopmount.

I actually was able to create a Windows repair flash drive, but convert it to boot with grub. And then in all the extra space added gparted, parted magic, knoppix and Ubuntu ISO. Then I had one flash drive to repair everything.

       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

I did it manually but there now are scripts to semi-automate the install.
      
 These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
[https://sourceforge.net/projects/multibootusb/files/](https://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
[http://ubuntuforums.org/showthread.php?t=2175738](http://ubuntuforums.org/showthread.php?t=2175738)
Uses grub4dos to boot many ISO and other bootable files
[http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1](http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1)

---

### Post by stalkingwolf on 2014-11-03
if it is just a bootloader issue the grub boot repair disk should fix it.

---

