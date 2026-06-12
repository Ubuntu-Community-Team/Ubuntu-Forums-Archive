---
title: "Removed Ubuntu extra space partition in HDD and can't log into Ubuntu install on SSD"
date: 2023-07-29
forum: General Help
---

### Post by eduardo-horta on 2023-07-29
Hello,

After removing an Ubuntu extra space partition on my HDD from Windows 11, I've been unable to log into Ubuntu which is installed on SSD. When I try to boot into it from grub, I get sent to emergency mode. I ran boot-repair and got the following:

[https://pastebin.ubuntu.com/p/cgjbBH5w7Y/](https://pastebin.ubuntu.com/p/cgjbBH5w7Y/)

What should I do to fix this issue?

Thanks!

---

### Post by tea for one on 2023-07-29
[COLOR="#0000FF"]Line 286[/COLOR]: The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB)
Have you tried this yet?

[COLOR="#0000FF"]Line 150[/COLOR]: sda5  493611008 494610431    999424   488M BIOS boot
Did you somehow install Ubuntu 22.04 in Legacy mode?
If you had installed Ubuntu in UEFI mode, this small partition would not be created.

---

### Post by MAFoElffen on 2023-07-29
First question... Is this a new install of Ubuntu, or did it ever run Ubuntu from this installation before?
> **tea for one said:**
> [COLOR=#0000FF]Line 286[/COLOR]: The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB)
Have you tried this yet?

[COLOR=#0000FF]Line 150[/COLOR]: sda5  493611008 494610431    999424   488M BIOS boot
Did you somehow install Ubuntu 22.04 in Legacy mode?
If you had installed Ubuntu in UEFI mode, this small partition would not be created.
^^^If he installed Ubuntu in Legacy mode, but onto a GPT disk, it would create a very small boot_bios partition flagged as that. But if it did that, you would assume that it also wrote the stage1 MBR boot code to sector 0, which it didn't right?

I think if he just changed the BIOS Boot mode back to UEFI, he will boot.

---

### Post by tea for one on 2023-07-29
> **MAFoElffen said:**
> I think if he just changed the BIOS Boot mode back to UEFI, he will boot.
Certainly possible, but when you see:-
[COLOR="#0000FF"]Line 40[/COLOR]: Operating System:  Windows 7
The OP reported that "After removing an Ubuntu extra space partition on my HDD from [COLOR="#0000FF"]Windows 11[/COLOR]" which should indicate that UEFI was the installation mode.
Or an original Windows Legacy system upgraded in-situ?

Like many of these threads, it is never completely clear how the operating systems have been installed, hence the to and fro of questions and answers until everything becomes more transparent.

I'm looking forward to the day when Legacy mode OS installations have been banished to the history books ;)

Let's wait and see the OP's response.

---

### Post by MAFoElffen on 2023-07-30
Via his boot-info report, I see everything installed for MS Windows and Ubuntu installed as UEFI, but it is booting right now as CSM/Legacy. So the boot mode is set wrong.

---

### Post by yancek on 2023-07-30
The OP apparently installed Grub twice, Legacy and EFI as both the EFI and BIOS grub partitions are installed.  Questions which need to be answered are did this ever work, booting either Ubuntu and windows from Grub or both?  Apparently this is an upgrade from windows 7 to 11 and the drive is GPT so only an EFI boot will work for windows.  Since both windows and Ubuntu are on the same drive, they need to be installed in the same boot mode, EFI.   I wonder what the Ubuntu "extra space" partition was that was deleted?  I would certainly recommend the first thing to try is to disable Legacy/CSM in the BIOS and test booting in EFI mode.

---

### Post by eduardo-horta on 2023-07-31
I can't boot in UEFI, only in Legacy mode, apparently due to some issue with my BIOS. As an addendum, I never could maintain some changes to my BIOS settings such as activating virtualization, whenever I rebooted the PC, it would reset to defaults. The install was done by a technician in another city, but I don't have the money to ask him to have a look right now. But the installation was kinda wacky from the beginning, due to the weird BIOS/motherboard/something else issues my PC seems to have.

---

### Post by eduardo-horta on 2023-07-31
Hey, everyone, thanks for taking the time to help me:

@ tea for one: I can't boot in UEFI, only in Legacy mode, apparently due to some issue with my BIOS. As an addendum, I never could maintain some changes to my BIOS settings such as activating virtualization, whenever I rebooted the PC, it would reset to defaults. The install was done by a technician in another city, but I don't have the money to ask him to have a look right now. But the installation was kinda wacky from the beginning, due to the weird BIOS/motherboard/something else issues my PC seems to have.

@ MAFoElffen: I believe there was only one Ubuntu installation done on the SSD, which I share with Windows 11, but the HDD was subject to a couple failed attempts to install Ubuntu by myself, but I erased the partition where I tried to do that before sending it to the technician who then installed succesfully on the SSD.

@ yancek: This arrangement seemed to work fine, Grub allowed me to boot into Windows 11 or Ubuntu. I upgraded from Windows 10 to 11. The Ubuntu extra space partition was a NTFS partition that was supposed to be storage, however it didn't work very well, including issues with permissions, allowing changes and overall wasn't very useful, so I tried to change it to ext4, it didn't work and then I deleted this partition from inside windows.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292531&stc=1[/IMG]

Tried to boot with UEFI turned on, got this. 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292530&stc=1[/IMG]

Then tried again with UEFI, Virtualization and TPM turned on, got some more errors. I then booted into Windows 11, also from UEFI somehow.

---

### Post by tea for one on 2023-07-31
> **eduardo-horta said:**
> I can't boot in UEFI, only in Legacy mode, apparently due to some issue with my BIOS.
Line 164: 1:1049kB:106MB:[COLOR="#0000FF"]105MB[/COLOR]:fat32:EFI system partition:boot, esp;
This is the nominal ESP size for a Windows UEFI installation, hence it must have been installed in UEFI mode.
> **eduardo-horta said:**
> Then tried again with UEFI, Virtualization and TPM turned on, got some more errors. I then booted into Windows 11, also from UEFI somehow.
Now, you have booted from UEFI = progress.

Turn off TPM and see if Grub appears.
Also, disable other UEFI security settings which may prevent Grub appearing.
i.e. Secure Boot and Platform Trust Technology and similar descriptions.

---

### Post by eduardo-horta on 2023-07-31
I fixed it! I had left a line to automount the partition that was now missing in fstab: deleted it, boots nicely now! I'm really sorry for this rookie mistake lol. 

But since I'm here and still have that issue with the TPM in my BIOS, can you help me try to fix that firmware bug that appeared in the picture I showed before? Should I open another thread for this issue?

Thanks!

---

