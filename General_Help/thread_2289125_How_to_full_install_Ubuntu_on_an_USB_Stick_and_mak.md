---
title: "How to full install Ubuntu on an USB Stick and make it bootable on an UEFI system?"
date: 2015-08-01
forum: General Help
---

### Post by nonsisa on 2015-08-01
I tried running it from a live USB and make the installation from there but it won't install grub no matter how I format the efi partition.

Is there a guide that I can follow except this one [http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware/](http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware/) or can anyone guide me through the process, so that it will work?

thanks in advance!

---

### Post by oldfred on 2015-08-01
If UEFI full install to external device you have to manually copy /EFI/ubuntu folder back to efi partition on external drive from sda's ESP. And if USB bootable, you then also have to copy shimx64.efi into /EFI/Boot as bootx64.efi.

External devices only boot from ESP using /EFI/Boot/bootx64.efi. And grub or shim always look for the tiny grub.cfg that just refers to the real grub.cfg in your install in /EFI/ubuntu. 
So you need both in ESP on flash drive
/EFI/Boot
/EFI/ubuntu

I have yet to get grub to install anywhere other than the ESP on sda. And my default install is there, so it overwrites it. But as long as grub version is same the only difference is the grub.cfg in /EFI/ubuntu. So I have that well backed up or now know how to edit it with correct partition to find grub.cfg in correct Ubuntu install.

I just mounted my full install. My efi on flash drive is labelled efi64, so I know it is not my efi on my hard drive.
 ```
fred@trusy-ar:/media/fred/efi64/EFI$ ls -l Boot
total 2260
-rw-r--r-- 1 fred fred  958328 Apr  8 20:25 bootx64.efi
-rw-r--r-- 1 fred fred 1355736 Oct  8  2014 shimx64.efi
fred@trusy-ar:/media/fred/efi64/EFI$ ls -l ubuntu
total 3428
-rw-r--r-- 1 fred fred     126 Apr 24 04:19 grub.cfg
-rw-r--r-- 1 fred fred     126 Apr 24 00:25 grub.cfg~
-rw-r--r-- 1 fred fred  958328 Apr 24 00:25 grubx64.efi
-rw-r--r-- 1 fred fred 1264848 Apr 24 00:25 MokManager.efi
-rw-r--r-- 1 fred fred 1276984 Apr 24 00:25 shimx64.efi
fred@trusy-ar:/media/fred/efi64/EFI$ cat ubuntu/grub.cfg
search.fs_uuid c9aa0b01-e786-4b17-930a-fa6bedc785d2 root hd2,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

The hd2 is probable incorrect as when directly booting drive it always is hd0. But UUID is correct for my flash drive's partition.

---

### Post by nonsisa on 2015-08-01
Thanks olfred for the information. That means it is not possible to have an external efi partition on a flash drive if I read correct?

Somehow in Legacy mode things wear a little easier. Umpf

---

### Post by yancek on 2015-08-01
I would suggest that you wait for oldfred or someone more knowledgeable to verify this but, the way I read his quote below, you need to copy files from the internal EFI partition to an EFI partition on your external usb drive.

> If UEFI full install to external device you have to manually copy  /EFI/ubuntu folder back to efi partition on external drive from sda's  ESP.

---

### Post by nonsisa on 2015-08-01
I tried it but could not find the efi folder running the live edition.

---

### Post by oldfred on 2015-08-01
When ever you install grub it copies into the ESP on sda. You should have a /EFI/ubuntu folder in sda, if it fully installed to the external drive. That is what you want to copy to sdb or whatever flash drive is.

Grub can be created, but I have never tried that. It is just easier to copy the installed version from sda.

---

### Post by nonsisa on 2015-08-02
Do you mean with sda an installation on the hard drive?

It wont let me install the efi folder on the usb. I have no clue why. I tried to install the EFI folder on sde1 but it didn't.

---

### Post by sudodus on 2015-08-02
If you want a stable portable system, that boots in UEFI mode as well as  BIOS/CSM mode, and in 64-bit as well as 32-bit computers, you can try

[One pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682").

If you want a pendrive with a live **and** an installed system, that works in UEFI and BIOS mode, you can try

[A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode]("http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506")

---

### Post by oldfred on 2015-08-02
An ESP - efi system partition does not have to be installed like the MBR with BIOS. You can back it up and restore it just by copying it. You can also move it if installed to incorrect drive. You just need to copy from sda to sde ESP.

I have not tried sudodus' installers, but they look like good choices for those who do not want to do it all themselves.

---

