---
title: "Grub"
date: 2016-06-19
forum: General Help
---

### Post by mitch24 on 2016-06-19
I may of accidentally deleted the partition of my HDD where Ubuntu was installed. I have Windows 7 on 1 partition and Ubuntu 14.1 LTS on the other. I've downloaded the same version of Ubuntu and made it into an ISO and tried to run a repair but to no avail. I can't even get into the BIOS to pick which device I want to boot from, when I turn the computer on it goes straight to the black screen where it says at the top "GNU GRUB version 2.02~beta2-29ubuntu0.2" and then underneath it has "MINIMAL BASH-like line editing is supported. For the first word, TAB Lists possible command completions. Anywhere else TAB lists possible device or file completions". Can anyone help me? I'm pulling my hair out and i've pretty much tried every single tutorial online!

---

### Post by yancek on 2016-06-19
If you can't get into the BIOS you have more serious problems than your bootloader.  There are absolutely no boot files for Grub or any other bootloader on your system board, they are all on the hard drive.  What exactly did you do with this Ubuntu iso?  Did you burn it as an image to a DVD to boot with, use the appropriate software to create a bootable flash drive and try booting it?  The Grub message you see is the result of deleting the partition with Ubuntu on it as that is where the majority of the Grub boot files are.  This is expected behavior and has nothing to do with your inability to access the BIOS.  You need to set your boot priority to the newly created Ubuntu DVD or flash drive to boot it.

---

### Post by mitch24 on 2016-06-19
Hey mate, 

I downloaded the ISO image from the website and then used YUMI to create a bootable USB but when I restart the computer it goes straight into the GRUB error message. How can I set my boot priority when I can't access the BIOS?

Also it doesn't explain why I still can't access Windows 7, if I JUST deleted the partition with Ubuntu on it then why can't I run Windows 7?

---

### Post by Impavidus on 2016-06-20
> **mitch24 said:**
> How can I set my boot priority when I can't access the BIOS?You can't. You'll have to get to the bios screen or the more modern uefi screen. Given that you dual boot with Win7, it's probably the legacy bios. On most computers you get a screen with the logo of the hardware manufacturer, even before you see the grub screen. It should mention a key to get into the bios and set boot priority. Usually this is something like Esc, Del, F2 or F10, but if varies by make and even model of computer.

> **mitch24 said:**
> Also it doesn't explain why I still can't access Windows 7, if I JUST deleted the partition with Ubuntu on it then why can't I run Windows 7?When you start a computer dual booting Linux and Windows, you first get grub, which is a boot loader. Grub is in the master boot record of your hard drive, which can hold only one boot loader. Grub reads its configuration files from the Ubuntu partition (which no longer works on your computer), which tell grub where it can find the Ubuntu boot files and the Windows boot loader. If you select Windows, grub will transfer control to the Windows boot loader (something called chainloading) and then Windows will boot, not even knowing grub or Linux are present. But without the grub files, grub doesn't know how to transfer control to Windows.

If you have Ubuntu and Windows on separate hard drives, or if you have an uefi system, you can boot Windows directly from the bios/uefi, bypassing grub. But I think you don't.

If you don't want Ubuntu any more, you can try to repair Windows booting using a Windows install or repair dvd. It will restore a Windows boot loader to the master boot record. If you can boot a Linux live disk, you can try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). It should be able to install a generic Windows boot loader to make Windows bootable again.

If you want to reinstall Ubuntu, just do so. It should detect Windows and give you a working grub menu again.

---

