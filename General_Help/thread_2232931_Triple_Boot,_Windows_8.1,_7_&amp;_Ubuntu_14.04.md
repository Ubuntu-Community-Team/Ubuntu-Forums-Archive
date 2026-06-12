---
title: "Triple Boot, Windows 8.1, 7 &amp; Ubuntu 14.04"
date: 2014-07-05
forum: General Help
---

### Post by spacetimecowboy on 2014-07-05
Good day one and all.

I have a new machine with Windows 8.1 installed.

I would like to install Windows 7 and Ubuntu 14.04.

I have a clear guide to dual booting 7 and 8.1 but wonder how Windows Boot Manager will respond to a Grub2 install

Ideally, I am imagining that my boot order will be Grub 2 offering a choice of Ubuntu or Windows, followed (if selecting Windows) by the Windows Boot Manager with the choice of 7 or 8.1, but I am not experienced in this area.

I have bootable media for W7 and Ubuntu and am just unsure which would be the best order to install them in, how to order the partitions, and how to establish an optimal and healthy boot environment.

Any advice would be gratefully recieved,

Thanks

---

### Post by yancek on 2014-07-05
I'm not really that familiar with bootloader on newer windows so I'm not sure how much the windows 8 bootloader is different from windows 7, if at all.  Windows bootloadees have always been backward compatible meaning that if you were to install two different versions, you installed the older first and the newer detected the older.  If you did the reverse it would require manual intervention so if you already have windows 8, I would suggest you investigate the two bootloader similarities and differences.

I'm not sure what you mean by how the windows boot manager will respond to Grub since a default windows system can't even read a Linux filesystem.  Basically, it won't respond at all, it won't recognize it.

If you have a windows 8 computer, you also have to deal with Secure Boot, FastBoot, UEFI and GPT partitioning.  I know very little about those so just wait and someone else more familiar will come by to help.

---

