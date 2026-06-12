---
title: "Changing GRUB Splash"
date: 2007-04-21
forum: General Help
---

### Post by b0ng0 on 2007-04-21
I have tried following the guide on Ubuntuguide.org however, when it gets to the bit where GRUB splash should load it says "Failed to load /boot/blahblah..."

I'm pretty sure I have it set up right, the only thing I could think would be wrong would be the (hd0,1) section but i've no idea what I could change those to, or how to find out what they mean. Thanks for any help

---

### Post by punong_bisyonaryo on 2007-04-21
(hd0,1) refers to your first harddrive's second partition. the harddrive number is the number beside hd, starting with 0, so your second harddrive would read hd1. The partition number is the second paramter and is numbered 0 onwards

More detail regarding your drives/partition would be useful. You probably just put in the wrong numbers.

Let's fix some stuff
1. Boot into liveCD.
2. mount your Ubuntu partition
```
sudo mkdir /media/hda1
sudo mount /dev/hda1 /media/hda1 -t ext3
```
take note that hda1 refers to your first harddrive, first partition. the "a" being the drive.
3. chroot /media/hda1
4. edit your menu.lst file as you had before.

---

### Post by Compyx on 2007-04-21
> **punong_bisyonaryo said:**
> (hd0,1) refers to your first harddrive's first partition. 

No it doesn't, (hd0,0) refers to your first drive's first partition.

---

### Post by punong_bisyonaryo on 2007-04-21
> **Compyx said:**
> No it doesn't, (hd0,0) refers to your first drive's first partition.

Thank you for the constructive, albeit frank, correction.:) 

Compyx is absolutely right, my bad.

---

### Post by b0ng0 on 2007-04-21
Thanks, i'll try that out.

---

### Post by Compyx on 2007-04-21
On my system, I have a single partition for Ubuntu at /dev/hda10, so my grub entry for the splashscreen looks like this:
```
splashimage=(hd0,9)/boot/grub/splashimages/fiesta.xpm.gz
```

Should you have a separate /boot partition at /dev/hda1, you would probably use an entry like this:
```
splashimage=(hd0,0)/grub/splashimages/fiesta.xpm.gz
```
leaving out "/boot" in the entry since /dev/hda1 gets mounted at /boot in your root partition.

---

### Post by b0ng0 on 2007-04-21
Thanks. I checked the filesystem and my Ubuntu is installed on sda3 so would I have (hd0,3) or (sd0,3)?

Also, how do I know if it is installed on a seperate boot partition?

Thanks

---

### Post by Compyx on 2007-04-21
Probably (sd0,2), you can check your /boot/grub/system.map file to see how the drive(s) is/are mapped:
```
cat /boot/grub/device.map
```

To check if /boot is on a separate partition, you can check /etc/fstab, if there's a line with /boot in it, you have a separate /boot partition:
```
grep '/boot' /etc/fstab
```

---

### Post by b0ng0 on 2007-04-21
Hmm the cat command lists my sda drive as hd0. But I have tried (hd0,*) where * has been 0-3 and none of them seem to work..

---

### Post by Compyx on 2007-04-21
Can you post your /etc/fstab and /boot/grub/menu.lst files? Maybe then I'll be able to see what the problem is. And the output of
```
ls -l /boot/grub/splashimages
```

---

### Post by b0ng0 on 2007-04-21
Fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=228cce41-6386-4bce-9ac6-180c7e527ef7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=4647e854-70f2-4af6-a753-f1e4353a29ed /home           ext3    defaults        0       2
# /dev/sda1
UUID=646C0DA96C0D7758 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=70F44DCCF44D94EE /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=20bebf77-5c22-4bfa-83bb-24d81a8d31f5 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

--------------------------------------------------------------------------------------------------------------------------

Grub Menu.lst

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

splashimage=(hd0,3)/boot/grub/splashimages/36907-Blu.xpm.gz

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
timeout		5

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
# kopt=root=UUID=228cce41-6386-4bce-9ac6-180c7e527ef7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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


title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=228cce41-6386-4bce-9ac6-180c7e527ef7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=228cce41-6386-4bce-9ac6-180c7e527ef7 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

-----------------------------------------------------------------------------------------------------------------

Output of ls

-rw-r--r-- 1 root root 52973 2007-04-20 19:37 36907-Blu.xpm.gz

---

### Post by Compyx on 2007-04-21
Thank you for posting your info.

From the looks of it:
```
splashimage=(hd0,2)/boot/grub/splashimages/36907-Blu.xpm.gz
```
should work.

If not, you might have a typo somewhere, or there's something else going on I can't see.

---

### Post by b0ng0 on 2007-04-21
Thanks, i'll try that out and let you know if it works. :)

---

### Post by Compyx on 2007-04-24
I might have found a 'fix' for this: for some reason, Grub cannot interpret the file correctly. After some poking around I noticed that when gunzipping the file, loading and saving it with the Gimp and then gzipping it again (and placing it in /boot/grub/splashimages) the file gets loaded and displayed correctly.

After examining the original file and the newly saved one, the palette section of the xpixmap-file had changed, so perhaps the original palette used a color-index that grub needs to display it's text. Who knows? I'm not an expert on either graphic formats or grub :)

But this 'solution' at least worked on my system, so give it a go, I'd say.

---

### Post by b0ng0 on 2007-04-24
Thanks, it's now working.

---

### Post by robdom on 2007-04-29
J have the same problem at boot grub said :  failed to read splashimage.

J used a 640x480  xpm with 16 colours  converted by convert from a jpg


with what parameter have You saved the file ?

Thanks in advance

---

