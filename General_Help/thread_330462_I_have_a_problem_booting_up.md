---
title: "I have a problem booting up"
date: 2007-01-03
forum: General Help
---

### Post by prc320 on 2007-01-03
Hi

I have a problem when I boot up, it goes through a boot seqence then comes up with error code 15 file not found. If I take one of the options it takes me back to code 15.

I have put clamav and klamav and I think this maybe the problem.

Help, at the moment I am using windows pc

Robert

---

### Post by MiCovran on 2007-01-03
Are you using GRUB? If you are, try reinstalling it: [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

If it doesn't work, post the output of ```
sudo fdisk -l
``` and contents of "/boot/grub/menu.lst".

Good luck.

---

### Post by prc320 on 2007-01-03
I tried reinstalling it but I still gives me error code 15 file not found so:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4791    38483676   83  Linux
/dev/hda2            4792        4998     1662727+   5  Extended
/dev/hda5            4792        4998     1662696   82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1            4238        4997     6104700    f  W95 Ext'd (LBA)
/dev/hdb5            4238        4997     6104668+   b  W95 FAT32

Disk /dev/sda: 507 MB, 507322880 bytes
16 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         983      495313+   6  FAT16
ubuntu@ubuntu:~$ 
[COLOR="Red"][/COLOR]
how do I get the contents of "/boot/grub/menu.lst"?

---

### Post by MiCovran on 2007-01-03
> how do I get the contents of "/boot/grub/menu.lst"?

I forgot to say this, sorry. I forgot that you can't boot. ](*,) 

You first have to mount your "/" partition. Don't mind what it all means, just type this:
```
sudo mount /dev/hda1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```

I think something is wrong with grub configuration.

---

### Post by MiCovran on 2007-01-03
By the way, is just ubuntu on this machine, or is it dual boot?

---

### Post by prc320 on 2007-01-03
ubuntu@ubuntu:~$ sudo mount /dev/hda1/mnt
mount: can't find /dev/hda1/mnt in /etc/fstab or /ect/mtab

I have two machines, one is ubuntu and in other in windoze!

---

### Post by MiCovran on 2007-01-03
> ubuntu@ubuntu:~$ sudo mount /dev/hda1/mnt
mount: can't find /dev/hda1/mnt in /etc/fstab or /ect/mtab
Not "sudo mount /dev/hda1/mnt", "sudo mount /dev/hda1 /mnt".
Be carefull about the spaces. Put a space before "/mnt".

I was thinking, maybe the simplest way to solve the situation would be to install Ubuntu from live CD once again, but without formatting the partitions.
You select "partition manually" in the installation process and leave partitions as they are. Then you select all the same mount points and simply do not reformat any partitions.
You can try it, or send me the menu.lst file. I had a similar problem when I messed something up in windows and couldn't boot. However, I have a dual boot and I don't know if this is the same situation with you.
Anyway, you have nothing to lose.

---

### Post by prc320 on 2007-01-04
Hi

Here it is:

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
## menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=e9f3b8e9-9d1c-4fc9-ba74-aa18c8061a10 ro
# kopt_2_6=root=/dev/hda1 ro

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by MiCovran on 2007-01-04
Try to delete lines 38 to 71 (between "#examples" and "# title Windows 95/98/NT/2000").

Looks like someone doubled all from 1st to the 34th line. I don't know if this will help, but I hope it will. I don't see any other flaws, I compared it with my "menu.lst".

Just type ```
sudo mount /dev/hda1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
``` remove those lines, save, reboot and hope for the best.

---

### Post by prc320 on 2007-01-04
ok I will try that now!

---

### Post by prc320 on 2007-01-12
Hi

Well I have almost got it sorted, it has been a bit of a nightmare.........

It was Klamav/Clamav. For what they did was move them into quarantine my */boot/initrd.img-2.6.17-10-generic *in */klamav.................. *That broken the link to */initrd.img *meaning it would never work unfortunately. You helped me by giving me a *mount /dev/hda1 /mnt *this did a mount to enable me to copy it off to another machine and start again. For that I thank you very much

---

