---
title: "Ubuntu 12.04 Boot Issue"
date: 2012-12-15
forum: General Help
---

### Post by mxant on 2012-12-15
I have a Lenovo g580 Laptop. I had dual boot ubuntu 10.04 and ubuntu 12.04. I installed ubuntu 10.04 first and ubuntu 12.04 afterwards. I wanted to delete ubuntu 10.04 partition hence used gpart to delete the partition. Then I follwed this [link]("http://opensource-sidh.blogspot.in/2011/06/recover-grub-live-ubuntu-cd-pendrive.html") and re-installed grub on /dev/sda5 where my ubuntu 12.04 is installed. I rebooted the machine.

But I could not able to boot into ubuntu partition. My laptop is first trying for PXE installation (which is in the bottom-most position in the boot order. after CD/DVD and Hard drive), failing, and asking me to change the boot order.

I could not find out what the problem is.Also I don't want to re-install. Please help me guys.

---

### Post by grahammechanical on 2012-12-15
The last Ubuntu installed puts its Grub into the MBR (Master Boot Record) of the hard disk. So, the Grub menu that you were seeing was the Grub menu of 12.04. After deleting the 10.04 Ubuntu you could have still booted into 12.04 Ubuntu and run

```
sudo update-grub
```

That would have reconfigured the 12.04 Grub configuration file which would have removed the option to load Ubuntu 10.04.

You machine is trying to boot using PXE because it cannot find an operating system on CD/DVD or on the hard disk. The BIOS searches for an operating system on each of the devices that are listed until it finds one. Or not in your case.

Are you sure that you deleted the 10.04 partition and not the 12.04 partition? It is my guess that Grub is not in the MBR of the hard disk.

If you only have one hard disk then the command is:

```
sudo grub-install /dev/sda
```

Perhaps you installed Grub into a partition - /dev/sda5?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

Regards.

---

### Post by mxant on 2012-12-15
I just checked. I definitely have deleted ubuntu 10.04 partition.
I installed Ubuntu 10.04 on my primary partition. and ubuntu 12.04 on my extended partition. Now I have deleted my primary partition. Is it causing the boot loader to go for pxe installation?

---

### Post by supremedalek on 2012-12-15
Grub itself should be on the beginning of the hd, so it is one of the first things that will be hit during the boot. Then it can tell where the OS is. That is why grahammechanical said to install grub in /dev/sda.

If it is going straight to pxe boot, it is not finding grub. If it did find grub it would start doing some grubbing thingies and the curl into a ball and cry because it cannot find the partition where the OS is.

---

### Post by Rexilion on 2012-12-15
> **supremedalek said:**
> Grub itself should be on the beginning of the hd, so it is one of the first things that will be hit during the boot. Then it can tell where the OS is. That is why grahammechanical said to install grub in /dev/sda.

If it is going straight to pxe boot, it is not finding grub. If it did find grub it would start doing some grubbing thingies and the curl into a ball and cry because it cannot find the partition where the OS is.

But if that is true, wouldn't he be seeing at least some part of GRUB (i.e. stage 1) instead of the BIOS skipping the disk?

---

