---
title: "VirtualBox instance getting stuck in grub rescue"
date: 2022-10-25
forum: General Help
---

### Post by gillyhl on 2022-10-25
I tried running a boot repair on the ISO image and got this result: [https://paste.ubuntu.com/p/GrsBTpTBx2/](https://paste.ubuntu.com/p/GrsBTpTBx2/)

I've tried to follow instructions similar to this to this to get out of grub rescue: [https://linuxhint.com/grub_rescue_ubuntu_1804/](https://linuxhint.com/grub_rescue_ubuntu_1804/) but all listed volumes return a "Filesystem is unknown" error.

The volume got corrupted after I tried a resize using VirtualBox, the image is no longer corrupted but I can't get to the OS when booting. 

Any help would be much appreciated :)

---

### Post by yancek on 2022-10-25
Boo t repair doesn't show anything useful.  You indicate you ran boot repair on the iso image, is that correct?  An ISO image is read only and you won't be able to repair anything.  Not sure what you have or are trying to do.  Boot repair shows only two partitions, one which looks like it was an EFI partition (sda1) and the  second which is an Extended partition (sda2) with no logical partitions to contain data.  The link you posted explains how to repair the bootloader of an installed system, do you have that?

---

