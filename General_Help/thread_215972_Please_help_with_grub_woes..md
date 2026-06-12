---
title: "Please help with grub woes."
date: 2006-07-14
forum: General Help
---

### Post by tincbtrar on 2006-07-14
Hi all.

Recently I decided to install Suse 10.1....I already am dual booting Xp and ubuntu.  Up until now, I have never faced a grub problem that I couldnt fix...

Anyway, now I can only boot into xp or Suse.  My ubuntu partitions do not show up from what I can tell...the bootloading feature in Yast shows my recent Ubuntu kernel but I get a file not found, even though it is pointing to the old partiton. And when I tried to use the liveCD for ubuntu and reinstall grub my "Partition Disks" menu only shows one huge partition instead of the old partitions I had set (root,home,swap,etc.) Did Suse do this, and is there anyway to get my ubuntu partitions back?  And even more of a concern, why are my individual partitions now one huge one?

Thanks in advance.

---

### Post by Jagot on 2006-07-14
Could you post the results of this command in Terminal/Konsole:

```
cat /boot/grub/menu.list
```

---

### Post by tincbtrar on 2006-07-14
Most certainly.  Here is my grub menu.

brian:/home/brian # cat /boot/grub/menu.lst
# Modified by YaST2. Last modification on Fri Jul 14 13:47:13 EDT 2006

color white/blue black/light-gray
default 0
timeout 8
gfxmenu (hd0,4)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title SUSE Linux 10.1
    root (hd0,4)
    kernel /boot/vmlinuz root=/dev/sda5 vga=0x317    resume=/dev/sda9  splash=silent showopts
    initrd /boot/initrd

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/sda7 ro
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)
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
# defoptions=
## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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
## ## End Default Options ##
###Don't change this comment - YaST2 identifier: Original name: Debian GNU/Linux, kernel 2.6.15-26-686 (/dev/sda8)###

title Debian GNU/Linux, kernel 2.6.15-26-686
    kernel (hd0,6)/boot/vmlinuz-2.6.15-26-686 root=/dev/sda7 ro
    initrd (hd0,4)/boot/initrd
    boot

###Don't change this comment - YaST2 identifier: Original name: Linux other 1###

title Windows XP Professional
    chainloader (hd0,0)+1

###Don't change this comment - YaST2 identifier: Original name: Linux other 2###

title Rescue And Recovery
    chainloader (hd0,1)+1

###Don't change this comment - YaST2 identifier: Original name: Linux other 3###

title Linux test sda6
    chainloader (hd0,5)+1

###Don't change this comment - YaST2 identifier: Original name: Linux other 4###

title Linux other 4
    chainloader (hd0,6)+1

###Don't change this comment - YaST2 identifier: Original name: Linux other 5###

title Linux other 5
    chainloader (hd0,9)+1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- SUSE Linux 10.1
    root (hd0,4)
    kernel /boot/vmlinuz root=/dev/sda5 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off  3
    initrd /boot/initrd

And just for kicks here is the result of fdisk -l

brian:/home/brian # fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2943    22249048+   7  HPFS/NTFS
/dev/sda2            3638        4182     4120200    c  W95 FAT32 (LBA)
/dev/sda3            2944        7752    36356040    f  W95 Ext'd (LBA)
/dev/sda5            2944        3637     5246608+  83  Linux
/dev/sda6            4464        5109     4875696   83  Linux
/dev/sda7            6125        7752    12305758+   b  W95 FAT32
/dev/sda8            5109        6125     7679038+  83  Linux
/dev/sda9            4183        4376     1461852   82  Linux swap / Solaris
/dev/sda10           4377        4463      657688+   b  W95 FAT32

Partition table entries are not in disk order

I used to have the ubuntu root partition listed at /dev/sda6.  I tried to share my /home folder between ubuntu and suse...

Thanks in advance.
Brian.

---

