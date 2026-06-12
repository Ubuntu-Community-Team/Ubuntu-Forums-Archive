---
title: "EFI naming conflict"
date: 2015-08-11
forum: General Help
---

### Post by clarknova on 2015-08-11
HP EliteBook 8460p
Ubuntu 15.04
Windows 10x64

I Partitioned my SSD (GPT), installed Windows 10 from USB in EFI mode, then installed Ubuntu in EFI mode. This resulted in the grub menu installing as /boot/efi/EFI/ubuntu/grubx64.efi. The Windows loader installed as /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi.

If I hit F9 and explicitly choose either of these .efi files to boot from, the computer boots into either grub or Windows as expected. Unfortunately, the firmware settings don't allow me to specify which .efi file to boot from, it automatically chooses the aforementioned bootmgfw.efi file by default, bypassing grub and the possibility of booting Ubuntu by default. If bootmgfw.efi is missing from its default location, the firmware will default to booting /boot/efi/EFI/Boot/bootx64.efi as it should.

The obvious workaround to get grub booting by default is to replace bootmgfw.efi with a renamed grubx64.efi, so the firmware will boot grub instead. The problem with this approach is that update-grub does not detect the Windows installation if the default Windows version of bootmgfw.efi is not in its place. Likewise, if I remove bootmgfw.efi altogether, or move it to its parent directory, then replace bootx64.efi with its grub counterfeit, grub again boots but update-grub does not detect a Windows installation, and thus won't boot Windows after being updated.

I understand I may be able to make a manual entry for Windows in /boot/grub/grub.cfg, but I would prefer not have to update that any time my Windows install is altered. I'm wondering if there are other directories where update-grub looks by default for a Windows .efi file, or if it can be told to look elsewhere than the default directory, since the HP firmware must be deceived in order for grub to work. Any hints on this?

---

### Post by grahammechanical on 2015-08-11
What you are describing seems to be typical for HP machines. The manufacturer has broken the protocol by fixing the UEFI so it only loads Windows. As forum member Oldfred points out we need a work around. Here is some very detail explanations by Oldfred covering several situations.

[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

You might find some help there.

Regards.

---

### Post by oldfred on 2015-08-11
With your HP the solution most often used is to copy grub or shim's efi files into /EFI/Boot and rename to bootx64.efi. Then use or if needed add an UEFI entry to boot the hard drive in UEFI mode. Note if grub ever does a major update and writes new grub or shim files into the ESP - efi system partition, you may have to copy it again. 

Some in past renamed the Windows efi boot file, but that is not recommended anymore. Windows updates overwrite it. And you cannot directly boot Windows from UEFI or one time boot key.

Some also like a gui boot loader. You can install rEFInd which seems to work on all these systems that have non-standard UEFI.

---

### Post by clarknova on 2015-08-20
> **oldfred said:**
> With your HP the solution most often used is to copy grub or shim's efi files into /EFI/Boot and rename to bootx64.efi.

Done

> **oldfred said:**
> Then use or if needed add an UEFI entry to boot the hard drive in UEFI mode.

Sorry, I don't understand this advice. I don't know how to make the laptop boot /EFI/Boot/bootx64.efi without manually invoking the boot menu at boot time, or deleting the bootmgfw.efi, making Windows unbootable.

Thank you both for the responses.

---

### Post by oldfred on 2015-08-20
The /EFI/Boot/bootx64.efi is supposed to be a default or fallback UEFI boot entry. Many systems have it and the bootx64.efi is just a copy of Windows efi boot file.
Often rebooting a couple of times will add the entry automatically.

But you can add an entry yourself with efibootmgr.
       You would first type sudo efibootmgr -v to get a list of boot options.
            sudo efibootmgr -v
    
 [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)


 sudo efibootmgr -c -g -d /dev/sdX -p Y -w -L "Default hard drive Boot" -l '\EFI\Boot\bootx64.efi' 

   Codes from 
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
-c | --create
-g | --gpt
-d | --disk DISK -  The disk containing the loader (defaults to /dev/sda) 
sdX where drive sda, sdb etc
-p | --part PART -    Partition number containing the bootloader (defaults to 1)  or sda1
-w | --write-signature
-L | --label LABEL -     Boot manager display label (defaults to "Linux") 
-l | --loader NAME -     Specify a loader (defaults to \\elilo.efi)

---

