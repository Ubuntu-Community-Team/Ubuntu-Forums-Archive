---
title: "[SOLVED] Bootable Software RAID"
date: 2007-07-19
forum: General Help
---

### Post by fjgaude on 2007-07-19
I created a raid5 array using mdadm, but first copied a bootable partition, using "find - cpio", onto the set with one disk missing. All went well and after two hours the array was constructed. The box has another boot disk that works fine, with /boot/grub and menu.lst. All disks are 300G Seagate SATAs.

Question: When booting and after getting the grub menu options, what is to be the root disk, partition on the "second drive". The array is /dev/md32 and has an UUID. The disk with MBR with grub points to the grub menu on the working linear (hd0,0), single disk. Here's what I have, along with the entries that do work, in menu.lst and it doesn't boot:

```
title		Ubuntu, kernel 2.6.20-16-generic (on RAID5 /dev/md32)
root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9e917be3:365b3aef:f9346e8d:a51a8587 ro quiet splash
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/md32 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
```

The three disks in the raid are FD, raid detectable. All one-partition formatted. I've tried both UUID and /dev/md32 without success. What should be the "root"?

Also, I can't say if raid is built into the kernel, 2.6.20-16, or is a module, but it auto assembles when the other drive boots and mounts it. Anyone know?

Any suggestions to get this potentially dual-boot box to work?

Thanks,

frank

---

