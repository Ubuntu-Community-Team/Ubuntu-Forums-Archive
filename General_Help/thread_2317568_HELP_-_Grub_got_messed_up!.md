---
title: "HELP - Grub got messed up!"
date: 2016-03-17
forum: General Help
---

### Post by dryan775 on 2016-03-17
Hello all,

I seem to have messed up my system.

I have a Toshiba C55A laptop, dual boot Windows 8.1 and Ubuntu 14.04 LTS.  Been running great for about a year.
Last week I wanted to make a bootable USB with 14.04, full install on the stick for a friend to try Ubuntu out with some basic stuff set up for him to see what it can do.
Used a LiveDVD session on this machine to install U14.04 to the stick.  The stick seems to be working fine, but when I went back to boot the laptop from the HDD, I got:

(back screen, gray text):
GNU GRUB version 2.02~beta2-9ubuntu1.7
Minimal BASH-like line editing is supported  blah blah
grub>

if I type exit, I get a Boot Menu (Looks like BIOS, all text, black text on white background):
1. HDD/SSD
2. USB
3. ODD (DVD)
4. LAN  EPI Network
<enter setup>
<hdd Recover>

If I choose HDD a window pops up (again all text):
ubuntu
Windows Boot Manager
Ubuntu

It DOESN'T MATTER which one I choose, Windows loads.

I can still boot to the LiveDVD and windows.
Windows Disk Management shows my 146GB partition as Healty (Primary Partition)

How can I fix this?

Thanks in advance for any advice.

---

### Post by yancek on 2016-03-17
Since you can still boot windows, go to the site below and download the boot repair iso and burn it as an image to a CD.  Then reboot the computer with the CD in the drive.  Set the CD to first boot priority and when it is booted. select the option to Create BootInfo summary and when it finishes, post a link here to the output.

  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by dryan775 on 2016-03-18
OK.
With the boot messed up, I can't boot to DVD, it start to then said media [failed] and stops.  This is the SAME DVD I used to boot to live to make the bootable USB.
I was able to boot on the the bootable USB stick and ran th boot-repair you suggested.
Here is the output file link:

paste.ubuntu.com/15418618/

Thanks again for your help!
NOTE:  I was able to access the Ubuntu drive while on the USB stick, so at least the file structure is still there.

---

### Post by oldfred on 2016-03-20
Is your friend's computer UEFI also?

But any full install of Ubuntu to any second drive or external drive, always installs grub to ESP - efi system partition on sda.
After full install to sdb and even specifically telling it to install grub to sdb and it saying it is installing grub to sdb, it overwrote my main Ubuntu boot in sda.
Actual only difference is drive & UUID in the 3 line grub.cfg which is only a configfile to the full grub.cfg in your install.
You can manually edit it with correct values for your internal install or from Boot-Repair do the full uninstall/reinstall of grub which recreate all of grub.

Boot-Repair's script does not show this file. This is mine:
```
search.fs_uuid [COLOR=#ff0000]5c1e1a3f-261f-4da5-a0c2-8f479b3039de[/COLOR] root [COLOR=#ff0000]hd0,gpt2 [/COLOR]
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

Your install is in sda6 which would be hd0,gpt6,
Your UUID for sda6 is  93c6c9f0-01a0-4697-8ea1-ede0647a7452

Your ESP - efi system partition is sda2.
So from live installer:
       mount /dev/sda2 /mnt
cd /mnt/efi/ubuntu
nano grub.cfg

You have to manually partition any second drive for UEFI boot, and make sure it has an ESP as a partition. Backup your ESP on sda. And after install, copy /EFI/ubuntu to second drive. Then copy again to /EFI/Boot and rename shimx64.efi to bootx64.efi. 
External drives only boot from /EFI/Boot/bootx64.efi. And the version of grub copied from a full install has to find /EFI/ubuntu/grub.cfg.
 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode)
A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode
[http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506](http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506)
[http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/](http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/)
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)

---

### Post by dryan775 on 2016-03-21
That might have worked but seemed a bit more complicated than I wanted to try right away.  I was finally able to boot from the Live DVD (I think the boot-repiar was seeing the USB and was still trying to setup grub to use the two OSs on the HDD and the USB), and without the USB there to confuse it, boot repair worked.  I now boot to grub and can select Windows or Ubuntu - the USB install is not an option.
.
Note to get it to boot from the DVD, pressing F12 during startup gave me the option, but always said Media Failed and wouldn't boot.  I got it to work by booting into Windows 8.1 and doing the hold-shift-while-seleting-restart method - that allowed me to boot from the LiveDVD.

---

### Post by oldfred on 2016-03-21
If grub/Boot-Repair is confused about both installs, you may have one in UEFI boot mode and other in BIOS boot mode.
Grub can only boot other installs in same boot mode as you boot grub/Ubuntu. 

With flash drive plugged in.
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by jmelton on 2016-03-21
Holy crap, I have the exact same problem on the exact same computer (Toshiba Satellite C55A)! I'm running Linux Mint 17.2 (Ubuntu derivative) and was doing some updates yesterday, and the computer froze during the updates--presumably while it was updating Grub. I've gotten a number of suggestions from folks in the Mint forum and have tried a couple of things, but so far nothing has worked, so I thought I'd ask over here too. The system boots fine into Windows 10 but not Linux. 

The first thing I tried was installing boot-repair-disk on a flash drive. In order to get my computer to boot from USB, I had to switch to CSM rather than UEFI mode. When I went into boot-repair-disk and attempted to do the repair, I got an error message: "The boot of your PC is in Legacy mode. Please change it to EFI mode..." So, in order to boot from the USB disk I had to enter a mode that is incompatible with the program I'm trying to boot into, apparently. So at this point I'm stuck as far as this option is concerned.

I eventually managed to find my Mint 17.2 CD and booted into Linux on that. I followed the instructions for repairing GRUB at [https://sites.google.com/site/easylinuxtipsproject/6]("https://sites.google.com/site/easylinuxtipsproject/6") and after entering the command apt-get install --reinstall grub-efi-amd64 I got the following error message: "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem." So, I entered that, and got this error message: "sudo: unable to resolve host mint dpkg: error: unknown option -o". Strike 2. There is a boot partition there according to gparted, but obviously something is messed up with it.

---

