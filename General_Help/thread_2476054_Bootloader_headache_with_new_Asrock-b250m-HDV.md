---
title: "Bootloader headache with new Asrock-b250m-HDV"
date: 2022-06-15
forum: General Help
---

### Post by yog-sothoth-cat on 2022-06-15
Hello all, I am ripping my hair out from this annoying bootloader issue. Here is what happened. I was gifted a motherboard + CPU combo from a friend of mine. I swapped the motherboard I was currently using out with that one. 

My system is dual booted. On sda, I have ubuntu. On sdb, I have windows. On my previous system I had GRUB installed on the EFI partition of /dev/sda1. In that partition, there is also a windows bootloader. 

When I turned my computer on for the first time, the UEFI did NOT recognize that I had grub installed. It only showed "windows bootloader" when it was searching for bootable media.

None of my files changed since swapping motherboards. I accidentally skipped the bios once, and windows said it was "repairing something." I let it happen. When I later booted the computer up with an arch liveCD, and mounted sda, none of the files were actually changed. 

I am concerned that the motherboard is somehow unable to see grub EFI information. There also isn't an option to manually specify an .efi file to boot from, otherwise I would just do that and bypass this headache. Maybe the MBR was overwritten by windows? 

I haven't made any changes yet because I don't want to break things any further. If push comes to shove I can just save all my old files and nuke everything, but I would rather it not come to that. 

Here is an imgur link with annotated screenshots. Thank you everyone! 

[https://imgur.com/gallery/Xq7CMta](https://imgur.com/gallery/Xq7CMta)

---

### Post by grahammechanical on 2022-06-15
> Maybe the MBR was overwritten by windows?

First of all, if the motherboard is UEFI and the hard drive has an EFI partition there cannot be an MBR (Master Boot Record).

You say that Windows was repairing something. Windows may also have set fast startup back on. That would prevent the Grub boot loader for working. Do you see a Grub boot menu? Can you use Windows to view the contents of that EFI partition? Do you see Ubuntu EFI boot files?

Regards

---

### Post by pbear42 on 2022-06-15
Adding the appropriate entry using efibootmgr probably would work, but IMHO easier to reinstall Grub.
You're gonna need an Ubuntu live session, though, not Arch.  Something like this should do it:

```
apt install grub-efi-amd64-signed shim-signed
sudo mount /dev/sda2 /mnt
sudo mount /dev/sda1 /mnt/boot/efi
sudo grub-install /dev/sda --boot-directory=/mnt/boot --uefi-secure-boot
```

This assumes the system partition is sda2 and the EFI partition is sda1.  Adjust as appropriate.
And, yes, the correct target for grub-install is the device, not the EFI partition.

ETA: Forgot to mention, you need to be connected to the internet before running the commands.

---

### Post by yancek on 2022-06-15
>  On my previous system I had GRUB installed on the EFI partition of  /dev/sda1. In that partition, there is also a windows bootloader. 
 

You should then have several directories in your EFI partition which would include Microsoft with the windows EFI boot files and ubuntu with the Ubuntu boot files.  There are Grub files on the EFI partition but the majority of files needed to boot Ubuntu are on the system partition.

>   I accidentally skipped the bios once, and windows said it was  "repairing something." I let it happen. When I later booted the computer  up with an arch liveCD, and mounted sda, none of the files were  actually changed. 

Repairing 'something' is pretty vague.  No way for anyone here to know what happened.  How do you know none of the files were changed?  Had you read through them before and after to compare and what files exactly are you referring to?

---

