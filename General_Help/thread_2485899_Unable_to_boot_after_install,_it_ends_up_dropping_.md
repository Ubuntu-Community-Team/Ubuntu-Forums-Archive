---
title: "Unable to boot after install, it ends up dropping to the BusyBox environment"
date: 2023-04-13
forum: General Help
---

### Post by rent63 on 2023-04-13
I have installed ubuntu on my disk but I am unable to boot, the last one I get is "ALERT! /dev/sda2 does not exist. Dropping to a shell!" I have attached an image all the lines that I get one the screen. Any help would be appreciated.

Here is the link to the image of the lines: [https://ibb.co/hFmkHt0](https://ibb.co/hFmkHt0) (I tried using insert image but it was not working)
[IMG]https://ibb.co/hFmkHt0[/IMG][IMG]https://ibb.co/hFmkHt0[/IMG]

---

### Post by tea for one on 2023-04-13
The info on this site may help [https://ostechnix.com/how-to-fix-busybox-initramfs-error-on-ubuntu/](https://ostechnix.com/how-to-fix-busybox-initramfs-error-on-ubuntu/)

Alternatively, you can boot into a live session (i.e. Try Ubuntu) and supply a boot-repair report.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
2nd option has full details.

---

### Post by yancek on 2023-04-13
Your post indicates that you just installed Ubuntu so we will expect that you have not been able to boot it since the install, is that correct?
You don't indicate whether you have another OS installed nor whether you have more than one drive?  Also, is this an EFI install or a Legacy/CSM install? (Do you know what those terms mean?)

The message is very explicit.  The bootloader is looking for a device named /dev/sda2 on that partition (sda2 is second partition on first drive) and can't find it.  You could get that information by booting the Ubuntu install USB and from a terminal, running either sudo fdisk -l or sudo parted -l to List the partitions.  The simplest way to get comprehensive information needed is to run the boot repair script suggested using the 2nd option (ppa) and running it after selecting Create BootInfo Summary Report.  Do not try any repairs.

---

### Post by rent63 on 2023-04-14
Hi, yes I have not been able to boot since install however funny thing is that I had ubuntu on this recently but I wiped it to reinstall it again, this is also a legacy install.

[https://ibb.co/MczQrxX]("https://imgbb.com/")

---

### Post by tea for one on 2023-04-14
> **rent63 said:**
> Hi, yes I have not been able to boot since install however funny thing is that I had ubuntu on this recently but I wiped it to reinstall it again, this is also a legacy install.

It looks like a UEFI installation because you do not have a BIOS Boot partition.
sda1 is 512M EFI System
sda2 is Linux filesystem 297.6G

If you have PC boot menu via a dedicated key (i.e. F2, F10 etc), can you boot in UEFI mode?

---

