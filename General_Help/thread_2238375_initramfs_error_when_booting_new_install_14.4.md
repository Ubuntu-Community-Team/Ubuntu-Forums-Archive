---
title: "initramfs error when booting new install 14.4"
date: 2014-08-07
forum: General Help
---

### Post by Bob_Mendon on 2014-08-07
I am getting an initramfs error when booting a new install 14.4. I have not had a problem with distros based on the 14x release and can't understand the problem. I have erased both hard drives and installed the OS as directed. I have searched the various threads but I am still not understanding how to correct the problem and why I am having this particular problem. I guess its back to one of the other flavors if I can't sort this out.

The error reads, "ALERT /dev/disk/by-uuid/[series of alpha-numeric characters] does not exist.

---

### Post by Bashing-om on 2014-08-07
Bob_Mendon; Hi !

That condition is generally indicative that grub can not find it's boot files in that 2nd stage of the boot process. What might be the solution is to (re-)install grub, making sure these boot files are installed where they need to be.

Boot the liveDVD in "try ubuntu" mode, and let's take a gander at where the boot files should reside:
Post back - between code tags - the outputs of terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```
IF the hard disk(s) is partitioned in GPT, will need to install another tool to look at the partitioning.
One thing at a time, let's see what we are working with.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2014-08-07
You have two hard drives. Which one has the boot priority? That series of alpha-numeric characters is the UUID (Universally Unique IDentifier) of the partition where Grub expects to find the Linux kernel image.

Every time we install to a partition that UUID changes. When we install the installer puts Grub into the MBR/UEFI of the first hard disk (sda) by default. If another hard disk has boot priority and also an installation of Grub that has not been updated, then Grub is checking for a UUID that is not longer valid. That could be the problem.

Either change the hard disk boot priority and boot from a Grub that is referencing the new install of Ubuntu, or boot into another Linux/Ubuntu on the other hard disk and run

```
sudo update-grub
```

And see if the printout detects the new install on Ubuntu on the right partition. That will correct the UUID reference. I am assuming that you have another ubuntu install on that second hard disk.

Regards.

---

### Post by Bob_Mendon on 2014-08-07
Ok..this is weird. I figured out what was going on. I was using a USB drive to install the OS. For what ever reason Grub was writing the boot files to the USB. I reinstalled with a DVD and everything worked just fine.

---

### Post by Bashing-om on 2014-08-07
Bob_Mendon; Good deal;

All's well
[INDENT][INDENT]that ends well
[/INDENT][/INDENT]

---

