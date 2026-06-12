---
title: "Unable to restore Windows boot sector using dd"
date: 2006-12-07
forum: General Help
---

### Post by jamadagni on 2006-12-07
**Aim:** to restore a working Windows installation on /dev/sda1 using tar and dd.

**The short story:**

1. tar | gzip the contents of sda1 and save it to another safe partition (or DVD).
2. dd if=/dev/sda1 of=~/sda1-bootsector bs=512 count=1
3. <something happens to crash the Windows installation>
4. reformat the partition using mkdosfs.
5. tar | gunzip from the backup.
6. dd if=~/sda1-bootsector of=/dev/sda1 bs=512 count=1

This drops me to a GRUB commandline when I try to boot back into Windows and does not start Windows as expected. Why? What did I do wrong?

**The long story:**

I am trying to make a backup image of my Windows installation partition sda1 using some Linux utility so that I can simply restore a clean image and get working, whenever I have to reinstall Windows.

I have successfully used partimage, but it has one big bug: it will not restore to a partition that is smaller than the original partition from which the image was created even if the image is smaller than (and hence can be contained within) the target partition.

So I thought about just doing a tar.gz of the contents of sda1 and write it to a DVD. But that has a problem that it does not store the Windows bootloader which lies in the boot sector of sda1.

When the partition contents are merely removed by rm -Rf * and the boot sector is untouched, then trying to boot to that partition via GRUB gives "NTLDR missing" which is the Windows bootloader's error message. If the NTLDR file is there, then that startup will go ahead without a problem.

But when the partition is formatted using mkdosfs or something else (I tried BootIt NG) then just restoring the first 512 bytes of the partition using dd and the backup does not give me back the NTLDR missing error. Instead, I get a GRUB commandline when I tried to boot to the Win XP GRUB item. 

Furthermore when Kubuntu boots and tries to mount the partition as it is listed in fstab, it throws out the following error:

```
[17179621.500000] FAT: Filesystem panic (dev sda1)
[17179621.500000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[17179621.500000]     File system has been set read-only
```

I don't know why this is happening or what to do now. Can anyone help?

---

