---
title: "Ubuntu boot stuck at &quot;Loading initial ramdisk...&quot; after changing legacy to EFI mode."
date: 2013-04-05
forum: General Help
---

### Post by htellez on 2013-04-05
Hello. I first tried to install ubuntu 12.10 (64-bit) in EFI mode. But I couldn't (the installer or try mode never loaded), so I installed it in legacy mode and it worked fine.
I have windows 8 installed in EFI mode and the recommendation was to change ubuntu to EFI mode as well ([https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)). 

I did so using the Boot-Repair tool.

After changing to EFI boot mode. I could see listed ubuntu and windows on the grub menu. Windows works just fine but ubuntu
gets stuck after displaying the line:
Loading intial ramdisk...

The url that Boot-Repair gave me is: [http://paste.ubuntu.com/5679516/](http://paste.ubuntu.com/5679516/)

As many of these EFI problems depend on the computer model. I must say that my computer is a MSI-G70.

I have read another forums, but no one said that they were first able to boot in legacy mode and after the change to EFI mode they couldn't.
They list problems like "when I have: [ usb devices plugged in / the ethernet card enabled ] it gets stuck".

I really hope I'm not posting a repeated question. And I will greatly appreciate any help.

---

### Post by oldfred on 2013-04-05
It sounds like you are past the efi or BIOS boot, but into video or boot parameters. Or maybe still before the video issues and initrd was not reset correctly for UEFI?

Did Ubuntu boot ok in BIOS mode?

But UEFI uses drivers and BIOS uses interrupts so their is some difference in how they startup.

Have you tried the second grub entry or recovery mode? It may be under advanced options.

What video card and processor?

 Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by htellez on 2013-04-05
Before I migrated ubuntu to EFI mode. It booted just fine in legacy mode. (Now that grub changed, I cannot start in legacy mode anymore).

I have tried the 3 boot options listed in grub menu.
The one that just says ubuntu (this one is not verbose, it never displays something)
The two that are under "Advanced options for ubuntu" wich seems the old grub version listing two modes for each kernel, normal and recovery mode (I tried both, and both get stuck at "Loading initial ramdisk...").

My processor is: Intel CORE i7-3630!M @ 2.40 GHz (8 cores)
The integrated video card is: Intel HD Graphics 4000
The dedicated graphic card is: GeForece GTX 675M

---

### Post by oldfred on 2013-04-05
With nVidia I have always had to use nomodeset on first boot or until I install the nVidia driver from Software Updates/Add'L drivers.

But are you booting with the internal graphics of the chip or with nVidia. Some have to turn one or the other off to boot. Do you have a BIOS setting for that?
Is this a Optimus system?

---

### Post by htellez on 2013-04-05
I have not the option.

---

### Post by oldfred on 2013-04-05
Then how do you know what video is used?

       nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Switchable Graphics is killing my Ubuntu Experience - see post #9
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)

---

### Post by htellez on 2013-04-07
I'm sorry about the delay in my answer.
The question wondered me and I did a little research.

It seems that my computer by default uses the intel graphic card.

And not only that, it seems that my nvidia graphic card has never been used.
 
I have the same problem than this person, at least in windows:
[http://www.tomshardware.com/forum/370549-33-gt70-670m-used](http://www.tomshardware.com/forum/370549-33-gt70-670m-used)

---

### Post by oldfred on 2013-04-07
There is only one Intel driver, the open source on supported by Intel. Intel is updating it for its newest chips, so it is regularly updated. Not sure what version is default with Ubuntu repositories.

 Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1 
[*]nVidia: nomodeset 
[*]Generic: xforcevesa or nouveau.modeset=0 
[*]Radeon: radeon.modeset=0 
[/LIST]

If you get liveCD to boot, you can see which is used:
 ubuntu@ubuntu:~$ lspci -nnk | grep -iA3 vga 

Some Intel do need settings and some of those newer systems also need other boot parameters.

A setting like this, but using your screens exact size not example 12080x1024.
 Force Intel Video mode as boot parameter in grub menu
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

 For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

Asus i3 with Intel graphics, 
"acpi_osi=Linux"
"video=1280x1024-24@75" or whatever native resolution is

 Intel Video Developer blog
[http://blog.ffwll.ch/2012/11/neat-drmi915-stuff-for-38.html](http://blog.ffwll.ch/2012/11/neat-drmi915-stuff-for-38.html)
Intel on new beta Kernel 3.8
[http://www.phoronix.com/scan.php?page=news_item&px=MTIzNDE](http://www.phoronix.com/scan.php?page=news_item&px=MTIzNDE)

---

### Post by fr-sc on 2013-10-03
Hello htellez,

Have you ever resolved the issue? I've got a new MSI GE60 and I'm running into the very same problem as you described it.
Although I use Ubuntu 13.04 now.
Thanks for any help!

frsc

---

### Post by fr-sc on 2013-10-24
I can get it to work more or less, when I set my GE60 to "UEFI with CSM" boot option and disable "Secure Boot".
I can select Ubuntu and Windows in GRUB. Although I can't get it working with the Windows boot manager set up with EasyBCD.

---

### Post by oldfred on 2013-10-24
Know nothing about EasyBCD, but with UEFI you do not need it as all boot loaders are equal and in UEFI menu. Grub2 will also give a menu to boot other systems also. Windows is the only system that does not offer to boot others and with BIOS some insisted on using Windows and then the third party EasyBCD. EasyBCD uses grub4dos with BIOS, not sure what it does with UEFI.

---

