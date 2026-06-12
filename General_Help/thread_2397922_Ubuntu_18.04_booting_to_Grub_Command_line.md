---
title: "Ubuntu 18.04 booting to Grub Command line"
date: 2018-08-05
forum: General Help
---

### Post by momia98 on 2018-08-05
Hi, I installed Ubuntu 18.04 on my windows 10 laptop a few days ago and I've been loving it. I just finished all my customization and installed all my apps so I decided to boot into the windows partition and shrink the windows volume to give Ubuntu more space. After doing that I can't boot back into Ubuntu. It goes straight to the grub command line. It says grub not grub rescue. The windows part still works and I can "try Ubuntu" using the drive I installed it with. I've googled around and can't find any solution to this.

Any help would be appreciated.

Edit: I've opened gparted on a live Ubuntu session and the 200gb partition is showing as unallocated storage. Could my installation have been wiped?

---

### Post by oldfred on 2018-08-05
UEFI or BIOS installs?
What brand/model system?

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

