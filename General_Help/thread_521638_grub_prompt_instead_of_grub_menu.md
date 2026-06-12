---
title: "grub prompt instead of grub menu"
date: 2007-08-09
forum: General Help
---

### Post by Trab on 2007-08-09
hello, i've been looking around trying to solve my problem, but its just not getting anywhere.


a friend of mine had a virus on there hard-drive, so i took it and plugged it into my computer. mistake number 1. grub, HATES me, so I dunno what i was thinking.


long story short, grub is now not working. i kept getting grub error 22, and couldnt fix it. finally, i used windows fixboot and got windows to boot, but thats not what i wanted.

after trying different ways of grub and grub install on my liveCD, my current situation is this

/dev/hda1 = windows
/dev/hda = hd0 and is bootable

/dev/sda1 = / (for ubuntu)
/dev/sda2 = /home
/dev/sda5 = /boot


when i reboot my computer, it brings up a grub prompt (i think it must be on /dev/hda)

how do i restore my grub menu (located in /dev/sda5/grub/menu.lst)


thanks.

-trab

---

### Post by apetresc on 2007-08-09
Use the LiveCD instructions here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

It claims to be about recovering from a Windows install, but really it's just instructions for reinstalling Grub from a LiveCD. It should work in your case too :)

---

### Post by Trab on 2007-08-09
yes, ive tried everything there, both 
```

grub> root (hd1,4) #where my boot partion is
grub> setup (hd0)

```
and i've tired
```

sudo grub-install --root-directory=/mnt hd0

```
after mounting /dev/sda5 (boot partion) to /mnt

i still get either a grub 22 error (not sure which causes this)
or a grub partion on boot up.

help is appricated.

-Trab

---

### Post by logos34 on 2007-08-09
can you post your menu.lst?

---

### Post by Trab on 2007-08-09
sure.

for the record, the error i am currently dealing with is Grub error 22, which i believe means the menu.lst can't be found, due to a partion being changed...i got this from the previous issue of only having a grub prompt by using a live cd to do
```

sudo grub-install --root-directory=/mnt (which is my hd1,4 boot partion) hd0

```


here is my menu.lst
```

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color green/black black/light-green

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
# kopt=root=UUID=821012dc-e8c6-4441-a7ce-3a6db6ab1368 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

title		Ubuntu, kernel 2.6.20-16-386
root		(hd1,4)
kernel		/vmlinuz-2.6.20-16-386 root=UUID=821012dc-e8c6-4441-a7ce-3a6db6ab1368 ro quiet splash
initrd		/initrd.img-2.6.20-16-386
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-386 (recovery mode)
root		(hd1,4)
kernel		/vmlinuz-2.6.20-16-386 root=UUID=821012dc-e8c6-4441-a7ce-3a6db6ab1368 ro single
initrd		/initrd.img-2.6.20-16-386

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,4)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=821012dc-e8c6-4441-a7ce-3a6db6ab1368 ro quiet splash
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,4)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=821012dc-e8c6-4441-a7ce-3a6db6ab1368 ro single
initrd		/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,4)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=821012dc-e8c6-4441-a7ce-3a6db6ab1368 ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,4)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=821012dc-e8c6-4441-a7ce-3a6db6ab1368 ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,4)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP Pro
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by meierfra on 2007-08-09
Maybe your UUID for sda5 has changed.  (Edit: Actually that's very unlikely since you reinstalled grub)  Post the output of

blkid   and
sudo fdisk -l

---

### Post by djchandler on 2007-08-09
Viruses installing themselves in the MBR of a disk is a very old tried and true means of spreading them. That was the main means before all of us got onto the internet. That method goes back to when sneaker net and floppy disks were the major means of communication. You'll know better next time!

DJ

---

### Post by Trab on 2007-08-09
while its entirely possible that i have a virus in my MBR, i dont think thats the issue. when i plugged in the new hard drive, i had unplugged hd0, and grub on my machine is VERY tepermental.



```

ubuntu@ubuntu:/mnt/grub$ blkid
/dev/sdb1: UUID="07E6-001E" TYPE="vfat"

```
and
```

ubuntu@ubuntu:/mnt/grub$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       13054   104856223+  83  Linux
/dev/sda2           13055       57799   359414212+  83  Linux
/dev/sda3           57800       60385    20772045    c  W95 FAT32 (LBA)
/dev/sda4           60386       60801     3341520    f  W95 Ext'd (LBA)
/dev/sda5           60386       60409      192748+  83  Linux
/dev/sda6           60410       60801     3148708+  82  Linux swap / Solaris

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2432    19535008+   7  HPFS/NTFS

Disk /dev/sdb: 1030 MB, 1030225920 bytes
4 heads, 3 sectors/track, 167680 cylinders
Units = cylinders of 12 * 512 = 6144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              21      167680     1005958+   6  FAT16
ubuntu@ubuntu:/mnt/grub$ 

```

help would be appricated, i'm gonna do more research on grub error 22 soon...i may just repair the windows MBR and bootfix then use add ubuntu to that for a quick fix, using the liveCD is a pain when i have to keep rebooting and reconfiging.


cheers,
Trab

---

### Post by meierfra on 2007-08-09
What's the output of 

find /boot/grub/stage1 

at the grub prompt?

---

### Post by Trab on 2007-08-09
update: now i get grub error 21. the difference: plugged back in the CD drive i had unplugged to add the other hard-drive.

i think its getting close...

```

grub> find /boot/grub/stage1
 (hd1,4)

```

---

### Post by meierfra on 2007-08-09
I don't know what is going on. But I would try to set up grub on more time:

grub> root (hd1,4)
grub> setup (hd0)

Also check your /boot/grub/menu.lst  afterwards and see whether the UUID for (hd1,4) has changed.

(maybe grub just gets confused  when you plug and unplug your hard drives)

---

### Post by Trab on 2007-08-09
alright. i'll try that. might just do the windows boot loader and fix it later. tired of using the  liveCD over and over.


```

grub> root (hd1,4)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+17 p (hd1,4)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

grub> 

```

---

