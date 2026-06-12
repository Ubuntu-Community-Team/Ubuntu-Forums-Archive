---
title: "Uninstall Ubuntu 16.04 with one partition"
date: 2017-02-27
forum: General Help
---

### Post by batmanwayne32 on 2017-02-27
I have a HP laptop, i5 2.5 GHz with 4 GB RAM and a single 128 SSD. I have a dual boot of windows 10 and Ubuntu 16.04 but I want the Ubuntu gone for good. Anyone can help?

---

### Post by RobGoss on 2017-02-27
Since you are using Windows you can delete the Ubuntu partitions and  reclaim the unallocated space

Beware that once this is done you may not be able to boot in to your Windows desktop, the reason for this is because when you installed Ubuntu boot loader it was installed on the Windows MBR partition so you will need to reinstall the boot loader for Windows

I don't have much  experience doing that maybe someone else can advise you how to accomplish this

---

### Post by batmanwayne32 on 2017-02-27
I have only one partition on Windows, and it contains the Ubuntu folder, I don't have any other partitions

---

### Post by RobGoss on 2017-02-27
Are you dual booting your system?

If you were using grub to dual-boot (most probably), then you may need the Windows CD to fix the boot manager and make Windows 10 bootable again

---

### Post by Impavidus on 2017-02-28
If it's an uefi system, you can set the boot order to Windows first. While running Windows, you can remove the Ubuntu partitions and remove the Ubuntu files from the efi partition. This would be the case for most newer computers, in particular those that came preinstalled with Windows 8 or 10.

If it's a bios dual boot, you must first reinstall the Windows boot loader to the master boot record, making Ubuntu unbootable. Then start Windows and use that to remove the Ubuntu partitions.

You say you have one partition, for Windows, with an Ubuntu folder. That suggests a wubi system, which is incompatble with uefi and no longer supported by Ubuntu. In this case there should be an uninstaller for Ubuntu available in Windows.

---

