---
title: "Weird problem with Gparted"
date: 2007-02-22
forum: General Help
---

### Post by phantommaggot on 2007-02-22
HI
so heres my problem

i had to do a fresh install of all my operating systems. 
Once i got windows straightened out, i decided to install Ubuntu.

so i whip out the disk and get into gparted and resize my ntfs partition from 145ish (160gb drive) to about 40, that worked fine. 

pulled up the installer, and used gparted to make a 26gig total setup (ext3 + swap) for ubuntu and install. that went great too. 

so after that was done i moved some stuff from windows to Linux and went to make a final partition (ntfs) for storage and general file swapping between operating systems. this is where the bad stuff happened

somehow it just extended my windows partition to ~124GB and said i only have 5GB free.. 

so heres my gpatred order now.
[ntfs ~122GB, ~5GB free] [ext3 ~4GB ~20GB free][swap]

heres how it should look
[ntfs 45GB] [~93GB unallocated] [ext3 24GB][swap]

windows and ubuntu both show that partition as 45GB
and windows is working fine.. 

so whats the problem??

anyways,
thanks for any help
-j

---

