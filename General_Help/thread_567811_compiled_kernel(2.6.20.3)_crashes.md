---
title: "compiled kernel(2.6.20.3) crashes"
date: 2007-10-05
forum: General Help
---

### Post by babun@intoto.com on 2007-10-05
Hi,

I have compiled the kernel & booted the compiled kernel. The new kernel panics while booting & throws  the following errors:

modproble: FATAL: Could not load /lib/modules/2.6.20.3-ubuntu1/modules.dep: No such file or directory
mount: unknown filesystem type 'devfs'
umount: devfs: not mounted

Please let me know how to get over this issue..

More details:
-----------------
I have downloaded the source from:
[http://launchpadlibrarian.net/7331991/linux-source-2.6.20_2.6.20.orig.tar.gz](http://launchpadlibrarian.net/7331991/linux-source-2.6.20_2.6.20.orig.tar.gz)

And followed these steps to compile the kernel (as per the README file in the downloaded tar):
    - untar the source
    - cd to linux source directory 
    - make 0=/home/user/build/kernel menuconfig (left to defaults)
    - make 0=/home/user/build/kernel
    - sudo make 0=/home/user/build/kernel modules_install install
    - cd /boot
    - mkinitrd -o initrd.img-2.6.20.3-ubuntu1

BY this time, I have vmlinuz-2.6.20.3-ubuntu1, Syetm.map-2.6.20.3-ubuntu1 and initrd.img-2.6.20.3-ubuntu1 created in /boot partition. Also in /boot/grub/menu.lst, an entry was created automatically:

menu.lst entry:

title		Ubuntu-VRF, kernel 2.6.20-3-generic
root		(hd0,7)
kernel		/vmlinuz-2.6.20.3-ubuntu1 root=UUID=84f17f5b-b898-4e8d-8a35-ae3c87a06945 ro splash
initrd		/initrd.img-2.6.20.3-ubuntu1


fstab contents:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda10
UUID=84f17f5b-b898-4e8d-8a35-ae3c87a06945 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda8
UUID=6e777a21-6517-46a0-bea5-35a74d288f3d /boot           ext3    defaults        0       2
# /dev/sda1
UUID=84CC-4CF9  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=8f3a5662-7f8c-479c-8c3e-43b5ac5c6875 /media/sda2     ext3    defaults        0       2
# /dev/sda3
UUID=e7fab587-ab31-46a2-94d8-9c357461ba35 /media/sda3     ext3    defaults        0       2
# /dev/sda5
UUID=fbb8b85e-0d0e-4beb-a75f-8dd79e73bc22 /media/sda5     ext3    defaults        0       2
# /dev/sda6
UUID=9d064b06-7d26-45f5-9061-ea026b0275c5 /media/sda6     ext3    defaults        0       2
# /dev/sda7
UUID=ff015f55-d4c7-4cc6-817a-3ec157ec166e none            swap    sw              0       0
# /dev/sda9
UUID=4c4c615f-98aa-4f43-87b0-7a828f21a635 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

           
Please help in identifying the issue.


Thanks,
Babu

---

### Post by 5-HT on 2007-10-05
> **babun@intoto.com said:**
> Hi,


modproble: FATAL: Could not load /lib/modules/2.6.20.3-ubuntu1/modules.dep: No such file or directory 
You'll need to run 'depmod' for the appropriate kernel version (sudo depmod <version>) to generate the modules.dep file.
> **babun@intoto.com said:**
> 
mount: unknown filesystem type 'devfs'
umount: devfs: not mounted 

Udev replaced devfs quite a bit ago. This shouldn't be causing a panic, but if you'd like it to go away remove any devfs support in your .config 

BTW: There is a much easier  "Ubuntu Way" to roll your own kernel: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

cheers,

---

### Post by babun@intoto.com on 2007-10-05
Hi, actually the file /lib/modules/2.6.20.3-ubuntu1/modules.dep is already available. But still this error is coming. May be, it is that there are some mounting issues at boot time ?

---

