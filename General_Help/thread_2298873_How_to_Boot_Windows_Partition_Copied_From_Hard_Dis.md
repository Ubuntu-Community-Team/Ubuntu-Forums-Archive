---
title: "How to Boot Windows Partition Copied From Hard Disk"
date: 2015-10-14
forum: General Help
---

### Post by cobalt2 on 2015-10-14
I had Windows xp installed on a hard disk which was showing read problems, so I retrieved all the data before formatting it. I copied the Windows files to a partition inside an extended partition on this volume, and now I want to boot from Windows. I know that I will need to do 2 things in order to boot from Windows: 1) Add Windows to the GRUB boot menu & 2) The partition where Windows is currently installed will have a different UUID than the one where it was initially installed, so I need to edit the Windows equivalent of fstab in GNU/Linux, in order for the UUIDs to match. 

Could someone advise me on how to do this?

---

### Post by sudodus on 2015-10-14
Windows has protection against illegal copying, which makes it hard to make it work from a copy. It is possible to use a 'perfect' cloned copy of the HDD or a compressed image made with a cloning tool, for example Clonezilla. But if you copied the files, there will probably be problems to re-install a working system from it.

XP usually came with a CD disk. If you have one, you can make a fresh installation. But I'm afraid it will be hard to update/upgrade it because it has passed end of life (no more support, not even security updates).

---

### Post by cobalt2 on 2015-10-14
Then I will install it anew in VirtualBox. I only need to use it as a platform for running offline programs that are incompatible with Ubuntu, and I'm running it from within the VM, so security isn't an issue. 

Thanks for the advice.

---

### Post by yancek on 2015-10-14
>  I copied the Windows files to a partition inside an extended partition on this volume, 

That won't work because windows needs it's boot files on a primary partition which also needs to be marked as active bootable.  Your VBox solution is probably the easiest solution.

---

### Post by sudodus on 2015-10-14
+1 for installing XP in VirtualBox :-)

---

