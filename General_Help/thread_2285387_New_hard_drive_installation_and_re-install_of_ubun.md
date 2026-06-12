---
title: "New hard drive installation and re-install of ubuntu"
date: 2015-07-05
forum: General Help
---

### Post by geomcd1949 on 2015-07-05
I've been an Ubuntu user for about three years. I understand a little about operating systems, but not much.

My SSD hard drive failed. I want to install a new SSD, and install Ubunut 14.04 on it. I know there is something called a bootloader, and think that it is stored in the motherboard's BIOS or UEFI.

My question is, is there anything I should know, or do, after installing the new SSD but before beginning installation of Ubuntu 14.04? I ask this because, with my old SSD, every time I started the computer I got the screen that presented the option of booting Ubuntu, or booting into several options of Recovery Mode. I highlighted "ubuntu" with the ip/down arrows, hit Enter, and Ubuntu then booted.

I don't want to have to make this selection, and want the OS to boot when the computer is started and go directly to the Ubuntu log-in screen.

Thanks!

~George

---

### Post by Bashing-om on 2015-07-05
geomcd1949; Hello;

No one answer fit's all. The major dependency here in respect to a new hard drive and how you set up is Other hard drives that might be installed in the box. Then there is your particular use case. Generally it is suggested that with SSDs to install the operating system proper (/) to the SSD, and on the old rotating hard drive install the ancillary partitions - /home and /swap and the supporting data partitions.

As to the boot code, you fail to have an understanding of how the process works. In bios you tell it the booting hard drive and/or device and bios looks and hands off to the boot code located on the booting device . Legacy is the (M)aster (B)oot (R)ecord -> legacy partitions ; EFI on the other hand hands off to an additional EFI boot partition that supports the better GPT partitioning scheme.
See: [https://iam.tj/kb/pc/boot/#a_bootloader](https://iam.tj/kb/pc/boot/#a_bootloader) for a detailed explanation.
Unified_Extensible_Firmware_Interface ?
MBR ?
For that initial hardware startup ?

Your use case, do you have the hardware to support separate partitions , and for your use case to what extent to you want any separate partitions ?

What hardware is available to that booting firmware ?

How much help does the GPU offer to the CPU ? Can have a lot to do with performance .

I personally have never found a fault with having my system broke up into separate partitions . '/' (root), /home, /swap ( if required due to less than 8 gigs of ram, and no hibernation) and the desired /data partitions. I like it that-a-way .

[INDENT][INDENT]just food for thought
[/INDENT][/INDENT]

---

### Post by geomcd1949 on 2015-07-05
Dear Bashing-om,

Thanks for the reply and citing the article. The article is for those smarter than I. 

My system is an ASRock H87 Pro4, cpu is an Intel i7-4770; 16GB RAM, NO other hard drives; an Nvidia GPU. No hard drives other than the new SSD.

The article mentions that some code is also placed on the cpu that governs the boot. I don't know enough to know if what has previously been placed on the cpu (by the previous installation) remains there, or if it will interfere with a new installation, or is necessary for a new installation, or will be overwritten by a new installation. 

I just want to know if I have to do ANYTHING, in addition to putting the Ubuntu installation disk in the optical drive, and setting the BIOS/UEFI so that the system boots from the installation disk. Do I have to turn on (or off) Secure Boot? Any other adjustment to the BIOS/UEFI?

I don't care about partitions - whatever Ubuntu suggests -- or the default -- will be fine.

Thanks again.

~George

---

### Post by Bashing-om on 2015-07-05
geomcd1949; Easy Peasy way:

Yes, set in the firmware that EFI is enabled - if the mainboard supports UEFI - , secure boot is disabled; set in the firmware to boot the liveDVD(USB)l
in the installer select " erase disk and install ubuntu"; answer the few questions about locale and keyboard, username and password and insure that grub is installed to 'sda' NOT any other .
Done and over with in a matter of a few scant minutes.
Reset in the firmware to boot the hard drive and ->
1st operation when install completes on the 1st reboot; make sure the system is updated.
command line way:
```

sudo apt update
sudo apt full-upgrade

```
note that apt has been re-written, and 'apt-get' is being depreciated in lieu of 'apt' .

[INDENT][INDENT][INDENT]up up and away
[/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-07-05
When you put the new SSD into the machine and then switch the computer on you will see a message that says no operating system found or insert disc with operating system or something like either of those messages. And we get those messages because we have not installed an operating system.

When we install Ubuntu on a disk whether it be SSD or hard disk the installation process will install a boot loader called Grub on to the SSD or hard disk. Then when we switch on the machine the motherboard's boot system (be it BIOS or UEFI) will look to the SSD for an operating system and it will find the Grub boot loader which will give us a boot menu. If we only have Ubuntu on the SSD then we will not see the boot menu. But Grub is still there but the boot menu is hidden.

If Ubuntu is not the only OS on the machine we get that boot menu. But there is a way to reduce the time that the menu displays to 1 second or even less. Then the machine will only load the default OS, which should be Ubuntu. To see the boot menu and boot into the other OS we will need to press Shift.

That puts it simply. Of course it can get more complicated than that. After installing the SSD you may want to check in the BIOS/UEFI boot system to see if the SSD drive is detected.

When installing Ubuntu you may need to enter the BIOS/UEFI to tell the motherboard to look at the DVD drive or a USB port for an operating system so that the Ubuntu installer will load. After installation is complete you may need to enter the BIOS/UEFI to redirect the motherboard to look to the SSD for an operating system.

Regards.

---

### Post by geomcd1949 on 2015-07-05
Bashing-om - Thanks very much. I learned something, and install was successful.

Grahammechanical - thanks for this, and also for various other help over the years.

---

### Post by Bashing-om on 2015-07-05
geomcd1949; Great !

Pleased I am able to push you along.

[INDENT][INDENT]napalm was not used in this exercise
[/INDENT][/INDENT]

---

