---
title: "Dual boot with windows 10 on separate hard drives with legacy bios"
date: 2018-04-21
forum: General Help
---

### Post by dab0mba on 2018-04-21
Hello!

I'd like to know how to dual boot with Windows with this config:

I basically have an SSD and HDD in my setup and I my SSD is full with Windows so I can't install ubuntu.

I looked up a bunch of guides online and none seem to work. 

I partitioned my HDD and I have successfully installed ubuntu in that partition but I don't know why the Grub Bootloader isn't showing up.

and I'm really at a loss here since I have been trying for days to no avail.

I hope someone can help me over here. Thanks!

---

### Post by oldfred on 2018-04-21
Are both system installed in UEFI boot mode or both in BIOS boot mode. You should not mix, but if you did, you have to manually boot from UEFI boot menu each time.
Did you turn off Windows fast start up which is just hibernation?

What brand/model system? Some need work arounds for UEFI boot.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by dab0mba on 2018-04-21
Well actually It's a pc I built myself. My windows is set to boot in BIOS mode and I'm pretty sure that my ubuntu was installed in BIOS mode as well (since I didn't go through the UEFI). 

Yes I did turn off fast startup. The problem with it is that it just boots to windows and somehow doesn't find the bootloader for ubuntu

---

### Post by oldfred on 2018-04-21
What brand motherboard,CPU & video then? Some need extra settings.
But you should be able to boot Ubuntu live flash drive in either BIOS or UEFI boot modes. But settings in UEFI may make a difference.
And newer Windows can change settings in UEFI, but I do not think Windows 7 does?

---

### Post by rbmorse on 2018-04-21
If there is a setting in the BIOS/UEFI setup to select or designate "boot device priority" make sure that the default entry points to the the drive where the GRUB bootloader is installed.  If there is a priority list, make sure that the first entry points to GRUB.  

The Windows 7 installer will set this to point to Windows even when run in BIOS mode, but I don't think the Ubuntu install will override this setting in BIOS mode. oldfred may know more.

---

### Post by yancek on 2018-04-21
Did you install Grub boot code to the MBR of the HD on which you installed Ubuntu?  If so, you would have to set it to first boot priority in the BIOS.  Since windows boots from its drive, you have it's code in the MBR of that drive.  Answers to these questions and whether you are using the older BIOS/MBR method or UEFI can be obrtained by running the boot repair suggested above.

---

