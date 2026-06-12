---
title: "Continued Ubuntu Boot Errors"
date: 2022-04-14
forum: General Help
---

### Post by stephencoffaro on 2022-04-14
Hello! I am a new Ubuntu user and I have been very excited to learn Linux. I followed a string of tutorials step-by-step and was able to create a bootable USB, dedicate 30 GB of partitions, and seemingly successfully installed Ubuntu. I was able to successfully able to access Ubuntu by swapped the Boot OS Manager priorities, and later realized that it would have been better to just make the selection directly when turning on my computer.

After several reboots, I encountered some errors that indicated that GRUB was unable to authenticate my account. I tried to use my Ubuntu local user password, but that was not accepted, and it occurred to me that there was no other password. 

I did a knee-jerk reaction and attempted to start the process from scratch and re-install Ubuntu from the same bootable USB. Since then, I seem to fall from one issue to the next. The most obvious issue is that I no longer see Ubuntu in the OS Boot Manager options, so I can only choose Windows OS or my bootable USB. I attempted to re-install Ubuntu with a few different options (initially I did 'something else' and used the dedicated partitions a 2nd time, and then I tried the first option, which was to erase and redownload Ubuntu). My friend suggested trying the process again with a clean image ISO and bootable USB. I've learned that the more times I try to fix the process it seems to break somewhere else, which brings me here.

I found a few guides online that suggested that I 'enable' Intel Software Guard Extensions (SQX) and disable Secure Boot, and I did both from my boot options.

I have attempted to do a boot repair ([https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)) and the process seemed to work, however, the interface did not provide an option to perform a standard repair, only an option to copy the report or to view advanced option. Per the guide I was referencing, I do not plan to touch the advanced options without some expert guidance.

The latest -- when I boot from USB and move toward installation, I choose "Normal Installation" and "Download updates while installing Ubuntu" and press continue. The next screen loads after a few seconds, but does not show any of the devices or storage that it normally boots.

**Here is the paste from my boot repair:**
[https://paste.ubuntu.com/p/5BDDDQPXXQ/](https://paste.ubuntu.com/p/5BDDDQPXXQ/)

**Also, I received the following messages that flash on my screen shortly before Ubuntu launches:**
[      0.158172] ACPI BIOS Error (bug): Could not resolve symbol [\SB.PCIO.DGPV],
AE_NOT_FOUND(20210331/psargs-330)
[      0.158192] ACPI Error: Aborting methods \_SB.PCIO.RP05.PCRP.ON due to previous error (AE_NOT_FOUND) (20210331/psparse-529)

I do not see any other error messages at this time. I am anxious to get established in a functional Linux environment and would appreciate any guidance. Thank you!

---

### Post by grahammechanical on 2022-04-14
How many drives do you have? It seems to me that you do not have any partitions to install Ubuntu in. Yet you say that you created a 30GB partition for Ubuntu. Are you choosing the install alongside option? Or the Something Else option? With the Something Else option we need to have at lease one partition already created for Ubuntu. 

If you intend to install Ubuntu on nvme0n1 alongside Windows. Then you need to use Windows tools to create unallocated space. Afterwards make sure that Windows still loads. Then we run the Ubuntu live session and use GParted to turn the unallocated space into a Linux partition (Ext4). Then when we run the installer we direct it to install Ubuntu into the Linux partition with a mount point of /. We also direct the installer to install Grub (bootloader) into the EFI partition. In your case it is nvme0n1p1. Then when we reboot we should see a Grub boot menu that gives us the option to boot either Ubuntu or Windows.

Is this what you were doing? I ask because I am not sure at all what you were actually trying.

By the way, as Windows is installed in UEFI mode you must install Ubuntu in UEFI mode. We do that by using the UEFI settings utility to load the Ubuntu live session in UEFI mode.

Regards

---

