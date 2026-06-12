---
title: "Removing grub from one of the hard drivers"
date: 2018-02-22
forum: General Help
---

### Post by renato92 on 2018-02-22
Hi everyone.

I got a small SSD and a HDD. I installed Ubuntu 17 on the SSD (home folder on the HDD) with grub on it. It was working fine and great. I decided to try the Ubuntu 18.04 beta, but it ended up installing the grub again.         
So here is the problem, if I choose to boot with the SSD first (I need to do manually everytime) it work almost fine. When I boot the HDD I get a weird grub with a graphical bug.   

My main problem is that any entry made by "grml-rescueboot" won't work (it was working fine before, I used to install Ubuntu 18). When I press enter the screens flashes and nothing else happens. This is true for both grubs (the "normal one from my SDD" and the one with the visual bug).

I was wondering if anyone could help me remove the grub on the HDD that has a visual bug and fix grml-rescueboot.

I attached the visual bugged grub and the GParted print from both drivers. Thanks.

---

### Post by oldfred on 2018-02-24
We do not recommend removing grub. 
But you can just reinstall a working grub, if desired.
With two drives and two installs, better to have each install have its grub in separate drives.

I notice a bios_grub on sdb. Which is required for BIOS boot with gpt drives.
Is sda also gpt partitioned? If so it also needs a bios_grub partition.

Post this:
sudo parted -l

---

