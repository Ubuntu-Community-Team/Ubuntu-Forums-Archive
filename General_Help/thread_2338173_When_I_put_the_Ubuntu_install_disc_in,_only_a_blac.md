---
title: "When I put the Ubuntu install disc in, only a black screen comes up?"
date: 2016-09-25
forum: General Help
---

### Post by tornado711 on 2016-09-25
I recently decided to install linux onto my old laptop. I started with Fedora, which installed just fine, then I tried ubuntu. With Ubuntu, all that happens is I hear my disc drive whirring like it's reading it, the screen is black for a bit, then it just skips straight to booting back into windows. I've experience this same issue with other variants of Ubuntu such as Kali Linux. I've searched high and low but the only related problem I can find is when people try to install it and it returns a black screen. The problem I can't even get into the install menu in general, as when I boot up my computer it's just a black screen for a bit, then it goes right to windows! I'll post some info about my computer below if it helps:

Boot load order has been organize to boot disc first
CD-ROM booting is enabled
Secure boot is disabled
Legacy boot is disabled 
Boot protocol: Ipv4+Ipv6

Specs:
Laptop type: HP Star Wars Special edition 15.6''
GPU: GeForce 940m
Processor: I7 6500u
RAM: 8GB

---

### Post by oldfred on 2016-09-25
With nVidia you often need nomodeset.
Are you getting grub menu to install? If getting BIOS screen you probably are in wrong boot mode, you want UEFI, if Windows is installed in UEFI.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132

      [/URL]
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
If UEFI a lot more info in link in my signature.

---

### Post by tornado711 on 2016-09-25
> **oldfred said:**
> With nVidia you often need nomodeset.
Are you getting grub menu to install? If getting BIOS screen you probably are in wrong boot mode, you want UEFI, if Windows is installed in UEFI.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132

      [/URL]
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
If UEFI a lot more info in link in my signature.


No, I don't get any menu, I don't even have the grub bootloader installed yet either. I literally put the disc in and have it boot the disc, and it's nothing but black screen, like the light of the screen comes on and it's just black, that's it, absolute nothingness, but I hear the disc drive whirring. I don't understand why it's doing this but it only seems to be doing it for Ubuntu variants, it loads stuff that isn't Ubuntu like Fedora 25 just fine, however anything in Debian Ubuntu it refuses to load. I don't have grub installed at all, I was going to install it in the Ubuntu installer. So currently, I just have the regular windows bootloader. Also, I have legacy boot disabled with IPV4+IPV6 boot protocol, that would mean it's in UEFI correct? Also, I should have secure boot disabled or enabled for this process? Currently as a temporary fill in for Grub I'm using the fedora bootloader if that helps at all.

EDIT: I did some research turns out my Windows is installed as EFI if that helps, or is EFI the same thing as UEFI?

---

### Post by oldfred on 2016-09-25
Actually EFI is what Apple Macs used. With, I think version 2 it became UEFI and that was the version used by Windows 8 systems.
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)

You should get one of the two screens shown, or else I would expect that you do not have a good ISO or a good install to flash drive.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[URL="http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html"]http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html

[/URL]
 Ubuntu UEFI install ISO
Also links on how to create a bootable DVD or USB flash drive, from Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Easy way to create UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 

[URL="http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html"]
[/URL]

---

### Post by tornado711 on 2016-09-26
> **oldfred said:**
> Actually EFI is what Apple Macs used. With, I think version 2 it became UEFI and that was the version used by Windows 8 systems.
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)

You should get one of the two screens shown, or else I would expect that you do not have a good ISO or a good install to flash drive.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[URL="http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html"]http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html

[/URL]
 Ubuntu UEFI install ISO
Also links on how to create a bootable DVD or USB flash drive, from Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Easy way to create UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 

[URL="http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html"]
[/URL]

The thing is, i've downloaded ubuntu and the other distro linuxes 3 different times and it just doesn't want to work. I'm using active ISO burner to burn to discs, i've even used mxpburner as well. I have no clue what could be causing this or why it would happen! I'm completely clueless on what else could have caused this! I've even tried different discs yet they still refuse to work! Also that link on how to create a bootable dvd or usb flash drive is broken. I don't think I'm burning it wrong because I've burned it from fedora back to ubuntu twice and fedora would still work everytime I burned it back!

---

### Post by Geoffrey_Arndt on 2016-09-26
Verify iso integrity (checksum match).   Make sure you're using a standard clean DVD and burning it at 4x or 8x (low burn speed).

---

### Post by tornado711 on 2016-09-26
> **Geoffrey_Arndt said:**
> Verify iso integrity (checksum match).   Make sure you're using a standard clean DVD and burning it at 4x or 8x (low burn speed).

How do I verify integrity of the ISO? Would I need to do that in say a command terminal? Sorry for this very newbie question but google isn't giving me very straight forward answers!

---

