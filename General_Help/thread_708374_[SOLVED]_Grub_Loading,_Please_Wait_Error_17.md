---
title: "[SOLVED] Grub Loading, Please Wait Error 17"
date: 2008-02-26
forum: General Help
---

### Post by handsomeDave on 2008-02-26
I've been using Ubuntu for just over a month now, and everything's been going pretty smooth, except for today when I turned on my computer, and I get
GRUB Loading stage1.5
GRUB loading, please wat...
Error 17

I didn't change or install anything, just shut down my computer like normal last night and now it won't turn on.
Does anybody have an ideas about how to fix this.
I've got a 500gb with ubuntu on it
160gb with windows vista
and 2 500gb data drives
all SATA

Oh and I really don't want to have to reinstall ubuntu, because i spent way too long trying to get everything working perfectly.

---

### Post by SpaceTeddy on 2008-02-26
don't know of this helps... 

[http://ubuntuforums.org/showthread.php?t=442945]("http://ubuntuforums.org/showthread.php?t=442945")
but it looks like it is worth a try

---

### Post by handsomeDave on 2008-02-26
Thanks anyway, but that didnt help..

But just to add something here. I can boot into vista fine.

EDIT: I did delete some files that i thought were just backup files from one of my data drives. But they might've been system files, they were in folders called ProgramData and Windows.

---

### Post by danwood76 on 2008-02-26
> 
Error 17 : "Invalid device requested"

This error is returned if a device string is recognizable but does not fall under the other device errors.

It could be that its referencing an incorrect partition or something else making it go funny.
Could you boot a live CD up mount your ubuntu drive and post your /boot/grub/menu.lst
and also
```

sudo fdisk -l

```

this info is very useful to post when you have grub issues.

---

### Post by handsomeDave on 2008-02-26
menu.lst

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=33e680fe-329b-4bcb-88f3-40aa2cdaa07f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=33e680fe-329b-4bcb-88f3-40aa2cdaa07f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet


fdisk

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x86204c43

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfec11412

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52c3876e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19458   156288000    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00029af4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60044   482303398+  83  Linux
/dev/sdd2           60045       60801     6080602+   5  Extended
/dev/sdd5           60045       60801     6080571   82  Linux swap / Solaris

Disk /dev/sde: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e3568fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       19929   160079661    c  W95 FAT32 (LBA)


device.map

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
(hd4)	/dev/sde

---

### Post by danwood76 on 2008-02-26
it would be nice if I could see the entire menu.lst
theres more to the config than just that section, though that does look correct.

You should post those types of things in code tags [code]... ...[/code ] to make it more readable

---

### Post by danwood76 on 2008-02-26
it might fix the problem if you just re install grub using the live CD.

heres a guide:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by handsomeDave on 2008-02-26
> **danwood76 said:**
> it would be nice if I could see the entire menu.lst
theres more to the config than just that section, though that does look correct.

You should post those types of things in code tags [code]... ...[/code ] to make it more readable

the rest of the menu.lst was all commented out.
and sorry bout the code tags, i didnt know about it

---

### Post by danwood76 on 2008-02-26
How do you boot vista?
Do you not do it through grub?

I would try reinstalling grub from the link I posted above, though if you boot vista in a different way from using grub then you need to make sure you choose the correct drive when you do the 'setup (hd0)' you would need to do setup (hd3) instead I would expect.
Though it does depend on how you boot vista.

---

### Post by handsomeDave on 2008-02-26
I just change the boot drive in the BIOS when the computer starts up. I didn't even know about GRUB until I had this problem

Here's the rest of menu.lst
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=33e680fe-329b-4bcb-88f3-40aa2cdaa07f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,0)

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
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=33e680fe-329b-4bcb-88f3-40aa2cdaa07f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=33e680fe-329b-4bcb-88f3-40aa2cdaa07f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by handsomeDave on 2008-02-26
After reinstalling grub, I still get the Error 17:Cannot Mount Selected Partition

---

### Post by danwood76 on 2008-02-26
You see when you change the boot prioity in the BIOS it will mess around with the drive map in grub which will cause you errors.
You can setup grub so that it will give you a menu that will let you boot vista.

Does it give you this error after its done the countdown or does it happen before?
If you get the countdown press escape and it should give you a list, from which you can select the recovery partition.

Im wondering if maybe the UUID has changed on your gutsy drive due to an update or something else.

---

### Post by handsomeDave on 2008-02-26
it gives me a count of 2, if i press esc i get a menu with Ubuntu 7.10, Ubuntu 7.10 (Recovery Mode) and Ubuntu 7.10 memtest86*. and the Recovery mode doesnt work.
also it's understandable that messing with the boot priority would mess it up, but i havent used vista since I installed ubuntu

---

### Post by danwood76 on 2008-02-26
right when you boot press escape and edit the main ubuntu line (not recovery mode)

edit the following line:
```

kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=33e680fe-329b-4bcb-88f3-40aa2cdaa07f ro quiet splash

```

to be:
```

kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sdd1 ro quiet splash

```

so remove the UUID bit and replace with the physical disk location.
if this doesnt work still then the UUID is ok.

If it does then just modify the menu.list so it has that instead.
You may want to look into booting vista from grub which will svae you a lot of BIOS hastle.

---

### Post by handsomeDave on 2008-02-26
didn't work :(

---

### Post by handsomeDave on 2008-02-27
is there anyway that I can reinstall system files and make it work without having to reinstall the whole OS? Like a repair option?

---

### Post by handsomeDave on 2008-02-27
I changed the boot order in the bios to match the device.map, and now it starts to boot, it gets to the ubuntu loading screen with the progress bar, but doesnt load.
I then get a screen that says
```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

---

### Post by handsomeDave on 2008-02-27
Solved. After restarting a couple times it finally just worked...

Thanks for your help. :-D

---

