---
title: "Ubuntu first time installation/mistakes"
date: 2007-11-18
forum: General Help
---

### Post by junner18 on 2007-11-18
Installed Ubuntu 7.10 yesterday, having never used or seen linux before,  So naturally I have had a few newbie problems.

I formatted the drive to remove windows entirely.  These are the issues I have.

1. I can't boot from the hard drive.  "Error loading operating system" is displayed as soon as the operating system should start loading.  I have to boot from the CD, and chose Boot from first hard drive to get things loaded.

2. How do I mount my second hard drive?  I can see it is Partition Editor, but can't find it anywhere else.  And what formats should my hard drives use?

---

### Post by Pumalite on 2007-11-18
If you finished installing Ubuntu; from Terminal, post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by junner18 on 2007-11-18
I'm not sure if I should be posting this whole thing, but here goes.

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=40f47f3b-70ee-41b4-ba5d-b90c4c0772ea ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=40f47f3b-70ee-41b4-ba5d-b90c4c0772ea ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=40f47f3b-70ee-41b4-ba5d-b90c4c0772ea ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet




Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x177e177e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   115732259    57866098+  83  Linux
/dev/sda2       115732260   117226304      747022+   5  Extended
/dev/sda5       115732323   117226304      746991   82  Linux swap / Solaris

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xba3abb4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   320159384   160079661   83  Linux

---

### Post by teryowen on 2007-11-18
Does your computer fail to load the OS after you select the option in GRUB or does GRUB just not display?

By the way when you post code, you can high light it in your post while you editing and click on the # symbol to wrap it in code and it will display it niceley
```

Like SO

```

EDIT:
To mount your second hard drive type this into terminal
```

mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1

```

---

### Post by Rev60073 on 2007-11-18
Regarding the second harddrive, do you want to reformat it as well, or do you have data in it that you want to access through your new Linux installation?

---

### Post by Pumalite on 2007-11-18
If you eliminated Windows, format your 2nd hard drive ext3. I see your menu.lst OK., but Windows is know to leave residual stuff sometimes that can only be removed DBanning the hard drive:
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Maybe you need to do that and then use Gparted Live CD to format your hard drive before you can install Ubuntu successfully.

---

### Post by junner18 on 2007-11-18
*The GRUB fails to load.

*I wanted to format both drives.  I assumed this would get done during the Ubuntu installation, But it seems to try to fit in with whatever else is on the drive.

---

### Post by Pumalite on 2007-11-18
You could have a 'hidden' recovery partition left or some other debris.

---

### Post by Rev60073 on 2007-11-18
> **junner18 said:**
> *The GRUB fails to load.

*I wanted to format both drives.  I assumed this would get done during the Ubuntu installation, But it seems to try to fit in with whatever else is on the drive.

To format the drive, identify which is its device name. From your fdisk output, seems like it is /dev/sdb.

To format this drive, the drive must be unmounted. Type:

sudo mount

And make sure that /dev/sdb is not there.

To format the drive, use mkfs.ext3 /dev/sdb (use with care).

Then, try mounting the drive: 

mkdir /mnt/drive2
mount /dev/sdb /mnt/drive2

Now your drive will be mounted and accessible under /mnt/drive2 .

For the changes to be permanent upon reboot, you should modify your /etc/fstab and add the drive there.

---

### Post by teryowen on 2007-11-18
Before formating you might try just fixing your grub.

Boot of the live cd or the way u specified using the hard drive.

Write to the MBR. Assuming grub.lst is intact, continue with the process. Type "grub" (return) to enter the grub shell.

Tell grub where to find the requisite files. If you know where they are, enter something like:

root (hd0,1)

(hd0,1) means primary controller master, second partition. If you DON'T know where they are, type:

find /boot/grub/stage1

and then enter the root command with the correct parameters. Note: If you are using a separate /boot partition , as the official documentation says: "... if you have the partition /boot and you install GRUB images into the directory /boot/grub, GRUB recognizes that the images lies under the directory /grub but not /boot/grub.' Thus, if 'find /boot/grub/stage1' does not find the file, try 'find /grub/stage1'."

Next, type:

setup (hd0)

This command will install grub on the MBR of the first drive.

I got this info from here [http://www.whoopis.com/howtos/howto_restore_mbr_grub.php](http://www.whoopis.com/howtos/howto_restore_mbr_grub.php)

this will update the MBR and tell it where the grub is and thus allowing you to use your GRUB to select which OS to boot.

---

### Post by junner18 on 2007-11-18
Got these problems solved, thanks.

---

### Post by Pumalite on 2007-11-19
Can you tell us how for the benefit of the forum?

---

