---
title: "Dual booting 14.04 and 16.04"
date: 2016-02-20
forum: General Help
---

### Post by SuperFreak on 2016-02-20
There are a gazillion posts,web sites, blogs about dual booting Ubuntu and Windows but I can't find anything about dual booting 2 versions of Ubuntu. I have a UEFI system and I am thinking of installing a dual boot of my present 14.04 with a beta version of 16.04 when it comes out. Is it simply a matter of using Something else in the installation procedure and making sure that the bootloader is in the same place as my 14.04 install (sda1)?. Attached is screenshot of gparted.

---

### Post by Dennis N on 2016-02-20
Use "Something Else" to specify the partition to be used for root (and optionally you home partition). The boot loader location for all installs done in UEFI mode with Ubiquity installer is the first EFI system partition on the first SATA drive (sda). Any other choice you make is just ignored.

The effect of this is that the previous Ubuntu boot files in the EFI system partion are overwritten by the newer install, and you will be booting it by default. If you don't want that, you backup the ubuntu folder in the EFI partition first, and restore it after the new install to have it boot to the previous install instead. 

Note: You will have the ability to boot only one Ubuntu OS in the EFI Boot Manager's boot menu - The other you boot from grub. This is not really a problem.

---

### Post by SuperFreak on 2016-02-20
Thanks, I was going to back up my original install in it's entirety with REDO in case it all went pear shaped.

---

### Post by Dennis N on 2016-02-20
You should have no problems.

Just to add, even if you don't backup the ubuntu folder in the EFI system partition, it is easy to manually edit the tiny /EFI/ubuntu/grub.cfg file to restore the previous system to the default boot, since it is the only file that is different, as far as I can tell. One of the advantages of UEFI.

---

### Post by SuperFreak on 2016-02-20
I guess boot repair would fix the partition automatically

---

### Post by grahammechanical on 2016-02-20
I have no experience of UEFI.

I am thinking that if the issue is grub.cfg in the efi boot partition belonging to 16.04 & not 14.04 then loading into Ubuntu 14.04 and running 

```
sudo update-grub
```

might fix it. Yes?

Regards.

---

### Post by oldfred on 2016-02-21
I always manually edit the grub.cfg in /EFI/ubuntu.
I copy in my ESP - efi system partition /EFI/ubuntu to another folder, so I can copy grub.cfg back.

I even tried changing the GRUB_DISTRIBUTOR entry in grub.
And I do get another folder in ESP, but somewhere grub is hard coded to only use /EFI/ubuntu/grub.cfg.
This did not work, but I did get new folder:
 #GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR="trusty"


And just to make it difficult they have changed the default mount of /EFI/Ubuntu, so you cannot edit it.
       Change the parameter to from umask=0077 to defaults.

   sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
or
sudo nano /etc/fstab
sudo mount -a

The remount will not change it, immediately either. You have to reboot.


 # /boot/efi was on /dev/sda1 during installation, be sure to use your UUID
14.04 fstab entry defaults
UUID=FD76-E33D  /boot/efi       vfat    [COLOR=#ff0000]defaults[/COLOR]        0       1
15.04 and later fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat [COLOR=#ff0000]   umask=0077[/COLOR]      0       1

---

### Post by Dennis N on 2016-02-21
> **grahammechanical said:**
> I have no experience of UEFI. I am thinking that if the issue is grub.cfg in the efi boot partition belonging to 16.04 & not 14.04 then loading into Ubuntu 14.04 and running ```
sudo update-grub
``` might fix it. Yes?
Regards.
Yes to the first part, but update-grub won't fix it.

In Ubuntu UEFI installs, there are two different grub.cfg files:

**/EFI/ubuntu/grub.cfg** in the EFI system partition, and **/boot/grub/grub.cfg** on the root partition. 

The first specifies the device on which the OS to be booted at startup is located. You can edit this file after installing to "point" to another Ubuntu that you have previously installed (or replace it with the previous backed-up file). Running update-grub in 14.04 won't change this - it will just generate a new /boot/grub/grub.cfg for the 14.04 and won't change the other grub.cfg - you would still boot to 16.04 (and its grub menu) at start up.

---

### Post by SuperFreak on 2016-02-21
I am afraid I am lost in the technicalities here. Will boot repair fix grub?

---

### Post by oldfred on 2016-02-21
Using Boot-Repair's advanced mode to totally uninstall/reinstall grub should work. You still want UEFI boot and reinstall grub2's UEFI version grub-efi-amd64.
If running from inside one install, you may have to run twice to get the fstab entry changed. Boot-Repair does edit fstab with defaults so it can edit it.

---

### Post by SuperFreak on 2016-02-21
Thanks OldFred

---

