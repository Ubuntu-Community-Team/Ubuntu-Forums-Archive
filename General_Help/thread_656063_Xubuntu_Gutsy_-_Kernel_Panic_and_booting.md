---
title: "Xubuntu Gutsy - Kernel Panic and booting"
date: 2008-01-02
forum: General Help
---

### Post by smacd on 2008-01-02
I was using Xubuntu 6.10 for a few months without any problem, however when I upgraded to 7.10 a few weeks ago, I developed two new problems.

The first problem is that, when I boot up, there is a blank screen for 2-3 minutes after the BIOS and GRUB load, before it gets to the log-in screen. It didn't take more than a few seconds with Edgy to get to the log-in screen.

The second problem is far more critical. I have just started getting an error at boot that says "Kernel Panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)", and the system seems to stop doing anything else. I have absolutely no idea what to do about this, or how to do anything about it. I have a feeling that my hard drive might be hosed, but I'm hoping I can salvage the system at least for a few more weeks.

This is on an old Toshiba laptop, I can get the specs for it if they are needed.

---

### Post by danwood76 on 2008-01-02
Well the first problem is due to the installer configuring the splash screen wrong, quite a common problem but easily fixed.

Can you boot with the live CD and then mount the drive?

regards,
Danny

---

### Post by smacd on 2008-01-02
yeah, i can boot up with my livecd and mount the drive. So what can i do from here?

---

### Post by danwood76 on 2008-01-02
Sounds like its probably a grub config problem.

can you post the result of these commands in terminal:

```

cat /boot/grub/menu.lst

sudo fdisk -l

```

regards,
Danny

---

### Post by smacd on 2008-01-02
```

sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier 0x2b49c53d

Device        Boot      Start      End          Blocks           Id     System
/dev/sda1  *            1            4682       37608133+  83    Linux
/dev/sda2                4863      4684       1461915         5    Extended
/dev/sda5                4863      4684       1461883+    82    Linux swap / Solaris

```

as for the other command, there does not appear to be a directory for grub in /boot/

---

### Post by danwood76 on 2008-01-03
Oh right, Sorry thats my bad.
What you need to do is mount the hard disk first and change to that root.

so boot the live cd and then do:

```

sudo mkdir /tempdrive

sudo mount -t ext3 /dev/sda1 /tempdrive

sudo chroot /tempdrive

```

that will change the terminal root drive to be your hard disk.
then post the result of:

```

cat /boot/grub/menu.lst

```

regards,
Danny

---

### Post by smacd on 2008-01-03
Alright, I didn't realize I needed to do chroot. so the following is the complete output. (I added spaces between the 8 and the ) so that it wont display 8)'s)

> root@ubuntu:/# cat /boot/grub/menu.lst
# menu.lst - See: grub(8 ), info grub, update-grub(8 )
#            grub-install(8 ), grub-floppy(8 ),
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
# kopt=root=UUID=a363e451-c408-43c5-85e8-f49bb83e7e5a ro

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
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a363e451-c408-43c5-85e8-f49bb83e7e5a ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a363e451-c408-43c5-85e8-f49bb83e7e5a ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by danwood76 on 2008-01-03
Your grub configuration looks fine.
You could try re installing it by following this guide:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Failing that it could be more a problem with a corrupt kernel or initramfs, which would probably mean a fresh install would be better, backing up your /home and /etc directories first to save your files and settings.

regards,
Danny

---

### Post by smacd on 2008-01-04
alright, thanks for the help Danny. The other thread didn't seem to help solve the problem, so I am going to just re-install. At least I figured out how to get access to the drive contents so i could back them up.

---

