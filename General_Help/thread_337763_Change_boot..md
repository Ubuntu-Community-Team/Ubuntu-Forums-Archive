---
title: "Change boot."
date: 2007-01-13
forum: General Help
---

### Post by bugz0r on 2007-01-13
In the picture attached I want the highlighted line to boot and not the the second one. How do I do this?

---

### Post by meng on 2007-01-13
sudo fdisk /dev/sda
The option for make bootable is option 'a'

---

### Post by Hossie on 2007-01-13
Edit /boot/grub/menu.lst and change the value for "default" and "timeout". For finding out the correct number, you have to search the appropriate blocks for the operating systems at the end of the file and "count" them (it starts with 0).

&#8364;dith: Do you just want to change the boot-flag or do you really want to boot from that partition?

---

### Post by bugz0r on 2007-01-13
I want sda1 to boot and not the sda2.

I did what meng said and now both sda1 and 2 are checked but sda2 boots.

---

### Post by Hossie on 2007-01-13
If you want to boot sda1 (What is on sda1? Linux, Windows?), you have to edit menu.lst as above. The boot flag is not necessary on modern operating systems. Don't you already have a list of operating systems to choose from during boot?

---

### Post by meng on 2007-01-13
> **Hossie said:**
> If you want to boot sda1 (What is on sda1? Linux, Windows?), you have to edit menu.lst as above. The boot flag is not necessary on modern operating systems. Don't you already have a list of operating systems during boot?
Correct. You have to make clearer exactly what it is you're trying to achieve. If you want one of your Linux distros/partitions to be the default choice on startup, then you need to edit the boot menu. The bootable flag has nothing to do with it.

---

### Post by bugz0r on 2007-01-13
This is my menu.lst. what should I change?

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
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by Hossie on 2007-01-13
Something in your menu.lst is weird. You seem to have 2 Ubuntu Installations (?), at least the last recovery-entry points to sda1 ( because of hd0,0 ), but still specifies root as sda2. If thats what you want to boot (I dont think so), just change default 0 to default 3. Maybe you first tell us, what kind of operating system is on sda1.

---

### Post by bugz0r on 2007-01-13
I have Edgy on sda1 and had to install dapper on sda2 because I've been trying to gain access to edgy since yesterday because I think I might have messed up grub when I tried to install windows.

---

### Post by Hossie on 2007-01-13
Then post the output of your menu.lst from Edgy (just mount sda1 somewhere).

---

### Post by bugz0r on 2007-01-13
I get this. Do you think we can talk elsewhere such as IRC? I'm at #ubuntu at the moment and it would be more convenient.

```

salman@salman-desktop:~$ sudo mount -t ext3 /dev/sda1 /
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by Hossie on 2007-01-13
I find it quite convient here. ;) 

Do **not** mount it on /!

```
sudo mkdir /media/somedir
sudo mount /dev/sda1 /media/somedir
cat /media/somedir/boot/grub/menu.lst
```

---

### Post by bugz0r on 2007-01-13
same message again.

---

### Post by Hossie on 2007-01-13
There is something really weird. If you cant mount it, you probably cant boot it, also. What does

```
dmesg | tail
```

tell you?

---

### Post by bugz0r on 2007-01-13
```

salman@salman-desktop:~$ dmesg | tail
[17181635.352000] EXT3-fs: group descriptors corrupted !
[17181635.560000] EXT3-fs error (device sda1): ext3_check_descriptors: Block bitmap for group 1648 not in group (block 4294967288)!
[17181635.560000] EXT3-fs: group descriptors corrupted !
[17181647.440000] EXT2-fs: sda1: couldn't mount because of unsupported optional features (4).
[17181655.752000] EXT3-fs error (device sda1): ext3_check_descriptors: Block bitmap for group 1648 not in group (block 4294967288)!
[17181655.752000] EXT3-fs: group descriptors corrupted !
[17182105.432000] EXT3-fs error (device sda1): ext3_check_descriptors: Block bitmap for group 1648 not in group (block 4294967288)!
[17182105.432000] EXT3-fs: group descriptors corrupted !
[17182126.248000] EXT3-fs error (device sda1): ext3_check_descriptors: Block bitmap for group 1648 not in group (block 4294967288)!
[17182126.248000] EXT3-fs: group descriptors corrupted !

```

---

### Post by Hossie on 2007-01-13
See? The filesystem seems corrupted, you probably cant boot it. Try to fix it with e2fsck.

&#8364;: Or is it really that "unsupported features"? Has Edgy some e3 patches that Dapper doesnt support? Maybe you should wait with e2fsck beforce someone can say something about that. But if you cant find out the name of the initrd and the kernel, you probably cant create a boot entry for sda1.

---

### Post by bugz0r on 2007-01-13
is there anyway I can save any of my files from the edgy partition?

---

### Post by Hossie on 2007-01-13
I really dont know about that "unsupported features". You could try with a (recent) LiveCD, though, like the relatively new Knoppix 5.1.1. Maybe someone here has the default initrd and kernel-image names for a grub entry? Or did you already install patches?

---

