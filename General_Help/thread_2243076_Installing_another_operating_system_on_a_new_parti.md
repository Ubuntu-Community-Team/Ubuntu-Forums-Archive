---
title: "Installing another operating system on a new partition?"
date: 2014-09-06
forum: General Help
---

### Post by billybux20 on 2014-09-06
So on my laptop I have Ubuntu 14.04 and no other current operating systems. I would like to install Windows alongside Ubuntu. 

1) Could I do this easily?
2) Would I have to use an application like Gparted to create a new partition and then install it into there?
3) I can backup all my files so would it be easier to install windows and get rid of Ubuntu, then re-install Ubuntu, and if so, how would I go about this?

Thank you for all help, it is much appreciated.

---

### Post by grahammechanical on 2014-09-06
You would need to create partitions for Windows because Microsoft does not accept that people want any other OS on their machines than Windows. 

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

From my experience of installing Windows 8 preview on a machine with Ubuntu already installed, this is what I learned.

1) We can direct Windows to install into a partition but before we try to install we must use the Windows install disk to format the partition. Then we can direct the installer to install Windows into the partition.

2) Windows will put its boot loader on the the hard disk. In fact it will put its boot loader on all hard disks in the machine. This means that afterwards you will not be able to boot Ubuntu. You will need to use something like Boot Repair to re-install the Grub boot loader. Or do it yourself from a Ubuntu live session.

How many partitions does Windows need? Will you be installing Windows 8? Does the machine have UEFI boot system or BIOS boot system? 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by magpie03 on 2014-09-06
It may or may not be easy. Depends on hardware. I do know that Windows must be installed first. Do you really need Windows? If you must, back up all your data and install Windows then install Ubuntu. If you want to use Windows 8, it will be a real challenge to set up porperly.

---

### Post by stalkingwolf on 2014-09-06
here is my experience.  Windows cant read ext partitions so it refuses to install if there are unreadable partitions.  The drive is bad dont you know.
Windows always wants to be first on the drive.  So I usually usually format the drive for windows , then install it. then use gparted (my choice) and partition the drive how i want and continue with my linux install/s.

Before wiping I copy my home folder to an external drive.

---

### Post by yancek on 2014-09-06
Windows does not have to be installed first but the problems are going to be what is posted above by grahammechincal, at least.  You will need to have at least one primary partition on which to put the boot files and if you are going to be using windows 8, that will add other compelxities.

---

