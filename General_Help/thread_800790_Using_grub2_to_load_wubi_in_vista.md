---
title: "Using grub2 to load wubi in vista"
date: 2008-05-20
forum: General Help
---

### Post by bean123 on 2008-05-20
Vista support boot file up to 32K, which is big enough for a customized grub2 kernel. Therefore, we can skip the real mode loader grldr.mbr altogether.

Download address:

[http://grub4dos.sourceforge.net/grub2/grub2-2008-05-20.iso.bz2](http://grub4dos.sourceforge.net/grub2/grub2-2008-05-20.iso.bz2)

This is the grub2 live CD image using the latest cvs code. To use it in harddisk, just extract the files to one of your ntfs/fat partition. The files in the root directory are boot files, here is some explanation:

g2ldr.mbr and g2ldr: This corresponds to old booting method, which rely on g2ldr.mbr to load the real kernel g2ldr.

core.img: This is a multiboot image. It can be used to load grub2 from grub legacy/grub4dos.

g2ntfs.mbr: This is customized grub2 kernel that have ntfs support. It can scan all your ntfs partition for /boot/grub folder, so don't worry about copy to the wrong partition/drive.

g2fat.mbr: This is very similar to g2ntfs.mbr, expect that it support fat instead of ntfs. If you copy /boot/grub to FAT partition, then you need this one.

For those of you that experience long delay at the real mode loader like help_me_please, you can try this one. Just copy /boot/grub and g2ntldr.mbr to your C:\ partition, then use bcdedit.exe to add a new entry for g2ntfs.mbr. If you don't know how to use bcdedit, just copy it over wubildr.mbr. (remember to save the original one, thought)

BTW, ago, can you provide a boot menu for grub2 ? I don't know the kernel parameters for loading wubi.

---

