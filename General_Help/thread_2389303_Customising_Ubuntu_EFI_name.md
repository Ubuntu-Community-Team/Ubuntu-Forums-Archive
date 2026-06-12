---
title: "Customising Ubuntu EFI name"
date: 2018-04-14
forum: General Help
---

### Post by lizard2014 on 2018-04-14
I am building my own Ubuntu-based ISO. I want to change the EFI entry name from "Ubuntu" to something else. I know this can be done by deleting the EFI entry and creating a new one with the efibootmgr command, but I want to change that in the ISO itself so that anyone who installs from my ISO gets my own EFI entry name displayed instead of "Ubuntu". How to do that? (I have chrooted into the ISO).

---

### Post by oldfred on 2018-04-15
I think you need to build your ISO with standard grub2, not Ubuntu's grub2.

I also have wanted to change name in UEFI as I have multiple Ubuntu installs and wanted separate entries.
In looking at grub they changed the one entry for efi_distributor =  to every place it is used to "ubuntu" or many entries thru out grub. In both grub and multiple grub patches at compile time. I have never compiled grub and I think it was 1981 the last time I compiled anything.

Standard grub2.

 cd grub-2.02
./util/grub-install.c:      efi_distributor = bootloader_id;
 /* The EFI specification requires that an EFI System Partition must

  contain an "EFI" subdirectory, and that OS loaders are stored in
 subdirectories below EFI.  Vendors are expected to pick names that do
 not collide with other vendors.  To minimise collisions, we use the
 name of our distributor if possible.
  */
  char *t;
  efi_distributor = bootloader_id; 

Grub distributor is in /etc/default/grub.

---

