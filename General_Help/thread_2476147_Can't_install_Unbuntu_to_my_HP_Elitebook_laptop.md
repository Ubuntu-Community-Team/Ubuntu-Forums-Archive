---
title: "Can't install Unbuntu to my HP Elitebook laptop"
date: 2022-06-17
forum: General Help
---

### Post by vett93 on 2022-06-17
I am trying to convert my HP Elitebook 850 to an Unbuntu laptop. I used Rufus to create a bootable USB drive with Ubuntu 20.04 LTS. I have tried it several times. But they all ended with "Bootdevice not found" error. I suspected that I did not partition the SSD properly. Can someone please advise what I should try next. Thank you.

---

### Post by sudodus on 2022-06-17
- Please tell us more details about your computer, for example the **model number of the graphics chip/card**. Knowing more about your computer will help us help you.

- **Can you boot into the USB drive?** Is there any option to boot the internal drive at all? Does it try booting and print some error output? In other words, how far does the boot process continue until it fails?

- **Can you run the Ubuntu installer** and install Ubuntu into the internal drive? Is there any error output during the installation?

- Is there any option to **boot the internal drive** at all? Does it try booting and print some error output? In other words, how far does the boot process continue until it fails?

[hr][/hr]
- Did you check with [FONT=Courier New]**sha256sum**[/FONT] that the downloaded file is good?

- When problems with 20.04 LTS in a new computer, it is a **good idea to test the newest released version, 22.04 LTS**. It has a newer linux kernel with newer hardware drivers, that are more likely to work (with a new computer).

---

### Post by mIk3_08 on 2022-06-17
> **vett93 said:**
> I am trying to convert my HP Elitebook 850 to an Unbuntu laptop. I used Rufus to create a bootable USB drive with Ubuntu 20.04 LTS. I have tried it several times. But they all ended with "Bootdevice not found" error. I suspected that I did not partition the SSD properly. Can someone please advise what I should try next. Thank you.
> **sudodus said:**
> - 
- Did you check with [FONT=&quot]**sha256sum**[/FONT] that the downloaded file is good?
I agree with suddus. Please check the sha256sum of your download maybe it was corrupted or something's not good with the your download. Regards and cheers.

---

### Post by oldfred on 2022-06-17
HP does not seem to support the use of efibootmgr to change boot order.  Grub uses that when it installs the boot loader.
Many also have to update UEFI firmware and if SSD update SSD firmware.

You should be able to got into UEFI settings (not UEFI boot menu) and change boot order.
hp 250 g3  Change boot order in UEFI settings
[https://ubuntuforums.org/showthread.php?t=2467077](https://ubuntuforums.org/showthread.php?t=2467077)
HP Envy - use UEFI to change boot order & f9 f10
[https://askubuntu.com/questions/1332255/dual-boot-only-booting-into-windows-no-option-to-choose-between-windows-or-ubun](https://askubuntu.com/questions/1332255/dual-boot-only-booting-into-windows-no-option-to-choose-between-windows-or-ubun)

There may be other UEFI settings as every vendor seems to have something unique.
HP Elitebook 840 G5 gpt issues - 
HP put a fail-safe gpt recovery into the UEFI Settings,  go into the UEFI Menu in Security -> Hard Drive Utilities -> Uncheck "Save/restore GPT System of Hard Drive"
[https://ubuntuforums.org/showthread.php?t=2436271](https://ubuntuforums.org/showthread.php?t=2436271)

---

### Post by vett93 on 2022-06-17
Thanks all. Let me provide more info. I am stuck at the Step 10 of this guide: [Install Ubuntu desktop | Ubuntu]("https://ubuntu.com/tutorials/install-ubuntu-desktop#10-complete-the-installation") The installation completed but I could not boot from the internal drive. I was at the page that it asked me to remove the USB drive and press enter. So I did that. Then it tried to boot from the internal drive, but failed. The error message is as follows:

BootDevice Not Found
Please install an operation system on your hard disk.
Hard Disk - (3F0)
F2 System Diagnostics
For more information, please visit: [www.hp.com\go\techcenter\startup]("http://www.hp.com\go\techcenter\startup")

I had installed Ubuntu to Windows computers a few times many years ago, but never on a HP laptop. My installation seemed to mess up the boot partition (not sure if this is the right term). When I enter the boot menu and try to select any option, it takes me to "HP PC Hardware Diagnostics UEFI" page. It has 4 options: memory test, hard drive check, language, and exit. I tested memory and hard drive, and found no error.

I downloaded the Ubuntu 20.04 LTS using my other Windows computer. There is no sha256sum option on the download page of the Ubuntu webpage.

---

### Post by sudodus on 2022-06-17
You have a new computer, and for that reason you need a new version of Ubuntu with a new Linux kernel and its new hardware drivers. So I suggest that you download Ubuntu Desktop version 22.04 LTS (architecture amd64 for PC) and check its sha256sum. You find both at this link:

[https://releases.ubuntu.com/jammy](https://releases.ubuntu.com/jammy)

It might work directly after boot, you might also need some tweaks according to the tips by oldfred in post #4, or even some more tweaks. But after some trial and error you will succeed ...

---

### Post by yancek on 2022-06-18
The link below has a download link for 20.04 as well as the sha256sum.  Might try downloading and checking again.

If you haven't solved this problem yet, I can tell you that I have an HP Notebook as well as an HP Pavilion on which I have installed Ubuntu and at least one other LInux OS so it is obviously possible.

You should have multiple options in your BIOS firmware.  You will have difficulty using efibootmgr with an HP, I've not been able to make changes on either computer with it but it is generally pretty simple to access  the BIOS firmware to make needed changes.  On both my HPs, I need to repeatedly tap the Esc key on boot and will then get several options including F9 for one time boot changes and F10 for permanent changes.  I'm not sure that your method to access the BIOS is the same on the Elitebootk, you will have to check that yourself.  Using F10, you should get several more options other than the HP Diagnostics option.

Do you have windows installed on the computer you are trying to install Ubuntu on?
What release/version of windows is it, if you have it?
If windows is/was installed, was it an EFI install?
Did you boot and install Ubuntu in EFI mode?
If you do not have windows currently installed, was it installed and was it an EFI install?

---

### Post by vett93 on 2022-06-21
Thanks all. It finally works!!!

I changed HP's boot mode options to "UEFI Native (without CSM)". Then it just works and works. Thanks all who have helped. :-)

---

