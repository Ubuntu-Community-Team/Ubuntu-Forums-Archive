---
title: "Grub Dual Boot Configuration"
date: 2006-09-14
forum: General Help
---

### Post by ToonArmy on 2006-09-14
I am having trouble dual booting my Ubuntu (which I have been loving since Hoary) with Windows XP. I have searched around this place and the mailing lists, and google, but haven't turned up exactly what I want.

I run Ubuntu from a SATA disc (sda) and Windows from an IDE disc (hda) both are installed in the first partition of the drive. Everyone else wants to know how to boot Windows from SATA and Ubuntu from IDE, I want the opposite and I am not having much success. I have tried various hacks at the instructions given nothing really works, my grub config for XP is included below.

Currently when I hit to boot XP from grub the screen flicks colour from a black to a more greyish black, I am guessing this maybe NTLDR taking over but thats all that happens.

I would like to avoid chaining grub from NTLDR and fiddling the BIOS everytime I want to go to Windows is getting rather annoying, then of course to get back (which I want to do ASAP ofc) is more annoying because I have to babysit until the Ubuntu disc is back in the driving seat.

```
title           Microsoft Windows XP
lock
root               (hd1,0)
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

```

Ubuntu boot instructions:

```
title           Ubuntu, kernel 2.6.15-26-k7
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-k7 root=/dev/sda1 resume=/dev/sda7 ro quiet splash elevator=cfq
initrd          /boot/initrd.img-2.6.15-26-k7
savedefault
boot
```

---

### Post by ciscosurfer on 2006-09-14
Don't know if you've checked this page, but it's extremely helpful...be sure to read the whole page before attemting anything!

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I have a very similar setup to you: Ubuntu on SATA, XP on IDE...

If you need more help, just let me know!  Be glad to try to help you ( also, please post your entire output of /etc/fstab as well as your /boot/grub/menu.lst )

---

### Post by ToonArmy on 2006-09-14
I looked there didn't find anything too helpful, here is how my discs are partitioned (output of fdisk -l).

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        9729    58613152+   5  Extended
/dev/sda5            2433        4864    19535008+  83  Linux
/dev/sda6            9487        9729     1951866   83  Linux
/dev/sda7            9365        9486      979933+  82  Linux swap / Solaris
/dev/sda8            4865        9364    36146218+  83  Linux
```

```
Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2350    18876343+   7  HPFS/NTFS
/dev/hda2            2351        4998    21270060   83  Linux
```

Output of Mount (minus optical drives and tmpfs etc):

```
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
/dev/sda5 on /home type ext3 (rw)
/dev/sda6 on /tmp type ext2 (rw)
```

Would you share the Windows portion of your grub configuration please. Many thanks.

---

### Post by drdrewusaf on 2006-09-14
Have you tried [WinGrub]("http://grub4dos.sourceforge.net/")?  It is resident on the Windows drive rather than the Ubuntu drive.  Slightly quirky software, but I have gotten success out of it where NOTHING else helped.  My drive situation is totally different, however I have faith that WinGrub will help or help you along.  I'm not at my PC now so I can't refrence my config for you, but if you like I can post it later.



Drew

---

### Post by ciscosurfer on 2006-09-14
I know you only want to see the Windows portion of my /boot/grub/menu.lst file, however, looking through my entire file my prove beneficial for you:

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout    10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue
color light-gray/brown white/brown

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet splash vga=791

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

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title        Ubuntu, kernel 2.6.15-26-686
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.15-26-686 root=/dev/sda1 ro quiet splash vga=791
initrd        /boot/initrd.img-2.6.15-26-686
savedefault
boot

title        Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.15-26-686 root=/dev/sda1 ro single
initrd        /boot/initrd.img-2.6.15-26-686
boot

#title        Ubuntu, kernel 2.6.15-26-386
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash vga=791
initrd        /boot/initrd.img-2.6.15-26-386
savedefault
boot

#title        Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd        /boot/initrd.img-2.6.15-26-386
boot

#title        Ubuntu, kernel 2.6.15-23-386
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro quiet splash vga=791
initrd        /boot/initrd.img-2.6.15-23-386
savedefault
boot

#title        Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro single
initrd        /boot/initrd.img-2.6.15-23-386
boot

#title        Ubuntu, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title        Windows NT/2000/XP (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb2
title        Windows NT/2000/XP (recovery)
root        (hd0,1)
savedefault
makeactive
chainloader    +1

# Knoppix kernel on sda3
title        Knoppix 5.0.1 (Debian GNU/Linux, kernel 2.6.17) good
root        (hd1,2)
kernel        /boot/vmlinuz root=/dev/sda3 ro ramdisk_size=100000 init=/etc/init lang=us apm=power-off nomce quiet vga=791 
initrd        /boot/initrd.img
savedefault
boot

# Knoppix kernel on sda3
title        Knoppix 5.0.1 (Debian GNU/Linux, kernel 2.6.17)
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.17 root=/dev/sda3 ro ramdisk_size=100000 init=/etc/init lang=us apm=power-off nomce quiet vga=791 
initrd        /boot/initrd.img-2.6.17
savedefault
boot

---

### Post by ToonArmy on 2006-09-15
Grub for you appears to be seeing /dev/sda* as hd(1,*) and /dev/hdb* as hd(0,*) which is not the case for me /dev/sda* is hd(0,*) and /dev/hda* is hd(1,*). This is where the problem comes into play because windows is insists it is the first drive.

Could you share the output of fdisk -l for each of your drives please?

@drdrewusaf I would rather not use WinGrub it strikes me as a dirty way of doing things, but it may come to that. I was looking at it yesterday.

---

### Post by ciscosurfer on 2006-09-15
Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *         635       14945   114953107+   7  HPFS/NTFS
/dev/hdb2               1         634     5092573+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3901    31334751   83  Linux
/dev/sda2           14033       14593     4506232+   5  Extended
/dev/sda3            3902        7800    31318717+  83  Linux
/dev/sda5           14033       14593     4506201   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24792   199141708+   7  HPFS/NTFS

>>> btw, my /dev/hda is mounted at /media/cdrom0...so perhaps if you get inside your box and switch around your drives and slave the appropriate drives like mine, you might be able to get your setup working.  I hope this helps you out. :grin:

---

