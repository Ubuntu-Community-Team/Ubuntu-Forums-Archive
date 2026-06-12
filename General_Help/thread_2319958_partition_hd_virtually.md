---
title: "partition hd virtually"
date: 2016-04-08
forum: General Help
---

### Post by sorb_ciren on 2016-04-08
Is possible partition HD virtually(without formatting again) on Ubuntu?

---

### Post by nerdtron on 2016-04-09
Can you explain more on what you're trying to achieve?
I think you have a large Ubuntu partition, you want to shrink this partition and make create a new partition with the space you shrinked? Is this assumption correct?

---

### Post by sorb_ciren on 2016-04-09
> **nerdtron said:**
> Can you explain more on what you're trying to achieve?
I think you have a large Ubuntu partition, you want to shrink this partition and make create a new partition with the space you shrinked? Is this assumption correct?

Yes.
I formatted my PC using my HD entire, now I want to create another partition for dual-boot.

---

### Post by Bucky Ball on 2016-04-09
Welcome. Boot from the install media> Try Ubuntu> once at the desktop launch Gparted> shrink or enlarge your partitions as you want. 

Not sure what 'virtual' partitioning is. This is a standard method. :-k :)

For future reference and to increase you chances of support, you might want to have a look at the pink 'Fastest way to get your question answered' link in my signature at the bottom of this post. Good luck.

---

### Post by grahammechanical on 2016-04-09
As part of the process of creating a partition you will need to set a  file system format. That will not prevent you from installing an OS into  that partition. The installer will create its own file system (format).  If it is Windows that you wish to install in that partition you may  find that first you have to format the partition to a Windows file  system using a Windows utility and then the Windows installer will see  the partition and allow you to install Windows into it.

Use Linux tools with Linux partitions & Windows tools with Windows partitions.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Regards

---

