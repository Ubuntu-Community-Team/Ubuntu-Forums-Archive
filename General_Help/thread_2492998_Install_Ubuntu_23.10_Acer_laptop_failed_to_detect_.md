---
title: "Install Ubuntu 23.10 Acer laptop failed to detect hardware"
date: 2023-11-29
forum: General Help
---

### Post by patricia.p on 2023-11-29
Laptop Acer aspire a314-22 currently booting windows 11 home, bios unsecured boot, Ahci, usb moved to 1st boot priority. I can not find a way to change to legacy
Usb burned with Rufus. I also tried manjaro just in case it was hardware not recognised by Ubuntu kernel it also failed but I captured the log prior to crash. 
It might be nvme drive or Acer stopping Linux install on BIOS v1.21
Hope to hear something that will install Ubuntu as sole os on the laptop.

---

### Post by MAFoElffen on 2023-11-29
But "your" laptop is UEFI Boot. You should have made the USB in Rufus as the option on the right, GPT only, so it boots as UEFI.

Right? You do not want to boot that as Legacy...

---

### Post by patricia.p on 2023-11-30
I created two usb with Ubuntu 23.10 in gpt fat32 today.

I checked that linpus was first in boot priority, and exited with F10.
The first went directly to Acer screen with Ubuntu logo and hung for 15 minutes. I crashed out as power button did not respond.
The second usb drive with identical flash gave me a brief warning no boot found, and no menu either. I waited 15 minutes while it hung. 

The BIOS version is the latest which I flashed prior to trying Linux.
I appreciate your help, how do I acquire logs when there is no menu? I don't see a way of upload photos of the boot.
[FONT=Helvetica]AMD Ryzen 3 3250U with Radeon Graphics[/FONT]
[FONT=Helvetica]WDC PC SN520 SDAPNUW-128G-1014
Sata mode AHCI
[/FONT][TABLE]
[TR]
[TD][FONT=Helvetica]Board Manufacture[/FONT][/TD]
[TD][FONT=Helvetica]   DL[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica]Board. [/FONT]
[FONT=Helvetica]Name[/FONT][/TD]
[TD][FONT=Helvetica]    Tulip_DA[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=Helvetica]Board Version[/FONT][/TD]
[TD][FONT=Helvetica]    V1.21[/FONT][/TD]
[/TR]
[/TABLE]
I flashed gpt NTFS Ubuntu just now, the boot log found NTFS partition on the USB, launched the NTFS bootloader until the splash screen came up and install stopped.

---

### Post by yancek on 2023-11-30
>  I checked that linpus was first in boot priority, and exited with F10.

Linpus is a much disparaged distribution of Linux which was used on some Acer notebooks.  Do or did you have it installed and if so, did you ever boot it?  Do you not have an option in the BIOS Boot Options to boot from USB?  You should be able to set the computer  to a one time boot from the usb.  A message generally appears at the bottom of the screen immediately on starting the computer telling you which key to use.

There is a link on the Ubuntu download page to another page explaining how to verify the download of the Ubuntu iso was good.  Did you do that check?  Is the usb you are using able to boot on another computer, if you have one available?

As suggested above, it would be best to do an EFI install.

---

### Post by patricia.p on 2023-11-30
The Ubuntu 23.10 usb is installed correctly on hp sff G1 i5-8500 so that linpus bootloader is working there. 

Could you give me a different Ubuntu ISO link just in case it's the 23.10 that is causing it to hang. Are there different bootloader version?
Forget what I said above.
I didn't see linpus when I tried the gpt NTFS USB, it was the first time booting, the Ubuntu NTFS is described as Kingston USB in the boot priority list.

---

### Post by MAFoElffen on 2023-12-01
Argh... Ubuntu NTFS???? LOL (Sorry) What are you making the LiveUSB from? That is where I think the difference and problem lies. Buring the image to a USB seems to be the biggest challenge people have, after verifying that the have a good image.

The LiveUSB is created it like this:
```

sdd      Ubuntu 22.04.3 LTS amd64  14.5G iso9660    USB 2.0 FD
&#9500;&#9472;sdd1   Ubuntu 22.04.3 LTS amd64   4.7G iso9660    
&#9500;&#9472;sdd2   ESP                        4.9M vfat       
&#9500;&#9472;sdd3                              300K            
&#9492;&#9472;sdd4   writable                   9.8G ext4       

```
The last may be different size or not be there at all, that doesn't really matter. those first 3 do. That one was made by "Startup Disk Creator"

On Windows I use Rufus. on Ubuntu, I use "Startup Disk Creator"...

---

### Post by oldfred on 2023-12-01
Acer has some unique requirements, but most are related to after install.
Have you updated UEFI to latest available. Some older ones had issues.

Some newer Acer required control-S in UEFI settings to open more options. If you have to set UEFI password, never lose that or reset to blank. Otherwise you may brick system. 
Most Acer require "trust" setting in UEFI on the Ubuntu grub UEFI boot entry. It may show as unknown. otherwise and not work.

Possibly similar, most Acer for several generations are very similar.
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire A515-54G Newer Acer -  CTRL S on the main Tab in BIOS to get the option to change SATA to AHCI
[https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected](https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected)
Acer Swift 3 SF314-511 See post #9 on procedure to get UEFI to see USB live installer.
[https://ubuntuforums.org/showthread.php?t=2475752](https://ubuntuforums.org/showthread.php?t=2475752)

---

### Post by patricia.p on 2023-12-02
Thanks for your help on this awkward Linux boot. The USB drive is formatted in fat32 and gpt. 

I have installed Debian 12 on the Acer, taking advice from this thread. [https://forums.linuxmint.com/viewtopic.php?t=361250](https://forums.linuxmint.com/viewtopic.php?t=361250)

I was worried that boot priority list has only 1. instead of a descriptive boot loader but is working so far. Once the install has finished I made the nvme argument permanent in terminal. 

It now boots normally, and windows is gone.

---

