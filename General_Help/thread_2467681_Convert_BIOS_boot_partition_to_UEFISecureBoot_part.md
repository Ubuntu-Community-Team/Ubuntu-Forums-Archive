---
title: "Convert BIOS boot partition to UEFI/SecureBoot partition"
date: 2021-10-04
forum: General Help
---

### Post by pj.connect on 2021-10-04
I need to "covert" from an ext4 linux boot partition to an ESP (UEFI/SecureBoot) boot partition in order to eventually move the current OS to another PC I currently have, which is UEFI/SecureBoot only (can't disable either UEFI or SecureBoot). 

As my current PC is getting older and older, as it supports both linux boot partition and ESP (UEFI), moving to ESP/UEFI boot seems the right choice instead to start anew on my other PC. Cant buy a new PC, and, my OS was originally installed in linux boot mode with encryption. 

This "move" or "conversion" would ensure the portability of the OS, from my old PC to the other PC I own, in case the old PC dies on me, thus hopefully ensuring the smoothest transition between PC's. My OS is on an external drive.

I would start anew, if it was possible for me to restore without lost on the new UEFI/SecureBoot only PC all current customizations/apps I actually have on my current PC, but still want portability, so I can use both PC's at the same time. 

Also, my OS is a fully encrypted system (i.e: default encryption setting of the installer). Lastly, I don't have space to create an additional ESP partition, one of the reason for the "conversion" (I would need to resize the lucks partition, and it's content).

Here's what I think are the steps I need to take to make it so:

1- ensure that UEFI support is compatible for both PC's, and ensure that SecureBoot support won't hinder to boot OS on a UEFI only that does not support SecureBoot;

2- make backup image of the ext4 linux boot partition, the encrypted root partition, and data to preserve my OS in case of mishaps;

3- somehow convert ext4 linux boot partition to an ESP (UEFI/SecureBoot) boot partition;

4- test the new installation on both PC's to ensure/demonstrate portability;

Portability is the need/issue here. Is that feasible? Is there a better way to make it so? The difficulty level is not a problem for me.

---

### Post by oldfred on 2021-10-04
If you are using encryption, you probably have an ext4 boot partition. That is not a bios_grub nor an ESP - efi system partition.
Post this:
sudo parted -l

Normally UEFI uses gpt, with Windows it is required, but Ubuntu lets you use the old MBR(msdos) with UEFI (but really should not).
With gpt to boot in BIOS mode, you need a 1 or 2MB unformatted partition with the bios_grub flag.
With gpt to boot in UEFI mode (Secure Boot or not) you need an ESP - efi system partition which must be FAT32.  A Linux boot partition must be ext4. So do not confuse an ESP which has initial boot files with a /boot partition with kernels. 
The ESP is more like the MBR or first sector of a drive that is used for BIOS boot with the old MBR partitioning. 

Have yet to see a system where you cannot turn off UEFI Secure boot. Vendors are now starting to offer systems without CSM/Legacy/BIOS boot option.
Often the Secure Boot option is not called Secure Boot. My motherboard calls it "Windows" or "Other" and since older said in manual to install Windows 7 in UEFI mode use "Other". Windows 7 did not support UEFI Secure Boot.
Some like Acer need extra keys (control S) and/or UEFI password to open up extra settings.

---

### Post by pj.connect on 2021-10-04
Hmmmm, very informative. I will change the title accordingly which will probably (convert ext4 boot partition to ESP boot partition with secureboot support), and update the rest of the post, so it will reflect exactly what I want/need, and read further your link.

---

### Post by grahammechanical on 2021-10-04
Let me look at your intentions from another point of view. You have a hard disk with Ubuntu on. The disk has MBR partitioning. You want to know if Ubuntu will still work if you put that disk in another computer. Is that it?

I only have a BIOS motherboard but I do have 2 drives. A 500Gb drive with MBR partitioning and a 250GB drive with GPT partitioning. I can tell you this: The 250GB drive with GPT has a 1MB BIOS boot partition and a 53MB efi boot partition (FAT32). Whereas, the 500GB drive with MBR partitioning only has 2MB unallocated space at the front of the drive. It does not have a boot partition. I think that is because some Grub bootloader code is in that 2MB unallocated space. And yes, I am booting different Linux versions from Grub on 500GB MBR partitioned drive. And I can also boot Linux from the Grub on the 1MB BIOS boot partition on the 250GB GPT drive.

I would expect therefore that if I had a UEFI motherboard I could put the 250GB drive in the machine and load Ubuntu without any problems. But I would have problems with the 500GB drive. I would still be able to access the data on the drive but loading Ubuntu from it, I am not so sure.

So, here are my questions: Is the motherboard of the old PC a BIOS or a UEFI motherboard? I do not think that you are clear on that matter.

> as it supports both BIOS and UEFI,

What does that statement mean? My BIOS motherboard does not support UEFI. It will work with GPT partitioned drives. Is the drive in the old PC MBR or GPT partitioned? If the motherboard is UEFI and the drive is MBR then you already have part of your answer. If the motherboard is UEFI and the drive is GPT then why do you think that there would be problems?

Of course, the way to settle this would be to put the old drive into the new PC and see what happens. It is what you want to do anyway. Do you have Windows on either of these PCs? Windows fast startup is what prevents dual booting.

Ubuntu has been compatible with secure boot for years. Proprietary video drivers are sometimes seen by secure boot as hostile code. There is nothing Ubuntu developers can do about proprietary code. Perhaps revert the old OS to the open source video driver before changing machines.

What version of Ubuntu do you have on that old PC?

Regards

---

