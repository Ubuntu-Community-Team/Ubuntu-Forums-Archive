---
title: "STILL getting grub error 17!!"
date: 2007-11-25
forum: General Help
---

### Post by helix on 2007-11-25
I have been working on this for literally over 10 hours. I keep having issue after issue with any linux distro its getting rediculous.  I can't seem to get grub to do its thing. I've setup, I've set the root drive, I've even let the ubuntu installer do its magic and STILL get the error 17. I've used windows's fixmbr and fixboot and tried again but still nothing!

p4 2.6
3gb pc3200
abit is-7 mobo
ati radion x850xt

happens with every version of ubuntu I've tried and with ever distro I've tried. 

:confused::confused::confused:

---

### Post by meierfra on 2007-11-25
Boot from the Ubuntu Live CD, open a terminal (Applications->Accessories->Terminal) and post the output of 

```
sudo fdisk -l
```
(l is a lowercase L, not the number one)

---

### Post by helix on 2007-11-25
ubuntu@ubuntu:~$ sudo su root
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/hda2            4865        4991     1020127+  82  Linux swap / Solaris
/dev/hda3            4992        9729    38057985   83  Linux

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       19457   156288321    7  HPFS/NTFS
root@ubuntu:/home/ubuntu# 





Thanks for the help.

---

### Post by meierfra on 2007-11-25
Mount the ubuntu partition:

```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/hda3 /ubuntu
```

and post the output of

```
 cat /ubuntu/boot/grub/menu.lst
```

---

### Post by helix on 2007-11-25
> **meierfra said:**
> Mount the ubuntu partition:

```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/hda3 /ubuntu
```

and post the output of

```
 cat /ubuntu/boot/grub/menu.lst
```

root@ubuntu:/mnt# cat /mnt/ubuntu/boot/grub/menu.lst
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
# kopt=root=UUID=f9b3c8cf-2d88-4fe7-9807-63acc6c809e6 ro
# kopt_2_6=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1



---------------------
thanks

---

### Post by teryowen on 2007-11-25
try these this:

sudo grub
root (hd0,2)
setup (hd0)
quit

---

### Post by meierfra on 2007-11-25
I don't see anything wrong. A few things to try:

1) Reinstall grub: (Opps, teryowen already suggest this)

```
sudo grub
root (hd0,2)
setup (hd0)
quit
```

Reboot, make sure that you boot from Windowd/Ubuntu drive

2) Change the boot order in the bios. (Try various settings)

3) Get Supergrub [(Hermanzone Info)]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

4)  Disconnect the other two hard drives.

Report back here if you notice any changes. In particular, if the grub menu ever shows up during boot up, most of your troubles will be over.

---

### Post by helix on 2007-11-25
Reinstalling grub didn't work, I changed the boot order to every possible combination before I posted here, I also tried supergrub as well and none of the options worked unfortionately. I've got a real odd issue here.

---

### Post by teryowen on 2007-11-25
does loading windows work?

---

### Post by meierfra on 2007-11-25
Did you try physically disconnecting the other two drives?

---

### Post by helix on 2007-11-25
> **teryowen said:**
> does loading windows work?

After I pop in the XP cd and go to the recover console then type "fixboot" and "fixmbr" it does yes, but otherwise I cannot proceed past the error 17.

> **meierfra said:**
> Did you try physically disconnected the other two drives?

Yes I tried that as well, still no dice.

---

### Post by teryowen on 2007-11-25
hvae u checked ur BIOS to make sure its set up properlly, that it can see the main hard drive, and is in the primary boot slot.

---

### Post by helix on 2007-11-25
> **teryowen said:**
> hvae u checked ur BIOS to make sure its set up properlly, that it can see the main hard drive, and is in the primary boot slot.

Just checked again. It is.

Is my only option to completely erase this disk and start from scratch?

---

### Post by teryowen on 2007-11-25
not always, but sometimes its what you have to do, my first installation didnt work either i reinstalled and worked dont know why.

Im sure these is a solution, i just dont know it.

You could look into lilo, maybe use that instead of GRUB

---

### Post by helix on 2007-11-25
I think I'm just gonna nuke it all and begin a new. Thanks for both your help, you guys have been very helpful!

---

