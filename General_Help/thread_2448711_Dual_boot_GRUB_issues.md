---
title: "Dual boot GRUB issues"
date: 2020-08-12
forum: General Help
---

### Post by su:bhatta on 2020-08-12
Hello after a long time .... Ah ! memories of learning to fix mistakes... good old days...
I have been stuck running a elementary for a long time.. blah...

Long story short... I am installing 2 OS on my laptop, OpenSuse Tumbleweed and Ubuntu 20.04. No Windows !!
I have installed them both and Ubuntu wrote its grub first and in which part of Disk i don't know !!
Opensuse wrote second and put the grub file in its own partition.I have to change boot option from BIOS to get default Opensuse to change :(

MOK screen comes up, errors show up that point (Google search, these forums) towards UEFI boot related issues...

I want to re-install the Opensuse due to issues (not only GRUB, Suse has own issues, installation?)

My question is, to get things corrected , in which part of Disk do I get Suse to write the grub?

Cheers all... any help is much appreciated.

If this is required :

```
Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: TOSHIBA MQ04ABF1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 2711528D-670B-4E2D-A1B6-4F7A965FDEB8

Device          Start        End    Sectors   Size Type
/dev/sda1        2048    1050623    1048576   512M EFI System
/dev/sda2     1050624  136218623  135168000  64.5G Linux filesystem
/dev/sda3  1949329408 1953525134    4195727     2G Linux swap
/dev/sda4   136218624  271386592  135167969  64.5G Linux filesystem
/dev/sda5   271386624 1949329407 1677942784 800.1G Microsoft basic data

Partition table entries are not in disk order.

```

---

### Post by CelticWarrior on 2020-08-12
In all UEFI systems the bootloaders reside in the ESP (EFI System Partition), your sda1.

---

### Post by oldfred on 2020-08-12
Both BIOS & UEFI, you normally select a drive like sda on where to install grub.
With UEFI, it finds & knows to actually put the grub/ubuntu boot files into the ESP - efi system partition, your sda1.

Does your UEFI boot menu show both Ubuntu and OpenSuse as boot options.
You can also see those from system with:
sudo efibootmgr -v

UEFI remembers old entries, so if name/label in UEFI changes or you have old installs that you removed there may be old entries in UEFI and old folders in ESP.

---

### Post by su:bhatta on 2020-08-12
Thanks CelticWarrior! 

> **oldfred said:**
> Both BIOS & UEFI, you normally select a drive like sda on where to install grub.
With UEFI, it finds & knows to actually put the grub/ubuntu boot files into the ESP - efi system partition, your sda1.

Does your UEFI boot menu show both Ubuntu and OpenSuse as boot options..

Yes oldfred, in UEFI Boot both Ubuntu and Suse can be chosen!

---

