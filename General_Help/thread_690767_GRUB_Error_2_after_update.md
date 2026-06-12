---
title: "GRUB Error 2 after update"
date: 2008-02-07
forum: General Help
---

### Post by Quintium on 2008-02-07
I have issues after the latest updates. (I posted a little different post in another topic that got "solved", sorry - but I still got a problem)

I have Ubuntu 7.10 on an external USB drive and WinXP on my internal Hard drive. GRUB loads and display the boot options like it always have. If I select windows I'm able to boot just find. But for the Ubuntu option I get "Error 2: Bad file or Directory type".

If I do "find /boot/grub/stage1", "find /boot/grub/stage2", or "find /boot/grub/menu.lst" it display (hd0,0)

But if I do "find /boot/grub/vmlinuz-2.6.22-14-generic" the floopy drive makes a noise and I get "Error 15: File not found?"

I tried to boot from Live CD but unable to start up since my new graphic card (which worked fine on my installed version before the update) just suddenly make loud beeping sounds and the Live CD never boots (even tho I did get the start Ubuntu loading graphic at the beginning)

I was finally able to get "safe graphics mode" to boot. I looked in the /boot folder:

vmlinuz-2.6.22-14-generic exist
initrd.img-2.6.22-14-generic exist 

Here is menu.lst:

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=310a1846-fdfb-4520-b329-57fc16e48ea5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=310a1846-fdfb-4520-b329-57fc16e48ea5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=310a1846-fdfb-4520-b329-57fc16e48ea5 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
map		(hd1) (hd0)
chainloader	+1



(sorry for any typos and grammar - not native English :) )

---

### Post by Quintium on 2008-02-07
*bump*

---

### Post by Quintium on 2008-02-08
*bump*
More info.

In the GRUB command line after pressing c at the GRUB menu I do following:

> 
root (hd0,0)

geometry (hd0)
[it finds the partitions on the USB drive just fine]

setup (hd0)
[all steps complete successful]


Anyone, please?

---

### Post by Quintium on 2008-02-08
fdisk -lu (from boot of Live CD)

sda1 is my windows boot partition (internal HD 1)
sdb1 is an extra windows partition (internal HD 2)
sdc1 is my Ubuntu partition (external USB drive)

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x46f0f408

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312576704   156288321    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x29b529b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   312576704   156288321    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00040f2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   429690554   214845246   83  Linux
/dev/sdc2       429690555   430686584      498015   82  Linux swap / Solaris
/dev/sdc3       430686585   976768064   273040740    b  W95 FAT32


---

### Post by Quintium on 2008-02-08
Anyone?!? Please?!?

---

### Post by Sidewinder1 on 2008-02-08
I've been trying to help but I'm a noob to linux. I think it's a problem with a rewritten menu.lst. There is quite a bit of confusion on my part with linux's disk naming conventions: we have uuid then we have sda and hdb, then we have hd0,1. It's all quite a mish-mash to me. Perhaps this thread will help you solve the problem.
[http://ubuntuforums.org/showthread.php?t=690467](http://ubuntuforums.org/showthread.php?t=690467)

---

### Post by Sidewinder1 on 2008-02-08
If the above thread does not solve your problem, you might try this one:
[http://ubuntuforums.org/showthread.php?t=687714](http://ubuntuforums.org/showthread.php?t=687714)

---

### Post by Quintium on 2008-02-08
Thanks Sidewinder1. I'm also trying to understand the mish-mash as you said. Even tho my USB drive is /dev/sdc then GRUB wants it as HD0 to work right when I installed Ubuntu originally (and worked well until this last update!)

I looked at your suggestions and this is what I found:

> ubuntu@ubuntu:~$ sudo vol_id /dev/sdc1
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=310a1846-fdfb-4520-b329-57fc16e48ea5
ID_FS_UUID_ENC=310a1846-fdfb-4520-b329-57fc16e48ea5
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=


> ubuntu@ubuntu:/media/disk/etc$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=310a1846-fdfb-4520-b329-57fc16e48ea5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=9050DABB50DAA76E /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=EEB88B58B88B1E69 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc2
UUID=c2ab883a-a79d-4191-92dd-20695e28ab81 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0



> ubuntu@ubuntu:/media/disk/etc$ cat initramfs-tools/conf.d/resume
RESUME=UUID=c2ab883a-a79d-4191-92dd-20695e28ab81


Everything looks correct to me. I'm very confused why suddenly it will not boot and I would really hate to have to re-install Ubuntu and then go thru the update again and then again not be able to boot without knowing a possible solution.

---

### Post by confused57 on 2008-02-08
You could try a direct kernel boot:
[http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot](http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot).
see the Direct Kernel Boot Option....

I believe pressing "c" at the grub boot menu will get you to a grub prompt, then follow the directions in the above link.

---

### Post by Quintium on 2008-02-09
The problem is that GRUB is unable to find /boot/vmliunz-2.6.22-14-generic even from the GRUB prompt even tho it points to the right partition etc. And I checked.. the file is there and it is not a linked file either.

I give up. My Ubuntu experience is over.

---

