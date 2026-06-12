---
title: "Dual Booting"
date: 2015-10-13
forum: General Help
---

### Post by fernedingd on 2015-10-13
Hi guys,
At first: I know, that questions like this where already posted here, but I still haven't fount a solution for my problem.

I am using Ubuntu for ~1 year and - because I'm studying Information Technology , specialized in IT Security, soon and want to train - want to install Kali Linux alongside Ubuntu now. The problem is, that I am not very experienced in dual booting two distributions.

My Questions:

• How do I create a second boot partition?

• How big should the partition be? (Is the space just for the OS and the space for Data is shared (I would give it like 10/15 GiB), or should it be as much as possible (half of the HDD)?

• Ist the installation progress the same as installing ist as the main OS or is it special?

---

### Post by yancek on 2015-10-13
> How do I create a second boot partition?

Why would you want to?  You don't need a boot partition for either system.  You would probably be better off installing Kali to a flash drive.  That is explained in detail along with other documentation at the Kali site below which also explains how to create a 'persistent' install and a regular install.

[http://docs.kali.org/](http://docs.kali.org/)

Not sure why you would want to share data with Ubuntu given the purpose of Kali?

---

### Post by Dennis N on 2015-10-13
> My Questions:

&#8226; How do I create a second boot partition?

&#8226; How big should the partition be? (Is the space just for the OS and the space for Data is shared (I would give it like 10/15 GiB), or should it be as much as possible (half of the HDD)?

&#8226; Ist the installation progress the same as installing ist as the main OS or is it special? 


When I install several OS on the same disk, I allow 25-30 GB for each OS partition, mounting each at /. I do not create a separate boot partition, or a separate home partition. I do create a data partition separate from the OS partitions for my data files that I want to access from any of the installed systems.

The second OS should be installed in the same mode (UEFI or BIOS) as the first OS. I don't know the Kali installer, so can't tell you anything about the actual process.

---

### Post by grahammechanical on 2015-10-13
I do not install with a separate boot partition. If I did I would not use the same boot partition for different distributions of Linux. Kernels are put in the boot partition and the different distributions might be running different Linux kernels. One thing is for sure. That boot partition will soon get filled with two distributions adding updated kernels from time to time.

Regards.

---

