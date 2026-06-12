---
title: "Can't boot to grub - UEFI boot sector trashed?"
date: 2017-06-14
forum: General Help
---

### Post by bsmith52 on 2017-06-14
Hello all,

I must have done something wrong the last time I shut down Ubuntu. Since then, I have not been able to boot into grub.

What I have done:
 - I have used the Super - Grub2 disk. I have been able to access Ubuntu, but unable to load Windows 7.
 - I have tried to recover via "sudo update-grub2" to recover grub bootloader - no go.
 - I have tried the recommended Ubuntu boot-repair utility to try the recommended repair - no go.
 - I have generated the boot info summary:
     [http://paste.ubuntu.com/24861702/](http://paste.ubuntu.com/24861702/)

My next step would have been a rebuild of the UEFI boot sector. This looks like it is a bit above me, so I thought that i would try this forum before I completely trashed this PC with an unsuccessful repair attempt.

Thanks in advance for your help.

---

### Post by oldfred on 2017-06-15
As Boot-Repair suggests:
The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
Do you want to continue?

And do the full reinstall of grub2 in UEFI mode.


Ubuntu is installed in UEFI boot mode.
Windows is installed in UEFI boot mode, but has not been added to grub menu.

Does your Slackware boot from grub menu. Just curious if it works from Ubuntu's UEFI grub to boot Slackware.
You show no BIOS boot loaders at all.

---

### Post by bsmith52 on 2017-06-17
46 years of programming computers and 10 years with Linux, and I still haven't "gotten" Linux. Arg!

I've been reading your excellent post, and am learning much. But still have not gotten a complete handle on it.

Your last question first: I have had no problems booting Slackware from Grub. I know that Slackware has used Lilo boot for a long time, but I had no trouble with Grub.

You mentioned that I am booting in legacy mode. This seems to be the source of the bulk of my problems. I thought that I had enabled UEFI. I had thought that once I had converted my HD's to GPT that my Unbuntu install would have been UEFI. But apparently, it was installed as legacy.

It has been a learning experience these last few days. Not the least of which was the key on making my flash drives bootable. I had spent many days thinking that by having the file /EFI/boot/bootx64.efi was sufficient and failing. Now I found that it takes a boot flag that can be inserted by Gparted at USB flash creation time. Thank you!

I have gotten my system working - even though I am unable to make Ubuntu the default on boot. But I am working. So I will close this thread. Thank you again.

---

### Post by oldfred on 2017-06-17
With new UEFI systems there are 3 ways to boot UEFI with Secure Boot, UEFI &  CSM which some systems call BIOS and other legacy.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

But you have the 3 ways to boot an install, and separately you have the three ways to boot installer. And how you boot install media it then how it installs which may not be the setting to boot the system once installed.
If you have Secure boot on, you may have to turn on allow USB boot and then only UEFI Secure Boot works. But currently with Secure boot on, you cannot boot Windows from grub, only from UEFI. And you cannot install proprietary drivers as they are a blob and Ubuntu cannot sign the blob to make it secure.

---

