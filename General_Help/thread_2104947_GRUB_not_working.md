---
title: "GRUB not working"
date: 2013-01-14
forum: General Help
---

### Post by SilentJimbo on 2013-01-14
I just installed on a new machine, and after installation, grub wasn't working, would just hang on a black screen with "GRUB_" in the corner.

Booted in using supergrubdisk, and tried reistalling grub:
$ sudo grub-install /dev/sda

On powering up, I am now instead taken to a grub command line, where I don't seem to be able to do anything useful.

I also tried:
$ sudo grub-install /dev/sda5
but that returned me to the original problem.

Any ideas?

---

### Post by oldfred on 2013-01-14
How new of a machine? Is it really UEFI/gpt not BIOS/MBR?

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by SilentJimbo on 2013-01-16
After a bit of fiddling around/re-installing, I managed to get in to boot properly, however the BIOS seems to have somehow been altered, and no longer contains options for booting from cd or usb (ie these entries are now missing from the boot priority list).  This is a bit worrying, since if anything goes wrong with the current installation, I'll not have a way of reinstalling.

Here's the output from boot-repair:
[http://paste.ubuntu.com/1539000/](http://paste.ubuntu.com/1539000/)

Any help would be most appreciated.

---

### Post by oldfred on 2013-01-16
Was drive originally gpt and have Windows 8?

Your sda5 looks like a bios_grub but that is only used with gpt partitions.

Some computers can only get into UEFI/BIOS from Windows if fastboot is still on in UEFI/BIOS.

This fix was supposedly added to UEFI boots, but you are in BIOS mode:
> Grub provided with Ubuntu installed as UEFI includes a "setup" option at the bottom of the GRUB menu. This launches your motherboard's UEFI setup, and can be used to get into UEFI setup on "fastboot" systems which skip the setup screen entirely when a valid OS is installed.

    

Do not know if booting liveCD/DVD/Flash in UEFI mode will give the option to boot into UEFI or not.

---

