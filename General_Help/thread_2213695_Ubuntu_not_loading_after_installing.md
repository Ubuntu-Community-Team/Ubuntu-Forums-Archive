---
title: "Ubuntu not loading after installing?"
date: 2014-03-28
forum: General Help
---

### Post by ajay5 on 2014-03-28
Hello , I recently installed ubuntu along with windows 8 both in legacy mode. I have two HDDs. I installed ubuntu in the slave drive which is a GPT disk.After installation of ubuntu computer restarts and goes directly into windows 8. When i tried boot-repair using live usb it says GPT detected. Can you guys help me to solve the problem?

---

### Post by alex2e1gzy on 2014-03-28
Does your Windows 8 use UEFI? If it does - try installing Ubuntu in UEFI. I read somewhere that GPT partitions are not well supported by some BIOSs booting legacy mode.

---

### Post by fantab on 2014-03-28
> **ajay5 said:**
> Hello , I recently *installed ubuntu along with windows 8 both in legacy mode*. I have two HDDs. I installed ubuntu in the slave drive which is a GPT disk.After installation of ubuntu computer restarts and goes directly into windows 8. When i tried boot-repair using live usb it says GPT detected. Can you guys help me to solve the problem?

To boot Linux from a GPT disk in 'legacy' mode you need to have small **10Mb Unformatted Partition with 'bios_grub' flag**. Did you create one?

Post the output of:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by grahammechanical on 2014-03-28
There is something else to consider. If Ubuntu is installed on sdb (just guessing) and Grub is installed onto sdb and the machine has sda boot priority then grub will not load. And it is only Grub that will give you an option to boot either Ubuntu or Windows. The Windows boot manager will not offer to boot Ubuntu. Have you tried changing the boot priority to the hard disk with Ubuntu on?

Regards.

---

### Post by Navneet_Kumar on 2014-03-28
I think the most probable cause may be the incorrect installation og grub.so the ubuntu can be accassed from the boot options area from the BIOS menu.so re-installation of grub might resolve the problem.

---

