---
title: "Booting from external hard drive"
date: 2016-07-26
forum: General Help
---

### Post by Tom_Carr on 2016-07-26
I installed ubuntu 16.04 on an external hard drive.  There is nothing else on the drive.  I wiped it with the install.
I have 4 old computers running various versions of linux.
On each computer I plugged in the hard drive,  adjusted the bios so the 1st thing it would try to boot from was a usb device, and booted up.
On one computer it worked fine.  This was not the computer I used to install ubuntu to the external hard drive.
On each of the other 3, there were 3 different error messages, but none of them would boot.
On each of the other 3,  if I booted from linux on the internal drive, I could see the external hard drive and read and write to it.

Is this common?  Are there often problems with booting from external hard drives? 

The external drive is a
WD My Passport Essential 500 GB USB 3.0/2.0 Portable External Hard Drive 
[https://smile.amazon.com/gp/product/B0041OSAZI/ref=oh_aui_search_detailpage?ie=UTF8&psc=1](https://smile.amazon.com/gp/product/B0041OSAZI/ref=oh_aui_search_detailpage?ie=UTF8&psc=1)

I could go into more detail about the error messages on the 3 computers where it would not boot, if that would be useful.

---

### Post by oldfred on 2016-07-26
Issues are often video related. 
Or are systems very limited in RAM. Older systems may need Lubuntu or Xubuntu as full Ubuntu with Unity needs newer video capabilities.

Did you install any proprietary video drivers?
Are all systems using same video card/chip?

Have you tried adding nomodeset if nVidia or AMD? or boot the second menu item or grub recovery mode?

And some systems just need different boot parameters in addition to or in place of nomodeset.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown and other boot parameters
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to add boot parameters,  grub menu after install (also grub when UEFI)
[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]https://wiki.ubuntu.com/Kernel/KernelBootParameters

[/URL]
 [https://wiki.ubuntu.com/Lubuntu#System_Requirements](https://wiki.ubuntu.com/Lubuntu#System_Requirements) 

[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]
[/URL]

---

### Post by Tom_Carr on 2016-07-26
> [COLOR=#000000]Did you install any proprietary video drivers?
[/COLOR]

I checked yes to install the non open source software when I did the install, but did not install anything in addition
> 
[COLOR=#000000]Are all systems using same video card/chip?[/COLOR]

I have not checked but I doubt it.

> [QUOTE]
[COLOR=#000000]Issues are often video related. [/COLOR]
[COLOR=#000000]Or are systems very limited in RAM. Older systems may need Lubuntu or Xubuntu as full Ubuntu with Unity needs newer video capabilities.[/COLOR][/QUOTE]

I will try that.  Which do you suggest, Lubuntu or Xubuntu?  I don't know anything about either of them.

---

### Post by oldfred on 2016-07-26
Its not just Ubuntu, but many flavors.
 Current Releases & Flavors
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)
Kubuntu, Edubuntu, Xubuntu, Mythbuntu, UbuntuStudio, Lubuntu, Ubuntu GNOME, Ubuntu Kylin, Ubuntu MATE  

Each flavor has a different gui/display and default set of applications, but use same kernel & repository for all applications.
Ubuntu with Unity and Kubuntu both need newer systems with better video cards or chips.

---

### Post by Tom_Carr on 2016-07-26
I've tried Kubuntu, Ubuntu Gnome and MATE.  I am familiar with the different displays, guis, apps and so on.  The type of gui is not so important.  I just want to version that is most likely to work booting on an external hard drive, on all kinds of different computers.

---

### Post by Tom_Carr on 2016-07-26
One of the machines that will not boot from the ext hd is already running ubuntu just fine on the internal hd.  
I get an error message:

error: file '/boot/grub/i386-pc/normal.mod' not found
Entering rescue mode...
grub rescue>

I tried entering 'e' and got unknown command

---

### Post by yancek on 2016-07-26
> I tried entering 'e' and got unknown command 				

That won't do anything at the grub rescue prompt.  Using the 'e' key is for the purpose of editing a menuentry from the Grub2 menu which you see on screen as is currently highlighted.

Did you install the Ubuntu as UEFI or MBR?
Are all of the computers UEFI or MBR?
If you installed UEFI, do you have an EFI partition on the external drive?  Not sure that will work?
If you installed MBR, did you install Grub to the MBR of the external drive?

---

### Post by Tom_Carr on 2016-07-26
> [QUOTE][COLOR=#000000]Did you install the Ubuntu as UEFI or MBR?[/COLOR]
[COLOR=#000000]Are all of the computers UEFI or MBR?[/COLOR]
[COLOR=#000000]If you installed UEFI, do you have an EFI partition on the external drive? Not sure that will work?[/COLOR]
[COLOR=#000000]If you installed MBR, did you install Grub to the MBR of the external drive?[/COLOR][/QUOTE]

I don't know what UEFI and MBR are.
I installed ubuntu yesterday so it is still fresh in my mind, and it did not ask me anything about UFEI of MBR.

Keep in mind that the external hard drive does boot successfully on another computer.

---

### Post by oldfred on 2016-07-26
Explanations of terms and links to further info is at the end of link in my signature.
Older systems are BIOS, but all Windows 8 or later that were pre-installed are UEFI with gpt partitioning.
BIOS & MBR is what computers have used since middle 1980's or IBM PC.

If you can boot it on some system, run this: 
Or from live installer you can also install Boot-Repair to run Summary Report:
       May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by sudodus on 2016-07-26
There are a few options/methods, that help making operating systems more portable - in other words, make them able to work in different computers (without changing things manually between each computer).

1. The originial and basic alternative is the live drive, as is appears, when you select the option [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389).

2. The next step is to provide a memory to this live drive, and run a persistent live drive. You can do this with all current Ubuntu flavours and versions, if you use the tool mkusb according to the following links.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

3. You can run an installed linux system, and it works well if you avoid proprietary drivers, and let the system select free drivers automatically. But it will be somewhat more limited, less portable compared to a live drive, unless you tweak the system.

It is possible to make an installed system bootable both in UEFI and BIOS mode.

-o-

Generally, it is possible to boot the system with a simple text screen or primitive graphics, and install necessary proprietary graphics, when running with this text or simple graphics. Often the graphics chip and wifi chip are most problematic (and may need proprietary drivers).

You can also tweak a system to reduce wear, which is important for installed systems in USB pendrives, but not important in hard disk drives and modern solid state drives (SSD).

You can use chainloading, if there are probleme to boot directly from the external drive. See this link

[Installation/FromUSBStick#Chainloading](https://help.ubuntu.com/community/Installation/FromUSBStick#Chainloading)

You can try the installed systems, that are stored in compressed image files and or tarballs, and described at the following links.

64-bits:
[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[UEFI-and-BIOS/stable-alternative](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative)

32-bits:
[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)
[OBI/Xenial-32-txt](https://help.ubuntu.com/community/OBI/Xenial-32-txt)
[Tested and debugged system to install [Ubuntu flavours of] Xenial 32-bit alias 16.04 LTS](http://ubuntuforums.org/showthread.php?t=1958073&page=19&p=13511300#post13511300)

-o-

I suggest that you make a ***persistent live*** system. Later on you can try with an installed system (installed like into an internal drive, but into your external drive).

You can test easily with a standard live drive to boot the different computers. Select a version and flavour, that works best (overall in all your computers), and make a persistent live drive from it. Use [mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent), and you will get a system, that can use the whole external USB or eSATA drive.

When you select persistent mkusb creates a partition for persistence in the target drive and the target system can use it automatically.

In a separate menu window you can choose between a GUID partition table, GPT, and an old style MSDOS partition table. Normally GPT is recommended (and it works with huge drives (greater than 2 TB), but many HP computers need an MSDOS partition table to boot directly from USB.

The persistent live drive boots from the third partition with a FAT32 alias vfat file system. The operating system is cloned from the iso file to the fourth partition. The fifth partition with an ext4 file system stores the overlay data for persistence.

[LIST=1]
[*]    partition: (NTFS) usbdata for storage and transfer of files
[*]    partition: GPT: bios_grub flag for booting in BIOS mode; MSDOS: extended partition
[*]    partition: (FAT32) boot partition
[*]    partition: (ISO 9660) cloned iso file
[*]    partition: (ext4) casper-rw or live-rw or persistence
[/LIST]

---

### Post by Tom_Carr on 2016-07-26
Thank you all for taking the time to try to explain this to me.  There is a lot that I don't understand.  I will take some time, read over this, read all the links, and probably be back with more questions.  

Thanks again.

---

### Post by sudodus on 2016-07-26
You are welcome - we are here to help, and we are happy to help.

Good luck :-)

---

### Post by noperative on 2016-07-26
I'm curious to know if you have the same problem putting the same OS on a flash drive instead of an external HDD. Also, what did you use to install the OS on the drive? i.e. Unetbootin etc...

---

### Post by oldfred on 2016-07-26
I typically only have Ubuntu installed and have grub and a copy of Ubuntu on every hard drive, and large flash drives.

So I eventually learned to directly boot ISO from grub. That way with now larger flash drives I was able to install several ISO, Ubuntu, Knoppix, gparted, parted magic etc so I had both an installer and a repair disk with multiple repair tools.

Now I just have all the ISO on my hard disk and use grub to boot that. I then can install to an external drive or to my other drive in my system. Installing from SSD to HDD or vice versa is very fast. Full install in less than 10 Min.

Bit more advanced as you have to have grub installed to a drive, and copy ISO, then manually create a grub loopmount boot stanza.
Details:
       [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
[URL="http://askubuntu.com/questions/388382/multi-partition-multi-os-bootable-usb/388484#388484"]http://askubuntu.com/questions/388382/multi-partition-multi-os-bootable-usb/388484#388484
[/URL]
 Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
UEFI grub install and example grub boot stanzas, Also Windows
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive) 

[URL="http://askubuntu.com/questions/388382/multi-partition-multi-os-bootable-usb/388484#388484"]
[/URL]

---