### Post by oldfred on 2016-09-26
Ubuntu UEFI install ISO
Also links on how to create a bootable DVD or USB flash drive, from Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

You use md5sum to verify ISO.
Some flash drives and some USB ports just do not work. Have you tried several?

You mention older laptop? How old.
Full Ubuntu requires a bit newer system, which some may say is still older and still works. 
Any system with Windows 8 originally will work, and many newer ones with Windows 7 should work.
Windows 8 release date: October 26, 2012. 

But older systems really need Lubuntu or Xubuntu which uses a lighter weight GUI/desktop.
        Current Releases & Flavors
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)
Kubuntu, Edubuntu, Xubuntu, Mythbuntu, UbuntuStudio, Lubuntu, Ubuntu GNOME, Ubuntu Kylin, Ubuntu MATE 
[http://xubuntu.org/](http://xubuntu.org/)
[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by tornado711 on 2016-09-26
> **oldfred said:**
> Ubuntu UEFI install ISO
Also links on how to create a bootable DVD or USB flash drive, from Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

You use md5sum to verify ISO.
Some flash drives and some USB ports just do not work. Have you tried several?

You mention older laptop? How old.
Full Ubuntu requires a bit newer system, which some may say is still older and still works. 
Any system with Windows 8 originally will work, and many newer ones with Windows 7 should work.
Windows 8 release date: October 26, 2012. 

But older systems really need Lubuntu or Xubuntu which uses a lighter weight GUI/desktop.
        Current Releases & Flavors
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)
Kubuntu, Edubuntu, Xubuntu, Mythbuntu, UbuntuStudio, Lubuntu, Ubuntu GNOME, Ubuntu Kylin, Ubuntu MATE 
[http://xubuntu.org/](http://xubuntu.org/)
[http://lubuntu.net/](http://lubuntu.net/)

I doubt it's the disc drive as it loads fedora and redhat based linuxes just fine, it's only specifically ones running off a Debian Ubunut type that don't. Also, if I said my laptop was old that was a mistake, my bad! It's very new, in fact it was made last year. I'm sure it can run it because my last computer (an HP pavilion from 2008 which was 1/4 as powerful as this computer), ran all the linux platforms perfectly fine, so I don't think it could be that. It came with Windows 10 pre-loaded on it as well. Also, MD5checksum, I run that through the command terminal in my current working Fedora linux correct? Thank you so much for all you help so far by the way! Again if you're referring to the command terminal  in GRUB I don't have it installed. I can't even get ubuntu to boot into the disc like I cannot even get the install menu. I have 0 access to anything linux, unless I can use md5cheksum in fedora.

---

### Post by Geoffrey_Arndt on 2016-09-27
OK, so a newer system . . why mess with a slow cd/dvd at all?  Get a 4 gib or larger usb flash-stick and use the program "Etcher" to convert the ISO from your Hard Drive to the USB as a bootable device.    Look to your efi startup/setup screens to find how to select the usb stick to boot the PC.  

 On my System76 Galago Laptop it's just by pressing the F7 key, I get a popup window that provides a short menu of disks (sda, sdb, sansa) to boot from - highlight your selection and press enter to start the boot system.   You do have something similar on your system (sometimes called the "one time boot" option or "custom boot option).

---

### Post by tornado711 on 2016-09-27
> **Geoffrey_Arndt said:**
> OK, so a newer system . . why mess with a slow cd/dvd at all?  Get a 4 gib or larger usb flash-stick and use the program "Etcher" to convert the ISO from your Hard Drive to the USB as a bootable device.    Look to your efi startup/setup screens to find how to select the usb stick to boot the PC.  

 On my System76 Galago Laptop it's just by pressing the F7 key, I get a popup window that provides a short menu of disks (sda, sdb, sansa) to boot from - highlight your selection and press enter to start the boot system.   You do have something similar on your system (sometimes called the "one time boot" option or "custom boot option).

I've already done half of what you said. When the problem had first happened, I tried a direct booting option, as my BIOS had an option to select the boot device and boot directly into that, and it still just gave a me a black screen. I have CD-ROM boot enabled and I've made sure the boot order is organized. I don't think the problem is that the computer is skipping past booting the CD, I think it's just that it doesn't want to boot the CD because even when using the BIOS to direct boot into the DISC, I still got a black screen. I'm still baffled as to why FEDORA and redhat linuxes work but Debian ones won't. I'm going to try to find my old flash drive to see if maybe that makes a difference, I just hope I find a solution for the CD problem though, because I prefer to store all my linux distros on discs.

---

### Post by oldfred on 2016-09-27
Is it really a CD or a DVD. Ubuntu does not fit on a CD anymore.
That is why I now prefer flash drives, but I download daily, beta and often different flavors. As well as many other repair ISO like gparted, Knoppix, parted magic, Boot-Repair and others. My stack of CD/DVDs was getting out of hand, so converted to flash drives which then I can at least copy newer version over older one.

---

### Post by Geoffrey_Arndt on 2016-09-27
Yes, the problem is not the media (optical disk, usb-flash-stick).   The black screen is almost certainly a gpu/drivers issue.   

Fedora etc. must default in the basic install to a vesa or generic driver that will run the X windows system.   In the Debian family of distros , , , you'll have to modify the boot-up process with parameters such as "nomodeset" which will give you a lower resolution (and slower) graphics stack and then you have to install the proprietary driver (amd/ati), (nvidia).

How to do "nomodeset"


   1).   For a PC with no other operating system - the Grub2 menu will NOT be displayed by default, so:
>     Hold down (right) SHIFT to display the menu during boot. In certain cases, pressing the ESC key may also display the menu.  
   If you are able to boot with this parameter, you can install a graphics driver from the "Additional Drivers" utility in the actual install.


   [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) <- How to set NOMODESET and other kernel boot options in grub2 
   [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) <-nomodeset option in detail
  
[https://help.ubuntu.com/community/PopularPages](https://help.ubuntu.com/community/PopularPages) 


One way how to install the drivers:
[URL="http://www.yourownlinux.com/2015/04/how-to-install-nvidia-346-59-stable-graphics-drivers-in-linux.html"]
http://www.yourownlinux.com/2015/04/how-to-install-nvidia-346-59-stable-graphics-drivers-in-linux.html[/URL]

---

### Post by tornado711 on 2016-09-27
> **oldfred said:**
> Is it really a CD or a DVD. Ubuntu does not fit on a CD anymore.
That is why I now prefer flash drives, but I download daily, beta and often different flavors. As well as many other repair ISO like gparted, Knoppix, parted magic, Boot-Repair and others. My stack of CD/DVDs was getting out of hand, so converted to flash drives which then I can at least copy newer version over older one.

The specific type is 'DVD-RW', it just seems very weird to me that specifically Ubuntu versions of linux don't work. Any redhat will work but Ubuntu versions even ones from older versions such as Kali Linux just refuse to work. I might try a USB flash drive but it still boggles me why something like the latest version of Fedora will work perfectly fine on a plain old disc!

EDIT: I found my 120gb thumb drive. I burned Kali onto it with UUI, and it boots fine on my desktop, however it seems to skip over it on my laptop like it doesn't exist. I'm trying to find out how I can direct boot it. For example, in my desktop bios, I can select the device and directly boot into that. I'm trying to figure out how I could do that on my laptop, as it has a default HP bios.

---

### Post by oldfred on 2016-09-27
What model HP?

HP should boot flash drive ok, but once installed HP is not UEFI dual boot friendly.
They violate UEFI spec and use description as part of boot and that description is "Windows Boot Manager". But there are multiple work arounds, depending on configuration on which may be better.

But UEFI boots /EFI/Boot/bootx64.efi on all external devices and is the fallback or hard drive entry for internal drives. HP often has an entry for that, but the file bootx64.efi is just another copy of Windows efi boot file. One work around is to make that be shimx64.efi to boot Ubuntu. But you have to have installed before that change works.

---

### Post by tornado711 on 2016-09-27
> **oldfred said:**
> What model HP?

HP should boot flash drive ok, but once installed HP is not UEFI dual boot friendly.
They violate UEFI spec and use description as part of boot and that description is "Windows Boot Manager". But there are multiple work arounds, depending on configuration on which may be better.

But UEFI boots /EFI/Boot/bootx64.efi on all external devices and is the fallback or hard drive entry for internal drives. HP often has an entry for that, but the file bootx64.efi is just another copy of Windows efi boot file. One work around is to make that be shimx64.efi to boot Ubuntu. But you have to have installed before that change works.


Well, I have the bootloader version of GRUB that Fedora uses installed, I had to manually set it to take priority over the windows bootmanager though which was annoying. I installed the Fedora linux onto the USB to see if that would boot it and it did just fine, but the computer in general refuses to boot the Ubuntu one. My laptop is an HP Pavilion star wars special edition laptop: [URL="http://www.bestbuy.com/site/hp-star-wars-special-edition-15-6-laptop-intel-core-i7-8gb-memory-1tb-hard-drive-darkside-black/4563805.p?skuId=4563805"]http://www.bestbuy.com/site/hp-star-wars-special-edition-15-6-laptop-intel-core-i7-8gb-memory-1tb-hard-drive-darkside-black/4563805.p?skuId=4563805
[/URL]

EDIT: The thumb drive is out of the question, I put it on my desktop just to install linux on there for now, only to realize that this thumb drive has a bad block in it.......just my luck.

EDIT 2: I fixed it! I stopped using UUI as my usb installer for my thumb drive. Instead, I used POWERISO to burn to the USB and that made it start working, so I was able to get Ubuntu on both my desktop and laptop. Thank you everyone for the help!

---

