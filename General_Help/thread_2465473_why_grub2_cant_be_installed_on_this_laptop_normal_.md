---
title: "why grub2 cant be installed on this laptop normal way"
date: 2021-08-03
forum: General Help
---

### Post by igor-uby on 2021-08-03
I have acer es1-533, and i have to use this solution of setting up grub2 on my laptop

[https://askubuntu.com/a/876153](https://askubuntu.com/a/876153)


Because during normal installation, if i allow bootloader to be installed the way installer installs it, it just freezes

But i dont know what is reason for this, what this code accomplishes that installer doesnt do?

What is special i'm missing here, that causes normal installed to hang (and whole PC to completely just freeze, until force shutted down)?

In this answer, he just created efi folder manually, manually mounted kernel and  devices, loaded some efivars kernel modules, and reinstalled grub on /mnt mount point (where all these mounted points are), and update-grub, to make grub update with OS entries
And finally made it bootable, by renaming it in EFI partition to bootx64.efi

I wish to find root problem for this, and maybe to make it to install it normally.
BIOS updates don't work, as reported by other users, in those forums

---

