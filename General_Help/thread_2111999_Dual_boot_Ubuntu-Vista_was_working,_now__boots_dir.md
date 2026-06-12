---
title: "Dual boot Ubuntu-Vista was working, now  boots directly to ubuntu without grub menu"
date: 2013-02-03
forum: General Help
---

### Post by jmiller64 on 2013-02-03
On my laptop, I had dual-boot Windows Vista and Ubuntu 8.0.4 Hardy working for years.  My old client required that I work on Ubuntu/Kubuntu 8.0.4, but my new client requires Windows Vista.  A few months ago, my laptop began booting directly to Ubuntu, without displaying the grub menu list to choose which OS to boot to.  I no longer know how to boot to Vista and would really like to be able to do so.  I would also prefer to keep Ubuntu 8.0.4 as my old client sometimes makes requests of me.  Any ideas on how to boot to Vista again?

---

### Post by Impavidus on 2013-02-03
Well, time for you client to upgrade. Hardy Heron has been unsupported for years. But you may  not be in the position to tell him/her to do so.

Grub must still be installed, I assume, but the menu isn't showing. Could you post the output of the following two commands?```
cat /etc/default/grub
grep menuentry /boot/grub/grub.cfg
```It should tell us how your menu is configured (it may be invisible due to the timer being set to 0) and whether Vista is in the menu.

These commands should work if you use grub2. If you're using grub legacy (still the default when Hardy Heron came out), try```
cat /boot/grub/menu.lst
```This should contain the same information.

---

### Post by oldfred on 2013-02-03
You probably still have grub legacy 0.97.
Did you try:
sudo update-grub

May be best to run Bootinfo script.
       Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by jmiller64 on 2013-02-04
Yes, I'm using legacy grub.  Here is the contents of /boot/grub/menu.lst:
(I have not yet tried "sudo update-grub" -- should I?  Also, I will look into running the Bootinfo script.)

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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

title           Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.24-28-generic root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro quiet splash
initrd          /boot/initrd.img-2.6.24-28-generic
quiet

title           Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic (recovery mode)
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.24-28-generic root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro single
initrd          /boot/initrd.img-2.6.24-28-generic

title           Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.24-27-generic root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro quiet splash
initrd          /boot/initrd.img-2.6.24-27-generic
quiet

title           Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.24-27-generic root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro single
initrd          /boot/initrd.img-2.6.24-27-generic

title           Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.24-26-generic root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro quiet splash
initrd          /boot/initrd.img-2.6.24-26-generic
quiet

title           Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.24-26-generic root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro single
initrd          /boot/initrd.img-2.6.24-26-generic

title           Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.24-24-generic root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro quiet splash
initrd          /boot/initrd.img-2.6.24-24-generic
quiet

title           Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic (recovery mode)
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.24-24-generic root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro single
initrd          /boot/initrd.img-2.6.24-24-generic

title           Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.24-23-generic root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro quiet splash
initrd          /boot/initrd.img-2.6.24-23-generic
quiet

title           Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic (recovery mode)
root            (hd1,5)
kernel          /boot/vmlinuz-2.6.24-23-generic root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro single
initrd          /boot/initrd.img-2.6.24-23-generic

title           Ubuntu 8.04.4 LTS, memtest86+
root            (hd1,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1
```

---

### Post by jmiller64 on 2013-02-04
Here is the contents of the results.txt file from running the bootinfoscript:


