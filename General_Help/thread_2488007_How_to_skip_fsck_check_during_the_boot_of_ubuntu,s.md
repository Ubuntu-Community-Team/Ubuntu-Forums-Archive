---
title: "How to skip fsck check during the boot of ubuntu,since it uses SystemD"
date: 2023-06-20
forum: General Help
---

### Post by marietto2008 on 2023-06-20
Hello.

I would like to upgrade the kernel and I want to enable KVM on my old but still functional "Samsung Chromebook ARM model XE303C12 SNOW" because later I want to virtualize FreeBSD with qemu and kvm. I've started following this tutorial :

[http://www.virtualopensystems.com/en/solutions/guides/kvm-on-chromebook/](http://www.virtualopensystems.com/en/solutions/guides/kvm-on-chromebook/)

As you can see,they used Ubuntu 13.04 as userland. No,I don't want to run such an old ubuntu version ! Actually my problem is that only 2 times over 10 tries my chromebook is able to boot correctly with the same setup. I've also completely erased the sd card with sudo dd if=/dev/zero of=/dev/mmcblk1 status=progress bs=2M but very rarely it wants to boot. I don't understand where the error is. When I insert the sd card into the slot it beeps and it prepares itself to boot chrome OS from the internal memory,not Linux from the sd card.

The problem could be systemd or whatever does that,to check and fix disk errors because it does not support natively chrome os disk partitions flags. So it may break those flags after the first boot. So,I want to ask if there is a method that stops systemd or whatever to check and fix disk errors.

Please give a look at this site :

[https://my.esecuredata.com/index.php?/knowledgebase/article/110/skip-or-permanently-bypass-fsck-check-on-linux](https://my.esecuredata.com/index.php?/knowledgebase/article/110/skip-or-permanently-bypass-fsck-check-on-linux)

where it says :

Update: If your OS uses SystemD, the fsck check is unskippable during boot.

So,it seems that I can't skip the checking on a OS that uses systemd like ubuntu. Is this true ? thanks.

---

### Post by MAFoElffen on 2023-06-20
Well, yes, you 'can' skip it, but do you really want to?

In the fstab doc's, in explaining the fields of the fstab line, there are 6 fields, that link says to change the last 2 fields, but you only have to consider and change the sixth field. 

The fifth field was for Pass (Backup), which was old and not really used anymore. The valid values are 0 & 1, with 0=skip, and 1=backup. The only value I have used for this in recent Linux is "0".

The sixth field is the File Check (Pass or fsck) field. The valid values are 0, 1, or 2. With 0=skip, 1=fsck on root, and 2=fsck on other than root.

From the Doc's:
```

Pass

In the last field, we need to write the file system check order, also known as the fsck order. This field takes 
only three values 0, 1, and 2. The value 0 is for not checking the file system and pass, 1 should be set for 
the root filesystem, and all other partitions should be set to 2. If you do not provide any value, 0 will be 
selected by default.

```
When it says "with SystemD", it is saying that if you have a system with SystemD, which is most all current Linux, no matter which Distro... But I think they are wrong in the description of that... I feel that should be rather, "any recent Linux Kernel". Because if you boot any recent Linux Kernel with the "fastboot" kernel boot option, then it will tell the kernel to skip the fsck check on that boot. 

***
The reason I ask if you really want to, is that if there is a power outage or if the system locks up and you have a hard reboot, sometimes that will cause file corruption or orphaned inodes, that is corrected during the boot process by that setting in the fstab line. See where that may save you? Otherwise, if not there, then you would have to do an offline, manual fsck on that partition.

Then again, 'fsck' only works on UFS Type filesystems, which is most Linux filesystems, with just a few exceptions (ZFS and BTRFS). It will also not work on NTFS, but that is not a Linux filesystem.

---

