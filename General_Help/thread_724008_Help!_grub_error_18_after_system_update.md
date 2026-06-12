---
title: "Help! grub error 18 after system update"
date: 2008-03-14
forum: General Help
---

### Post by evozero on 2008-03-14
Hi All, Can anyone help me with my setup please?
I have 7.10 running fine for months, i have always applied the new updates and never had a problem.
Until a now. when i boot 2.6.20-16 i get error 18: selected cylinder exceeds maximum supported by bios
i can boot 2.6.20-15 without a problem, both kernels are on the same drive?
its a 40GB IDE drive with 8.2GB free
Any ideas to fix this without a fresh install?
if i have to reinstall how do i save my opera and thunderbird data, accounts,bookmarks etc?
below is my menu.lst, i cant see anything wrong with it?

Many Thanks in advance
Ian


title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d48dacbe-0b6d-4a0a-b54e-9c9f1856fffb ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d48dacbe-0b6d-4a0a-b54e-9c9f1856fffb ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d48dacbe-0b6d-4a0a-b54e-9c9f1856fffb ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d48dacbe-0b6d-4a0a-b54e-9c9f1856fffb ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

---

### Post by wblancqu on 2008-03-14
"Error 18

Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

The kernel itself does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem.
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot."

Found at [http://wiki.linuxquestions.org/wiki/GRUB]("http://wiki.linuxquestions.org/wiki/GRUB")

---

### Post by Herman on 2008-03-14
I agree with wblancqu in the post above.
Probably you were just lucky at first that your kernels happened to have been placed close to the start of your hard drive. In the last update your newest kernel probably was placed outside the limit, and that's why you're having this booting problem now.

Here is what you can do, [How to make a separate /boot partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition").-contains the Linux kernel, initrd.img and GRUB files.

I hope that will be explained well enough for you to be able to follow, if not then please don't be shy to ask more questions in this thread and we (meaning I or someone else in this forum), will help you.

Regards, Herman :)

---

### Post by danwood76 on 2008-03-14
It might be that the initrd hasnt been created causing funny issues.
I know the latest update on my laptop left my grub config messed up due to it not linking to the initrd.

When logged in could you post the contents of your menu.lst?
```

cat /boot/grub/menu.lst

```

-- edit --

sorry I started reading something else in the middle of reading this thread and missed all that,
forget my post

---

