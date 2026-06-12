---
title: "Want To Re-install Ubuntu's GRUB2"
date: 2017-07-25
forum: General Help
---

### Post by tb75252 on 2017-07-25
I am running Ubuntu 16.04 LTS, 64-bit.

Today I installed on the same HD (different partition) Fedora 26.  Fedora installed its version of GRUB2 to /dev/sda and got rid of Ubuntu's one.  It did it without giving me a choice...  I like Ubuntu's version of GRUB2 better.

How do I re-install the Ubuntu version of GRUB2 to /dev/sda?  Obviously, it has to be re-installed in such a way that its menu will allow me to launch either Ubuntu or Fedora.

---

### Post by oldfred on 2017-07-25
UEFI or BIOS?

BIOS:
You can from Fedora boot into Ubuntu?
If so, just install Ubuntu's grub to MBR.
But did you let Fedora use its default LVM? 
Most dual/multi-booting suggest using just a standard ext4 partition like Ubuntu. 
If LVM, you have to add the LVM drivers back into Ubuntu & mount the Fedora partition for Ubuntu's os-prober to find the Fedora install.

 # to find an LVM install from a non-LVM install
sudo apt-get install lvm2
sudo vgchange -a y
sudo update-grub 

#reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub 

Not sure how Fedora works, in Ubuntu major updates will reinstall grub to MBR, in Ubuntu you can change a setting to not have it reinstall. Or just plan on fixing Ubuntu after Fedora updates.

If UEFI, just change boot order either in UEFI or with efibootmgr.

---

