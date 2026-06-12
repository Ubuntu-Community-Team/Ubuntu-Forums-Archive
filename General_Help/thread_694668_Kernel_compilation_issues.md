---
title: "Kernel compilation issues"
date: 2008-02-12
forum: General Help
---

### Post by jsvidyad on 2008-02-12
Hi

   I am running 32 bit edgy on a core 2 duo machine. I am trying to compile the linux kernel version 2.6.24(obtained from kernel.org)  on it using the instructions posted here [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) . The only deviation from the instructions was that I did not copy the config file. I did that as that did not help in previous kernel compilation attempts. Now, the kernel compiled fine and the linux-image and linux-headers deb packages were created. I installed these two packages. Now, when I try to reboot into the new kernel, the system hangs up on booting. I again tried to reboot into the recovery mode of the new kernel. Things went fine until it gave a message saying:
Begin: Waiting for root file system

Then, after waiting for a while, it gave a message saying:
Done.
ALERT! /dev/sda6 does not exist. Dropping to a shell!

Then it takes me to a shell titled BusyBox v1.1.3 where I can type some basic commands, but no filesystems are mounted. When i try to mount them manually, i get messages saying /dev/sda6 does not exist and so on.

  Can someone tell me why I am having these  problems?? I have been trying to install the kernel for the past few days with absolutely no success. The kernel does compile , but I cannot boot into these kernels and use  them.  Can someone please help me??

---

### Post by taurus on 2008-02-12
Do you still have the old kernel where you can boot with?  Maybe you specify the wrong / partition in /boot/grub/menu.lst for the new kernel.

See if you get any output of this command at a prompt.

```
fdisk -l
```

---

### Post by danwood76 on 2008-02-12
Another option is that you may not have the correct chipset drivers compiled into the kernel.
Without the chipset drivers it will find no hard disks, and so will not be able to boot.

---

### Post by Whiffle on 2008-02-12
If you didn't copy the config file, what config did you use?

---

### Post by jsvidyad on 2008-02-12
No. even the old kernel use the option root=/dev/sda6 which is what the new kernel uses

fdisk -l gives no output

I did make menuconfig and manually chose the options I wanted.

---

### Post by apetresc on 2008-02-12
> **jsvidyad said:**
> No. even the old kernel use the option root=/dev/sda6 which is what the new kernel uses

In that case it's definitely an issue of not having installed FS drivers for whatever your root filesystem is formatted as. If it's ext3, enable those from make menuconfig: ```
File systems  --->
	<*> Second extended fs support
		[*]   Ext2 extended attributes
	<*> Ext3 journalling file system support
		[*]   Ext3 extended attributes
		[*]   Ext3 POSIX Access Control Lists
		[ ]    Ext3 Security Labels
		[ ]    JBD (ext3) debugging support
```
Similarly for any other FS you may be using on /dev/sda6

---

