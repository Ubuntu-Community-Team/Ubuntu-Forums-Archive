---
title: "Cant boot windows"
date: 2007-02-25
forum: General Help
---

### Post by wobniarpro on 2007-02-25
Hi ppl,

i am new to uBuntu just installed it (n00b)


Please tell me why i cant use WINDOWS.

I have installed ubuntu (in partiotion) on a 75 GB hd with windows...


In menu i can see 4 ubuntu systems    and in  "other systems ": WINDOWS XP,,,,,,,, but when i try to start windows it seems that its going to start but after 1-2sec Pc reboots again and i have to choose ubuntu again...



reply me plz i have important stuff saved in windows and i have to recover that or i gonna die.....:confused:

---

### Post by highneko on 2007-02-25
If you need to access information from your windows partition then that wouldn't be a problem. It's not a fix but at least you can get the data. 

If I were in your position I would just want to make sure my data was ok. So if that's what you wanna do then boot up ubuntu and type the following commands into a terminal:

To open a terminal: Applications > Accessories > Terminal
```
df -h
sudo fdisk -l
ls / 

```

---

### Post by wobniarpro on 2007-02-25
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              23G  2.4G   20G  12% /
varrun                502M   84K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb             10M  128K  9.9M   2% /proc/bus/usb
udev                   10M  128K  9.9M   2% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   18M  485M   4% /lib/modules/2.6.17-11-generic/volatile
/dev/hdc              529M  529M     0 100% /media/cdrom0
user@user-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6609    53086761    7  HPFS/NTFS
/dev/hda2            6610        9598    24009142+  83  Linux
/dev/hda3            9599        9729     1052257+   5  Extended
/dev/hda5            9599        9729     1052226   82  Linux swap / Solaris
user@user-desktop:~$ ls /
bin    dev   initrd          lib         mnt   root  sys  var
boot   etc   initrd.img      lost+found  opt   sbin  tmp  vmlinuz
cdrom  home  initrd.img.old  media       proc  srv   usr  vmlinuz.old



---------




hey bro i got this,

I am dumb man i should never install new system :///

tell me plz what should i do to browse windows from linux



[[img=http://img87.imageshack.us/img87/2466/screenshotrr7.th.png]](http://img87.imageshack.us/my.php?image=screenshotrr7.png)

---

### Post by wobniarpro on 2007-02-25
:(

---

### Post by highneko on 2007-02-25
Thank you. We'll try to get you through this. Don't worry. n_n

```
sudo mkdir /windows
sudo mount /dev/hda1 /windows
gksudo nautilus /windows || gksudo konqueror /windows
```

---

### Post by wobniarpro on 2007-02-25
THANKS A LOT MAN

i got my files (mailing hehehh)


Now i can calm :D

ok now tell me how to make boot windows correctly,,,

---

### Post by highneko on 2007-02-25
Were you manually editing your grub config maybe? Sounds like a strange problem; Never heard of something like this. Maybe to get started you can paste your menu.lst:
```
gksudo gedit /boot/grub/menu.lst || gksudo kate /boot/grub/menu.lst
```

---

### Post by wobniarpro on 2007-02-25
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
# kopt=root=UUID=04d29c1d-51d1-46a0-b1e0-e6518a06e7c0 ro
# kopt_2_6=root=/dev/hda2 ro

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

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by highneko on 2007-02-25
Maybe try to remove the line "savedefault" closest to the bottom. Then reboot and try Windows.

---

### Post by wobniarpro on 2007-02-25
no way :/


Have same problem...

---

### Post by highneko on 2007-02-25
Did you save the file as root? Make sure it was saved. What error are you getting during boot attempts? Grub should be saying something.

---

### Post by wobniarpro on 2007-02-25
I saved it as u said,


No grub is not saying anything...


When i click on WINDOWS XP home edition it works then windows boot screen appears but compuer restarts again and i get grub again....

[[IMG]http://img512.imageshack.us/img512/8457/untitledpp4.jpg[/IMG]](http://imageshack.us)

---

### Post by wobniarpro on 2007-02-25
well well well,,,,


I had to format my disc and  :(  then at last now i have ubuntu/xp working on same hard disk with different partitions,,,,

---

