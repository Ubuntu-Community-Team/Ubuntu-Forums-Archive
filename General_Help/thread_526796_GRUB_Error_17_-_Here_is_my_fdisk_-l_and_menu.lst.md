---
title: "GRUB Error 17 - Here is my fdisk -l and menu.lst"
date: 2007-08-15
forum: General Help
---

### Post by aaronbc on 2007-08-15
All of the sudden I started getting GRUB Error 17 when I boot my computer (used to work fine).  Here is my fdisk -l and menu.lst: (hda is just general storage, hdb is my ubuntu installation, sda is winXP on a scsi drive, sdb is a USB thumb drive)  I did notice that this problem started happening after using my thumb drive.  When I first rebooted after using the thumb drive I had to go into my BIOS because it got reset to boot from the thumb drive automatically.  Don't know if that has anything to do with the problem.

```
root@1[knoppix]# fdisk -l

Disk /dev/hda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        9732    78172258+   7  HPFS/NTFS

Disk /dev/hdb: 10.2 GB, 10254827520 bytes
255 heads, 63 sectors/track, 1246 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1187     9534546   83  Linux
/dev/hdb2            1188        1246      473917+   5  Extended
/dev/hdb5            1188        1246      473886   82  Linux swap / Solaris

Disk /dev/sda: 18.2 GB, 18210037760 bytes
255 heads, 63 sectors/track, 2213 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2212    17767858+   7  HPFS/NTFS

Disk /dev/sdb: 1027 MB, 1027416576 bytes
16 heads, 63 sectors/track, 1990 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1991     1003305    e  W95 FAT16 (LBA)

root@1[knoppix]# cat /media/hdb1/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# kopt=root=UUID=ec11f21e-1dd4-41c7-8c7d-6b74685010c7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=ec11f21e-1dd4-41c7-8c7d-6b74685010c7 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=ec11f21e-1dd4-41c7-8c7d-6b74685010c7 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root           (hd0,0)
savedefault
makeactive
chainloader     +1


```

---

### Post by OzzyFrank on 2007-08-16
Hiya. Got your private message, but since you posted this thread, I may as well reply here for the benefit of others. OK, I too have Ubuntu on the 2nd drive, but have Windows on the 1st, and I use a boot manager (Acronis OS Selector) that runs off that drive (hda of course). Now, for me the best solution is NOT to have GRUB on the MBR of hda or even hdb, but the partition itself (in GRUB lingo (hd1,0)). For you, it would be to stick GRUB in the MBR, but not on the Ubuntu drive, but the primary master (hda or in GRUB (hd0)). [In GRUB hda is (hd0) and hdb1 is (hd1,0) etc]

So, for you the answer should be to get to a grub> prompt, then specify the MBR of the1st drive, since that is what the system looks to when booting. Whether you use GRUB or something like Acronis installed through Windows as your primary boot loader, it has to be on the primary master drive. I noticed that you tried to install GRUB to the MBR of your Ubuntu drive, hdb, so do as follows at the grub> prompt:

root (hd1,0)
setup (hd0)

Let me know if this works. Cheers

---

### Post by OzzyFrank on 2007-08-16
OK, just did a scan of your fstab etc, just in case coz I've had my drives go from starting with "h" then to "s" and back again a few times since Feisty came out, and have had to deal with it by changing the "h" to "s" and back again in important files like fstab. Anyway, I noticed in fstab:

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd2,0)

Shouldn't that read (hd1,0) for your Ubuntu partition hdb1? You might need to change that back, as wrong entries (like my hda vs sda issue) will result in a no-go just like a GRUB that is mangled enough to need a reinstall. I'll quote your device.map info for others interested:

[COLOR="Purple"]my device.map file looked something like:
(hd0) /dev/sda
(hd1) /dev/sdb
(hd2) /dev/sdc

I tried changing it to:
(hd0) /dev/sda
(hd1) /dev/hda
(hd2) /dev/hdb[/COLOR]

According to your fdisk output, the order should be:

[B](hd0) /dev/hda
(hd1) /dev/hdb
(hd2) /dev/sda[/B]

Hope this helps too! Cheers

---

### Post by lewac on 2007-10-09
yep I had this idenitcal prob. my sys has win2000 (and MSDOS) installed on two separate primary partitions on the first drive (hd0). ubuntu is also installed within an extended on this same drive. well after the win2000 boot "resetting" (blue-screening and then auto-reboot from there) a coupla times and then returning to an attempted ubuntu boot we got error 17 (which basically means that the partition attempting to boot doesn't have a valid linux OS on it).

well I gotta bunch of hd's (each with several partitions) on this box and somehow some "thing" trashed ALL my ubuntu entries within menu.lst. how I have no clue but hey we go from what-we-got to what-we-want, right? so boot from the live CD and taking a look at menu.lst (/boot/grub/menu.lst is the path) shows ALL my ubuntu "root" entries changed FROM (hd0,4) TO (hd2,4)!!! well changing them all BACK to (hd0,4)... the partition that REALLY does have ubuntu installed; fixed it. 

now a bit off-topic here but relevant... once you get all this working do a search on the following file... mbrutild.exe. this file is kinda buried within the reference site but anyhow it represents a real gem because it allows one to backup AND restore either the MBR and/or the entire first sector on the boot drive (generally (hd0). true. you also need a DOS boot floppy (because its a DOS app) to run it (if you don't have that you can find it as well). the idea here is to make a copy of that entire first sector once everything is working as it should... uhh good idea to place those copies on an fat16 partition somewhere as well (as floppies are NOT known for their robustness!). although it won't repair the noted menu.lst issue its a very straightforward method of repair on the MBR AND grub. just be careful (because you do NOT want to do a "save" when in fact you wanted "restore" (or visa-versa))! and finally another valuable use is to ERASE the MBR on a "trashed" drive (thereby more-than-likely salvaging same). and finally, finally IF you make ANY partition changes at all ascertain that you make "new" copies of these backup files.

---

