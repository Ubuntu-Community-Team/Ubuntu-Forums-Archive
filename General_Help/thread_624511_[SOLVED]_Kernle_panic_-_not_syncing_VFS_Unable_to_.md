---
title: "[SOLVED] Kernle panic - not syncing: VFS: Unable to mount root fs on unknown-block (0"
date: 2007-11-27
forum: General Help
---

### Post by ragas on 2007-11-27
VFS: Cannot open root device "UUID=..." or unknown-block (0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs onunknown-block (0,0)

I am trying to compile Linux Kernel version 2.6.16 with Mobile IPv6 support. I followed the procedure for building the kernel from [http://www.howtoforge.com/kernel_compilation_ubuntu_p2](http://www.howtoforge.com/kernel_compilation_ubuntu_p2). I successfully built the kernel image but I am getting the above error when I try to boot using that kernel. 

I did a google search on this error but could not find a definitive solution. I guess, at least in my case, this is being caused due to some module not being loaded. I dont' really know which module I might have skipped during the kernel cofiguration phase. 

Also, I was getting an error like 'minimum kernel required is 2.6.17' when I was doing a mkinitramfs. So I just modified the line MINKVER="2.6.17" to MINKVER="2.6.16" in /usr/share/initramfs-tools/hooks/udev so that an initrd image would be created for my kernel version, 2.6.16. (I did this as I have no idea what other procedure to follow for building initrd for kernel versions less than 2.6.17). I hope that this did not mess up anything, *praying*! 

Any help on how to solve the above problem would be highly appreciated. Please let me know if I need to provide any more information. 


```
My current configuration: 
-------------------------
Ubuntu Gutsy 7.10 with kernel 2.6.22-14
(running as a vm on vmware. I guess this is in no way concerned with vm as I am getting the same error on a standalone desktop with ubuntu also). 

Grub configuration
------------------
...
...
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3635ab94-cd00-4c4e-a51c-437527e94ecc ro quiet splash locale=de_DE
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3635ab94-cd00-4c4e-a51c-437527e94ecc ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.16-mipv6-2.0.2
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.16-mipv6-2.0.2 root=UUID=3635ab94-cd00-4c4e-a51c-437527e94ecc ro quiet splash locale=de_DE
initrd		/boot/initrd.img-2.6.16-mipv6-2.0.2
quiet

title		Ubuntu 7.10, kernel 2.6.16-mipv6-2.0.2 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.16-mipv6-2.0.2 root=UUID=3635ab94-cd00-4c4e-a51c-437527e94ecc ro single
initrd		/boot/initrd.img-2.6.16-mipv6-2.0.2

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


fstab
-----
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3635ab94-cd00-4c4e-a51c-437527e94ecc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=3a0e084c-c3e5-4952-baea-6b7b1d82672c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
</code>
```

---

### Post by Thyme on 2007-11-27
Hi ragas,

> VFS: Cannot open root device "UUID=..." or unknown-block (0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs onunknown-block (0

From my experience, this happens when you haven't compilled in the pata/sata drivers for you (SCSI) hdd, into your kernel.

Double check:

"Device Drivers" --> "SCSI Drvice Support"

Check the following with *:

1. SCSI Disk Support
2. SCSI CDROM Support
3. SCSI Generic Support
4. Verbose SCSI Error Handling (kernel size+- 12k)

NOTE: THey should not be modules (M) as your kernel will end up not booting.

---

### Post by ragas on 2007-11-27
Thank you very much for the reply. Thyme 
I checked my .config file and found the following were set as modules: 
CONFIG_BLK_DEV_IDESCSI=m
CONFIG_SCSI=m
CONFIG_SCSI_PROC_FS=y
CONFIG_SCSI_SPI_ATTRS=m
CONFIG_SCSI_FC_ATTRS=m
CONFIG_SCSI_ISCSI_ATTRS=m
CONFIG_SCSI_SAS_ATTRS=m

I modified the .config (ofcourse, using menuconfig) and compiled the above into the kernel now. But still the problem persists. 
Any other hints?

---

### Post by ragas on 2007-11-27
Ha! Finally my problem is solved. I took the old .config file (which came with my 2.6.22-14) and made my required changes in it to support Mobile IPv6 and built the kernel. It is working now :guitar:

I tried this method of using oldconfig previously also. But it did not work at that time. I was not doing a 'make kpkg-clean' before building the kernel. May be that was the problem. I was under the impression that the newly compiled / built files will overwrite the old ones, which was not being done I guess. 

Now, I did a 'make kpkg-clean' before building the kernel. And lo! it worked!

---

### Post by Thyme on 2007-11-27
Glad it worked Ragas :) Apologies for not replying earlier, I'm not at expert in compiling kernels so I was hoping somebody else will jump in and save the day ! Anyway, well done dude ..

---

