---
title: "Booting an internal SSD externally?"
date: 2018-01-23
forum: General Help
---

### Post by xipho2 on 2018-01-23
Hi, 
Xubuntu is installed on that SSD, but the laptop is lame, small monitor, and it would be nice to start X. from a PC. I am planning to use a USB-to-Sata-Adapter for that purpose. PC is off, plug in the adapter with the SSD into the USB port, switch on the machine, BIOS, select the SSD and hope to start X. that way, as I would do it with a flash drive. 
1. Will that work?
2. Can I try this, without breaking hardware?

Thanx for your advice!

---

### Post by TheFu on 2018-01-23
I don't have a clear picture of what you want.  

If you are trying to run an X/Client and ship the display to a different X/Server over a network, that is possible. People do that all the time, but the X/Client running on your lame laptop will still be slow.

If you somehow hope to leave an SSD inside the laptop, connected to the laptop and expect some other computer to boot from that, forgetaboutit. Things don't work that way.

And when you say "X", what, exactly, do you mean?

---

### Post by xipho2 on 2018-01-23
X=Xbuntu.This OS on an internal SSD I want to boot from outside of the PC, viaa USBtoSata Adapter. Because it is difficult to remove the PC fromthe furniture and to open it, takes an amount of time, too. Adapter with the SSD is plugged into a USB port outside of the PC, as you would use it for your Flash drive.

---

### Post by C.S.Cameron on 2018-01-23
Should not be a problem, but might be a little slow at times if there is not lots of RAM.
Don't see any reason that it would break anything.
My wife has been running Ubuntu for 10 years,from an internal drive plugged into USB.

---

### Post by oldfred on 2018-01-23
UEFI or BIOS.

If BIOS and grub boot loader in MBR, it should just work.

But if UEFI, UEFI only boots external drives from /EFI/Boot/Bootx64.efi. But grub only creates /EFI/ubuntu folder with several grub/ubuntu files.
Then you need to create /EFI/Boot and copy all of /EFI/ubuntu to /EFI/Boot and rename shimx64.efi to bootx64.efi.
When I do a full install to a flash drive, Ubuntu/grub only installs to internal ESP - efi system partition, so I have to do exactly the same copy to make flash drive work.

---

### Post by sudodus on 2018-01-23
It will probably work,

- if you have no proprietary drivers and

- if there is a bootloader in the SSD (for BIOS or UEFI mode or both).

The following link (and links from it) might help you by comparing your system in the SSD with what is suggested/described,

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

---

### Post by TheFu on 2018-01-23
> **xipho2 said:**
> X=Xbuntu.This OS on an internal SSD I want to boot from outside of the PC, viaa USBtoSata Adapter. Because it is difficult to remove the PC fromthe furniture and to open it, takes an amount of time, too. Adapter with the SSD is plugged into a USB port outside of the PC, as you would use it for your Flash drive.

Generally speaking "X" means X/Windows or X11 ... which is short for X11/Windows.  Hence my confusion.  [https://en.wikipedia.org/wiki/X_Window_System](https://en.wikipedia.org/wiki/X_Window_System) for reference.

You want to only have the "lame" laptop to be used as boot storage?

Do you want to leave the SSD internally connected to the "lame" laptop, but use it to boot some other computer?   There are ways to use the storage for external systems using PXE or NFS or iSCSI, but these are non-trivial to setup and require the "lame" laptop be setup specifically for that purpose.

The easiest answer is to pull the SSD out of the "lame" laptop, and either install it into a different system or put it inside a USB external case or use the appropriate SSD connector to USB device.  Different SSDs have different sorts of connectors, so without the exact model of SSD to look up the exact case/adapter needed, it is difficult to say.  SATA, mSATA, m.2 SATA and others are some of the different connector types. [https://rog.asus.com/articles/hands-on/easy-guide-to-ssds-sata-msata-m-2-and-u-2/](https://rog.asus.com/articles/hands-on/easy-guide-to-ssds-sata-msata-m-2-and-u-2/) has details for many.

Please confirm what you really intend.  Reading the other posts here, it is clear we are all interpreting differently.

---

### Post by sudodus on 2018-01-23
> **thefu said:**
> please confirm what you really intend.  Reading the other posts here, it is clear we are all interpreting differently.

+1 :-)

---

### Post by xipho2 on 2018-01-27
Cameron's post is the right reply. But, alas, the BIOS of the  PC did not display the SSD, as it would happen with a flash drive. I am  using the adapter, shipped with the SSD for cloning the OS. Perhaps not  suitable for that purpose?

---

### Post by oldfred on 2018-01-27
Is it UEFI?

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by C.S.Cameron on 2018-01-27
There are almost too many things that can go wrong to list.
Try the SSD on a different machine.
Try booting plugged into USB of laptop.
Try F10 or F12 to get a BIOS boot menu.
When booted from Flash drive can you see contents of the SSD?
Are there proprietary drivers on the SSD? Nvidia, etc.
If the laptop is lame it is probbably BIOS, but is the PC?

---

### Post by xipho2 on 2018-02-01
No UEFI. But, as said, Flash drives are displayed and the OS installed on the flash drive is starting.

---

### Post by xipho2 on 2018-02-01
@Cameron: Tried it on different machines. no avail. Of course I got to the BIOS menue, the SSD was not displayed....

---

### Post by sudodus on 2018-02-01
Maybe the external box for the SSD does not cooperate well enough with the boot system of the computers. Many boxes can be used for booting, but not all of them. (I often boot systems in external SSDs.)

---

