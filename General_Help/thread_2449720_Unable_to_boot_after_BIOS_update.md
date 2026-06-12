---
title: "Unable to boot after BIOS update"
date: 2020-09-01
forum: General Help
---

### Post by backspin on 2020-09-01
Last night I updated my Gigabyte motherboards BIOS, and now I'm unable to boot into Ubuntu.

When booting I end up at the "Minimal BASH-Like line editing is supported".

By setting root and prefix in command line, I was able to boot into Ubuntu, but rebooting again just throws me back into Minimal Bash.  

I've tried installing boot-repair, and ran the tool, but since running the tool I can no longer boot into Ubuntu.  So, I'm now logged in via a live USB stick.

What recommendations do you have to fix Grub so that I can boot into the Ubuntu OS again?

Thanks,

David

---

### Post by CatKiller on 2020-09-01
Updating the BIOS/UEFI resets everything to defaults, so you'd need to set things like AHCI, whether you're using the Legacy CSM, whether you're using Secure Boot, your default boot device, and so on, again. Easy enough. 

Running Boot Repair may well have broken it, though.

---

### Post by backspin on 2020-09-01
I looked and appears boot-repair option was set for secure boot. However looking in the BIOS, secure boot is not enabled.

I checkd for AHCI and that is set to AHCI and Legacy CSM is turned on.   

What I did was to launch boot-repair again without the secure boot option. > Results  [https://paste.ubuntu.com/p/xrGDmZbHdd/](https://paste.ubuntu.com/p/xrGDmZbHdd/)

---

### Post by CelticWarrior on 2020-09-01
> [COLOR=#000000]Please [/COLOR][COLOR=#AA22FF]**do**[/COLOR][COLOR=#000000] not forget to make your UEFI firmware boot on the Ubuntu [/COLOR][COLOR=#666666]20[/COLOR][COLOR=#000000].04.1 LTS entry[/COLOR]

This ^^^. The firmware reset also resets the boot order.

---

### Post by backspin on 2020-09-01
> **CelticWarrior said:**
> This ^^^. The firmware reset also resets the boot order.

I've tried changing the boot order.

---

### Post by CelticWarrior on 2020-09-01
> **backspin said:**
> I've tried changing the boot order.

How exactly?
What was the result?

---

### Post by oldfred on 2020-09-01
You have a BIOS boot loader in MBR, so must make sure not to boot in BIOS/Legacy/CSM boot mode as it will try to use that and fail. You want the UEFI boot as fstab shows mount of ESP - efi system partition.

But I did see one other thread with a MBR partitioned drive and UEFI boot and they had issues also.
Windows only boots from gpt with UEFI and only in BIOS from MBR. 
UEFI highly recommends gpt with UEFI.
And gpt is just better than MBR.

But Ubuntu has let you install in UEFI boot mode to MBR partitioned drives.
Do not know if some of the new changes to grub for secure boot fixes also now cause issues with MBR partitioning or not.

---

### Post by CatKiller on 2020-09-01
> **backspin said:**
> and Legacy CSM is turned on.

You probably want that set to Off.

---

### Post by backspin on 2020-09-02
I backup my system daily.... After spending over 6 hours trying to figure the issue out and getting nowhere..  I simply blew it away and re-installed Ubuntu. From there I just restored my home directory, and re-installed my apps.  I'm now working just as I was before this happened.

I feel the boot-repair program really screwed up because looking at my 2 partitions, they were both set to boot and both were not working if selected to boot from.   

At this point I just need to set my backup schedule again... Fortunately I work from a high end system and it literally takes 10 minutes to install Ubuntu, and another 10 minutes to restore. I'm a Linux gamer, so I don't have a hugely complicated system to begin with, and that makes things easier from a restore standpoint. 

I really appreciate everyone's feedback and help with this matter.

---

