---
title: "extra partitions"
date: 2007-11-26
forum: General Help
---

### Post by nageldh11 on 2007-11-26
After testing and re-installing 7.10 (dual boot) several times I noticed I have what appears to be several extra drives and swap files.

I looked at then with GParted and other than the size (as I was changing sizes during the test installs) they all appear to have the same contents. Below is the info. Should I use GParted to remove all of the ones not mounted or active? I also notice after several installs I have what appears to be many more entries in the "dual boot" display created by GRUB. Will these clean up if I delete these partitions?

Thanks


/dev/sda3   ext3  not mounted
/dev/sda4   extended
  /dev/sda10    ext3 not mounted
  /dev/sda11    linux-swap not active
  /dev/sda6     ext3  not mounted
  /dev/sda8     ext3  not mounted
  /dev/sda12   ext3 mounted on 
  /dev/sda13   linux-swap active
  /dev/sda9    linux-swap not active
  /dev/sda7    linux-swap not active
  /dev/sda5    linux-swap not active

---

### Post by smartboyathome on 2007-11-26
Looks like you installed Ubuntu more than once and didn't get rid of the rest of them. You can get rid of them by deleting them, but you have to edit /boot/grub/menu.lst to get rid of the extra grub entries.

---

### Post by nageldh11 on 2007-11-26
Thanks for your quick response

---

