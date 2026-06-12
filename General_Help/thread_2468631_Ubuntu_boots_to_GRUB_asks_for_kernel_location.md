---
title: "Ubuntu boots to GRUB asks for kernel location"
date: 2021-11-05
forum: General Help
---

### Post by woodrowc on 2021-11-05
I'm new to Linux, I installed Ubuntu on my SSD and after being told the installation was successful I rebooted. When it boots up it gives me a GRUB line and asks me to ID the kernel location first. Is my computer not giving me a boot menu because I didn't install it on my C drive with windows? Should I reinstall my Ubuntu on my C drive or should I try hunting down my kernel location?

---

### Post by oldfred on 2021-11-05
Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO unless 21.10:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

It seems Boot-Repair does not yet have a ppa download available for 21.10. If that version, use the ISO and create a bootable flash drive.
The Boot-Repair ISO is based on Lubuntu.

---

### Post by woodrowc on 2021-11-05
Is this what you're looking for? [https://paste.ubuntu.com/p/tH3TjTVF6y/](https://paste.ubuntu.com/p/tH3TjTVF6y/)

---

### Post by yancek on 2021-11-06
>  Is my computer not giving me a boot menu because I didn't install it on my C drive with windows?  

Sorrry but, you need to go way back to before the very basics as that will absolutely never work.  First off you say "Ubuntu" but not which Ubuntu.  It matters as Ubuntu has been releasing multiple distributons yearly for well over a decade and we have no idea which you are using unless YOU tell us.  Also, you mention windows but not which windows.  The first release of windows was in 1985, do you see the problem if you are not specific?

A Linux operating system (Ubuntu) will not run on a windows (ntfs) filesystem nor will a windows operating system run on a Linux filesystem.
So which Ubuntu, which windows, do you know the type of drive you have (gpt, msdos) or whether windows and/or Ubuntu are installed UEFI or Legacy mode?  If you don't recognize any of these terms, time to do some reading.  Dual booting windows 10 and Ubuntu UEFI is explained at the link below.  If you have windows 10 preinstalled and Ubuntu, read the link below through its entirely, probably more than once as a lot of terms are going to be unfamiliar.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

After reading through the link above, take a look at the boot repair output, specifically lines 23-35 which show that you do have an EFI install of both windows and Ubuntu and the proper EFI files for both are on .nvme0n1p3 which is an nvme drive and partition 3 is the vfat EFI partition.  Not that both window and Ubuntu EFI files are here although the windows system partition (referred to as C drive) is on that same drive nvme0n1p4 (partition 4) your Ubuntu is on another physical hard drive.  Your Ubuntu OS is on a separate drive/partition (sda4).  The sda3 vfat partition serves no useful purpose.

You will need to access your BIOS firmware.  Look at lines 108-117 in boot repair.  Your current boot is Boot0012 which is your Samsung slash drive which I expect is the flash drive you used to install Ubuntu.  You need to change that to Boot0001 so that Ubuntu boots first.  When you successfully boot Ubuntu, open a terminal and run the following command to add windows to the Ubuntu Grub menu so that you will be able to select either windows or Ubuntu from that menu.

When you initialy boot the computer, you should see several options, Boot Options for a single change to boot which is what you used to set the Samsung first, and another option which you can use to make the change permanent.  These options vary from manufacturer to manufacturer and you have not indicated what manufacturer you are using so you will need to check your owner manual or do an online search on how to access the BIOS firmware for your specific model.

---

### Post by oldfred on 2021-11-06
You are showing UEFI installs of both Windows &  Ubuntu.
Report cannot tell if Windows 8 or 10, but you have Ubuntu 20.04.3.

But you have old Windows BIOS type boot loaders in the gpt protective MBR. Those will never work as Windows installs are UEFI on gpt drives which can only be UEFI boot.

Have you switched to try to boot in BIOS/CSM/Legacy mode and that is what is causing error?

---

