---
title: "Oops. Now what?"
date: 2020-12-28
forum: General Help
---

### Post by sschimel on 2020-12-28
After years of dithering, I decided this week to set up both my laptops as dual boot. The older one now has Win10/Ubuntu. The newer one got Win10/Manjaro. Turns out Manjaro doesn't play well with the system clock as no matter what setting I changed either OS, one or the other clock was always 2 hours wrong. I had set the correct time zone (Jerusalem GMT +2). So I decided to replace Manjaro with Ubunto. I did some half-assed researched and deleted the partition that had the Liniux in it. But when I try to boot from USB to install Ubunto, I get all sorts of error messages. I'm including docs showing both the errors on boot and the current partitions. I have no doubt that someone on the forum will be able to help me fix it. Thanks in advance. [ATTACH=CONFIG]287636[/ATTACH][ATTACH=CONFIG]287637[/ATTACH]

---

### Post by CatKiller on 2020-12-28
> **sschimel said:**
> no matter what setting I changed either OS, one or the other clock was always 2 hours wrong.
Windows assumes that the hardware clock is set to local time. Every other OS uses UTC for the hardware clock. There are settings in both Windows and Linux to set it to the other one, but the Linux one is probably easier: it's just a setting in a text file, although I can't remember which it is off the top of my head. I'm sure you can search for it, though.

---

### Post by sschimel on 2020-12-28
It's moot at this point as I can't install Linux

---

### Post by Frogs Hair on 2020-12-28
I use the following command to set Ubuntu to local time on my dual boot other wise there is a 4 hour difference on Win 10.   

 ```
timedatectl set-local-rtc 1 --adjust-system-clock
```

---

### Post by CatKiller on 2020-12-28
> **sschimel said:**
> It's moot at this point as I can't install Linux

Well, "newer" isn't quite as complete a description of your hardware as you might be imagining. Neither to we know what install image you're trying to use, nor whether you had errors in your download, nor whether you've written the image properly, or how you're trying to boot it. For starters. And you apparently had Manjaro working on it already, except for one issue that you now know how to fix.

---

### Post by sschimel on 2020-12-28
CatKiller, I can't tell if you're sniping at me or asking me for more info. And yes, I had Manjaro running. And now I don't. I posted my laptop's specs below; I hope that's sufficient info, in conjunction with the attachments from my original post. I'm trying to boot from a USB stick, formatted with the Ubunto ISO via Rufus. The same why I installed Ubunto on my older laptop. And the same way I installed Manjaro on my newer laptop (a 2020 model). 
I'm on: Operating System
    Windows 10 Home 64-bit
CPU
    Intel Core i7 9750H @ 2.60GHz    48 °C
    Coffee Lake 14nm Technology
RAM
    16.0GB Dual-Channel Unknown @ 1330MHz (19-19-19-43)
Motherboard
    LENOVO LNVNB161216 (U3E1)
Graphics
    Generic PnP Monitor (1920x1080@60Hz)
    4095MB NVIDIA GeForce GTX 1650 (Lenovo)    41 °C
Storage
    476GB Micron MTFDHBA512TCK (Unknown (SSD))
Optical Drives
    No optical disk drives detected

---

### Post by tea for one on 2020-12-28
> I did some half-assed researched and deleted the partition that had the Liniux in it

You probably deleted the grub bootloader and therefore the PC is looking for a non-existent file?

Shut down the PC completely
Power On
Use your [COLOR="#0000FF"]dedicated key[/COLOR] to access the UEFI boot menu
Double check that you can boot into Windows 10 via Windows Boot Manager

I hope that you have backed up all your data.

---

### Post by sschimel on 2020-12-28
I can still boot into Windows. How can I fix the grub bootloader?

---

### Post by ajgreeny on 2020-12-28
> **sschimel said:**
> I can still boot into Windows. How can I fix the grub bootloader?
Without a Linux distro installed you can't fix grub; grub depends on a Linux operating system.

Assuming the machine nis using UEFI, which I believe it must be, there will be a keyboard key to press to enable the first boot device and from this you should be able to choose the USB boot device you created.  The keyboard key depends on the motherboard in use so look in the manual or information you have with the machine and you should find that somewhere.

This, however, also assumes that the USB was created using UEFI and that you chose the UEFI option at boot as often a UEFI and non-UEFI boot option are shown, as without that it will be almost useless.  I know nothing about Rufus so can not help with that.

---

### Post by oldfred on 2020-12-28
The Ubuntu ISO is both old BIOS and newer UEFI bootable.
But Rufus only makes a flash drive that is one or the other.
You want gpt and UEFI option, not MBR CSM(non-UEFI) option.

Shows creating BIOS/MBR installer.
[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#3-usb-selection](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#3-usb-selection)
Shows creating UEFI installer:
[https://askubuntu.com/questions/1278772/unable-to-access-ubuntu-from-uefi](https://askubuntu.com/questions/1278772/unable-to-access-ubuntu-from-uefi)

With nVidia you need to use safe mode or nomodeset boot option. 
And then choose to install nVidia driver as part of install or nomodeset to boot installed system until you do install driver. Older versions of Ubuntu only had nomodeset as option. Now they give the user the option to install the proprietary nVidia driver, but user has to choose.

Safe Graphics Boot option on installer adds nomodeset.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

See also link below in my signature.

---

### Post by CatKiller on 2020-12-28
> **sschimel said:**
> CatKiller, I can't tell if you're sniping at me or asking me for more info.
The latter, with enough of the former so that you consider how people might rely on the information you provide in order to be able to help. We only know what you tell us.

---