```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on boot 
    drive #2 in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/BCD

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab

sdb7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf1fb6b69

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   182,016,449   182,016,387   7 NTFS / exFAT / HPFS
/dev/sda2         182,016,450   195,366,464    13,350,015   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc7c04516

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    20,482,047    20,480,000   c W95 FAT32 (LBA)
/dev/sdb2          20,482,875   195,366,464   174,883,590   f W95 Extended (LBA)
/dev/sdb5          20,482,938    24,691,904     4,208,967  82 Linux swap / Solaris
/dev/sdb6          24,691,968   108,583,334    83,891,367  83 Linux
/dev/sdb7         108,583,398   195,366,464    86,783,067  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        1736AEE94AC9EEF1                       ntfs       OS
/dev/sda2        2C88743C8874071C                       ntfs       HP_RECOVERY
/dev/sdb1        9CF1-E41E                              vfat       DATA
/dev/sdb5        37e5e000-00d3-4145-b368-50a230b0bc29   swap       
/dev/sdb6        98b7be21-d6a7-4e70-83da-8d716898c718   ext3       
/dev/sdb7        61bdbc50-c1bd-4de3-aed1-19bd78388aed   ext3       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdb7        /home                    ext3       (rw,relatime)


=========================== sdb6/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.24-28-generic root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro quiet splash
initrd        /boot/initrd.img-2.6.24-28-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-28-generic (recovery mode)
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.24-28-generic root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro single
initrd        /boot/initrd.img-2.6.24-28-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro quiet splash
initrd        /boot/initrd.img-2.6.24-27-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro single
initrd        /boot/initrd.img-2.6.24-27-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro quiet splash
initrd        /boot/initrd.img-2.6.24-26-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro single
initrd        /boot/initrd.img-2.6.24-26-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-24-generic (recovery mode)
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-23-generic (recovery mode)
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=98b7be21-d6a7-4e70-83da-8d716898c718 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.4 LTS, memtest86+
root        (hd1,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1

--------------------------------------------------------------------------------

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=98b7be21-d6a7-4e70-83da-8d716898c718 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb7
UUID=61bdbc50-c1bd-4de3-aed1-19bd78388aed /home           ext3    relatime        0       2
# /dev/sdb5
UUID=37e5e000-00d3-4145-b368-50a230b0bc29 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
iodine.trustamerica.com:/appstore /appstore nfs rw,nosuid,hard,rsize=8192,wsize=8192,timeo=14,intr 0 0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/menu.lst
            ?? = ??             boot/grub/stage2
            ?? = ??             boot/initrd.img-2.6.24-23-generic
            ?? = ??             boot/initrd.img-2.6.24-23-generic.bak
            ?? = ??             boot/initrd.img-2.6.24-24-generic
            ?? = ??             boot/initrd.img-2.6.24-24-generic.bak
            ?? = ??             boot/initrd.img-2.6.24-26-generic
            ?? = ??             boot/initrd.img-2.6.24-26-generic.bak
            ?? = ??             boot/initrd.img-2.6.24-27-generic
            ?? = ??             boot/initrd.img-2.6.24-27-generic.bak
            ?? = ??             boot/initrd.img-2.6.24-28-generic
            ?? = ??             boot/initrd.img-2.6.24-28-generic.bak
            ?? = ??             boot/vmlinuz-2.6.24-23-generic
            ?? = ??             boot/vmlinuz-2.6.24-24-generic
            ?? = ??             boot/vmlinuz-2.6.24-26-generic
            ?? = ??             boot/vmlinuz-2.6.24-27-generic
            ?? = ??             boot/vmlinuz-2.6.24-28-generic
            ?? = ??             initrd.img
            ?? = ??             initrd.img.old
            ?? = ??             vmlinuz
            ?? = ??             vmlinuz.old

```

---

### Post by jmiller64 on 2013-02-04
I ran "sudo update-grub" but I don't see any improvements afterwards -- I still get no grub OS list at boot up, and I boot directly to Kubuntu.

---

### Post by oldfred on 2013-02-04
From what I remember of Grub legacy that looks normal. You have the sda1 set as boot with the normal boot files for Windows.

I might install the grub boot loader to sdb and set BIOS to boot sdb, if you system allows you to choose boot drive in BIOS. Some old systems only set boot drive with jumpers on IDE drive. Somewhat newer IDE with cable select usually could set boot drive in BIOS.

Then you can install the Windows boot driver to sda and test Windows boot directly. 

these command are really the same with grub 2 & grub legacy. From inside you install.
sudo grub-install /dev/sdb
This is to automatically generate a new menu.lst file for you.
sudo update-grub

Then you can install a Windows boot loader to sda.

Not sure if your install will still download lilo or not?
       Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

    
If you cannot download lilo you will have to use liveCD with a newer version.

You have a lot of kernels. Do you actually have the Windows entry but it is not shown inside the grub box. A small arrow may mean you have more entries and need to scroll down. 
Since grub shown multiple systems it should show menu.

---

