---
title: "BIOS doesn't seem to find GRUB"
date: 2008-06-17
forum: General Help
---

### Post by scbash on 2008-06-17
Hi all-

I'm trying to diagnose a boot problem with my Ubuntu box.  It could either be a hardware or software problem, so I'm investigating both angles currently.

When I boot my Ubuntu machine the BIOS claims there's no system disk available.  The problem cropped up after I removed some spare hard drives after buying a NAS.  After checking the connections inside the case the problem remained.  Next I booted using an 8.04 LiveCD, selected "Boot from first hard drive" and my system booted fine.  I ran 'sudo grub-install /dev/hda', which gave no errors, and rebooted.  BIOS still didn't find grub.  Once again I put in the LiveCD and was able to boot from the first hard drive.

Has any one seen this problem before?  I have an ASUS A7N8X2.0 motherboard running Phoenix BIOS.  I'm running Ubuntu 8.04 with all current updates.

Thanks,
Stephen

---

### Post by feisty john on 2008-06-17
I don't know that I'm going to be able to help that much, but what do
```
ls -a -l /boot
```
and
```
cat /boot/grub/menu.lst
```
return?

---

### Post by scbash on 2008-06-17
> **feisty john said:**
> I don't know that I'm going to be able to help that much
Any help is appreciated!  Here's what you asked for:

```
scbash@maestro:~$ ls -al /boot
total 91492
drwxr-xr-x  4 root root    4096 2008-06-17 13:36 .
drwxr-xr-x 21 root root    4096 2008-06-17 13:36 ..
-rw-r--r--  1 root root  424317 2008-02-12 05:39 abi-2.6.22-14-generic
-rw-r--r--  1 root root  422607 2008-04-10 12:51 abi-2.6.24-16-generic
-rw-r--r--  1 root root  422667 2008-05-01 13:59 abi-2.6.24-17-generic
-rw-r--r--  1 root root  422667 2008-05-28 22:39 abi-2.6.24-18-generic
-rw-r--r--  1 root root  422667 2008-06-04 16:50 abi-2.6.24-19-generic
drwxr-xr-x  3 root root    4096 2008-06-14 13:35 boot
-rw-r--r--  1 root root   75311 2008-02-12 05:39 config-2.6.22-14-generic
-rw-r--r--  1 root root   79964 2008-04-10 12:51 config-2.6.24-16-generic
-rw-r--r--  1 root root   80071 2008-05-01 13:59 config-2.6.24-17-generic
-rw-r--r--  1 root root   80071 2008-05-28 22:39 config-2.6.24-18-generic
-rw-r--r--  1 root root   80049 2008-06-04 16:50 config-2.6.24-19-generic
drwxr-xr-x  2 root root    4096 2008-06-17 13:36 grub
-rw-r--r--  1 root root 7495264 2008-03-23 14:29 initrd.img-2.6.22-14-generic
-rw-r--r--  1 root root 7494269 2008-03-23 12:30 initrd.img-2.6.22-14-generic.bak
-rw-r--r--  1 root root 7725316 2008-05-13 18:34 initrd.img-2.6.24-16-generic
-rw-r--r--  1 root root 7725300 2008-05-13 18:27 initrd.img-2.6.24-16-generic.bak
-rw-r--r--  1 root root 7725747 2008-05-26 13:27 initrd.img-2.6.24-17-generic
-rw-r--r--  1 root root 7725762 2008-05-26 13:26 initrd.img-2.6.24-17-generic.bak
-rw-r--r--  1 root root 7763074 2008-06-14 13:41 initrd.img-2.6.24-18-generic
-rw-r--r--  1 root root 7725502 2008-06-03 17:55 initrd.img-2.6.24-18-generic.bak
-rw-r--r--  1 root root 7765077 2008-06-17 13:36 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7765065 2008-06-17 13:36 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 06:06 memtest86+.bin
-rw-r--r--  1 root root  823535 2008-02-12 05:39 System.map-2.6.22-14-generic
-rw-r--r--  1 root root  899892 2008-04-10 12:51 System.map-2.6.24-16-generic
-rw-r--r--  1 root root  905012 2008-05-01 13:59 System.map-2.6.24-17-generic
-rw-r--r--  1 root root  905012 2008-05-28 22:39 System.map-2.6.24-18-generic
-rw-r--r--  1 root root  905146 2008-06-04 16:50 System.map-2.6.24-19-generic
-rw-r--r--  1 root root 1764536 2008-02-12 05:39 vmlinuz-2.6.22-14-generic
-rw-r--r--  1 root root 1904248 2008-04-10 12:51 vmlinuz-2.6.24-16-generic
-rw-r--r--  1 root root 1921944 2008-05-01 13:59 vmlinuz-2.6.24-17-generic
-rw-r--r--  1 root root 1921528 2008-05-28 22:39 vmlinuz-2.6.24-18-generic
-rw-r--r--  1 root root 1920408 2008-06-04 16:50 vmlinuz-2.6.24-19-generic
scbash@maestro:~$
```

```
scbash@maestro:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=a8f5d9bb-d7ef-4e4c-a99e-2a4712b5c474 ro

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a8f5d9bb-d7ef-4e4c-a99e-2a4712b5c474 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a8f5d9bb-d7ef-4e4c-a99e-2a4712b5c474 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=a8f5d9bb-d7ef-4e4c-a99e-2a4712b5c474 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=a8f5d9bb-d7ef-4e4c-a99e-2a4712b5c474 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=a8f5d9bb-d7ef-4e4c-a99e-2a4712b5c474 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=a8f5d9bb-d7ef-4e4c-a99e-2a4712b5c474 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a8f5d9bb-d7ef-4e4c-a99e-2a4712b5c474 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a8f5d9bb-d7ef-4e4c-a99e-2a4712b5c474 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a8f5d9bb-d7ef-4e4c-a99e-2a4712b5c474 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a8f5d9bb-d7ef-4e4c-a99e-2a4712b5c474 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

scbash@maestro:~$ 
```

---

### Post by feisty john on 2008-06-18
Man, I'm stumped. Everything that I know of looks fine. I don't know if the presence of Windows XP along with Ubuntu could be confounding anything, but it shouldn't be. 

Anyone with more expertise have any ideas? Maybe mess around with your motherboard's settings?...

---

### Post by manfer on 2008-06-18
That looks like Bios is not finding disk. If it can't find disk it is impossible for it to find Master Boot Record on that disk to load grub.

I don't know that technology NAS (Network Attached Storage), but what I have read is that it is a server storage system that uses the TCP/IP protocol to communicate. So I suppose Bios should have the ability to boot from network devices to recognize disks on NAS. But only guessing, not sure.

---

