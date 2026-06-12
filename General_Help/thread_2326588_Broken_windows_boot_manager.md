---
title: "Broken windows boot manager"
date: 2016-06-02
forum: General Help
---

### Post by Daniel_Schechtman on 2016-06-02
Hello

I deleted Linux from my computer. But I missed a step and turned off my computer without fixing Windows boot manager. When the computer loaded up, it showed a black GNU GRUB screen with some text on it. Is there any way I can fix this?

Thanks

---

### Post by yancek on 2016-06-02
Use your windows installation DVD and select the repair option.  You don't indicate which version of windows you are using so it's difficult to be more specific.

---

### Post by ajgreeny on 2016-06-02
We also need to know if it is using UEFI or BIOS.

---

### Post by Daniel_Schechtman on 2016-06-02
With the information below, is using window media installation all I need to do?

---

### Post by Daniel_Schechtman on 2016-06-03
I am using Windows 10 with UEFI.

---

### Post by oldfred on 2016-06-03
With Windows 10, if preinstalled with UEFI, you just need to go into UEFI and change boot order to boot Windows.
Or use one time boot key like f10 or f12, check manual to choose to boot Windows.

With UEFI all boot loaders are in the ESP, efi system partition. 

If you want to houseclean totally you have to remove the /EFI/ubuntu folder in the ESP and the grub entries in UEFI's NVRAM.
[http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743)

 mount the ESP with `mountvol b: /s` in Windows

---

### Post by Daniel_Schechtman on 2016-06-03
I can't repair Windows like instructed because when I turn on my computer, this is the first screen to come up

[https://drive.google.com/open?id=0B6bFGw0RdTbLd2ZVOEVXZUh3dDQ](https://drive.google.com/open?id=0B6bFGw0RdTbLd2ZVOEVXZUh3dDQ)

If I wasn't clear before, I apologize. What I did was delete the partition containing Ubuntu from my hard drive. Then a little while later I turned it off. When I tried turning it back on again it showed that screen, and I am trying to get Windows to boot normally.

---

### Post by oldfred on 2016-06-03
Ubuntu is still the first item to boot in UEFI.
You just have to change the first item to Windows.

If you have the Ubuntu live installer, you can also change boot order with efibootmgr.

       sudo efibootmgr -v  

 Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)
sudo efibootmgr -o 2,1
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

### Post by Daniel_Schechtman on 2016-06-03
I'm sorry, I am new to all this stuff. I already have a Ubuntu bootable usb (the same one that I used to install Ubuntu in the first place). How do I use that to switch which os will be booted first from the screen that I shown?

---

### Post by oldfred on 2016-06-03
Post #8 has details.

From live installer post the output of 
sudo efibootmgr -v

---

