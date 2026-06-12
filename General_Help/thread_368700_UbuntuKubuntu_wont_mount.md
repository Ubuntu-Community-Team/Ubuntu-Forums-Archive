---
title: "Ubuntu/Kubuntu wont mount"
date: 2007-02-23
forum: General Help
---

### Post by Lgndryhr on 2007-02-23
Hi. I joined these forums because I am here all the time reading for help and what not as well as interesting tips. I finally joined because no one seemed to have my problem.

I cannot get my Ubuntu/Kubuntu (i have gnome and kde both installed) to load. When I select the kernel from grub it boots and when it gets to Mounting system root file it freezes and takes me back to the screen with info of kernel loading sequence i would find in menu.lst. I am wondering what can be causing this. I have it installed on its own HDD separate from my Windows. I have version 6.06 with kernel 2.6-15-28-386.

---

### Post by taurus on 2007-02-23
Is there an error message about root partition when it boots up?

Otherwise, boot with the LiveCD, mount your harddrive, asusming it's /dev/hdb1

Applications -> Accessories -> Terminal (for Ubuntu)
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hdb1 /mnt/ubuntu
```
and post the outputs of these two commands here.

```
cat /mnt/ubuntu/etc/fstab
cat /mnt/ubuntu/boot/grub/menu.lst
```

---

### Post by Lgndryhr on 2007-02-23
results from  cat /mnt/ubuntu/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
/dev/sda1  /mnt/PSP  vfat  noauto,noatime,users,shortname=win95,check=s  0 0

results from cat /mnt/ubuntu/boot/grub/menu.lst (spaces around "8's" so it doesnt show up as smiley faces)

# menu.lst - See: grub( 8 ), info grub, update-grub( 8 )
#            grub-install( 8 ), grub-floppy( 8 ),
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

title           Ubuntu, kernel 2.6.15-28-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.15-28-386
boot

title           Ubuntu, kernel 2.6.15-27-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by Lgndryhr on 2007-02-23
hey i am off to work so anything posted in here i wont be able to test until later tonight.

EDIT: Now it is mounting and loading just fine. Idk why it is now. I tried like 10 times earlier and it wouldn't. Strange. Very odd. I would still like to know what caused this so please don't lock this thread.

---

### Post by taurus on 2007-02-23
That is real strange because you have declared /dev/sda1 as ext3 _and_ vfat at the same time, according to /etc/fstab!

```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
**/dev/sda1 / ext3 defaults,errors=remount-ro 0 1**
/dev/sda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0
**/dev/sda1 /mnt/PSP vfat noauto,noatime,users,shortname=win95,check=s 0 0**

```

What's the output of this command from a terminal then?

```
sudo fdisk -l
```

---

### Post by Lgndryhr on 2007-02-24
> **taurus said:**
> That is real strange because you have declared /dev/sda1 as ext3 _and_ vfat at the same time, according to /etc/fstab!

```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
**/dev/sda1 / ext3 defaults,errors=remount-ro 0 1**
/dev/sda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0
**/dev/sda1 /mnt/PSP vfat noauto,noatime,users,shortname=win95,check=s 0 0**

```

What's the output of this command from a terminal then?

```
sudo fdisk -l
```


ah those. if you read one is for psp so i can read and write to it using an usb cable. anyways the outcome from that is:

```
Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35916   288495238+  83  Linux
/dev/sda2           35917       36483     4554427+   5  Extended
/dev/sda5           35917       36483     4554396   82  Linux swap / Solaris

Disk /dev/hda: 120.0 GB, 120060444672 bytes
240 heads, 63 sectors/track, 15508 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       15507   117232888+   7  HPFS/NTFS
```

also do i need to keep that stuff in the mnt folder? 

oh and when it did finally boot up before i left for work it did the usual forced check thing after 30 mounts and near the end it received some sort of fail thing and restarted and now boots just fine.

---

### Post by taurus on 2007-02-24
PSP or not, it should not have the same name as your harddrive.  It should have been /dev/sdb1.  Plug it in and post this output again.

```
sudo fdisk -l
```

---

### Post by Lgndryhr on 2007-02-24
not sure if you saw in my last post but....
do i need to keep that stuff in the mnt folder?
oh and when it did finally boot up before i left for work it did the usual forced check thing after 30 mounts and near the end it received some sort of fail thing and restarted and now boots just fine.

> **taurus said:**
> PSP or not, it should not have the same name as your harddrive.  It should have been /dev/sdb1.  Plug it in and post this output again.

```
sudo fdisk -l
```

really? oh. everything i read said to have it that way. anyways here is the output again
```
Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35916   288495238+  83  Linux
/dev/sda2           35917       36483     4554427+   5  Extended
/dev/sda5           35917       36483     4554396   82  Linux swap / Solaris

Disk /dev/hda: 120.0 GB, 120060444672 bytes
240 heads, 63 sectors/track, 15508 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       15507   117232888+   7  HPFS/NTFS

```

---

### Post by taurus on 2007-02-24
Did you plug in your psp and was it on because there is no info regarding it at all?

---

### Post by Lgndryhr on 2007-02-24
> **taurus said:**
> Did you plug in your psp and was it on because there is no info regarding it at all?

oh i thought u meant plug in the /dev/sdb1 in place of dev/sda1. opps sorry lemme go get it.


here it is.

```
Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35916   288495238+  83  Linux
/dev/sda2           35917       36483     4554427+   5  Extended
/dev/sda5           35917       36483     4554396   82  Linux swap / Solaris

Disk /dev/hda: 120.0 GB, 120060444672 bytes
240 heads, 63 sectors/track, 15508 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       15507   117232888+   7  HPFS/NTFS

Disk /dev/sdf: 4098 MB, 4098883584 bytes
128 heads, 63 sectors/track, 992 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1         992     3999649    c  W95 FAT32 (LBA)

```

---

### Post by taurus on 2007-02-24
You need to replace this line in /etc/fstab

```

/dev/sda1 /mnt/PSP vfat noauto,noatime,users,shortname=win95,check=s 0 0

```
with this line since your PSP is /dev/sdf1.

```

/dev/sdf1 /mnt/PSP vfat noauto,noatime,users,shortname=win95,check=s 0 0

```

---

### Post by Lgndryhr on 2007-02-24
> **taurus said:**
> You need to replace this line in /etc/fstab

```

/dev/sda1 /mnt/PSP vfat noauto,noatime,users,shortname=win95,check=s 0 0

```
with this line since your PSP is /dev/sdf1.

```

/dev/sdf1 /mnt/PSP vfat noauto,noatime,users,shortname=win95,check=s 0 0

```

other than that was there anything else wrong? or any idea why my linux would not mount but will now.

---

### Post by taurus on 2007-02-24
Does it, /dev/sdf1, mount when you plug it in?

```
df -h
```

---

### Post by Lgndryhr on 2007-02-24
> **taurus said:**
> Does it, /dev/sdf1, mount when you plug it in?

```
df -h
```

it wont even mount. 
i get
```

mount: mount point /mnt/PSP does not exist
Please check that the device is plugged correctly.

``` in a window

and output from dh -h is 
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             271G   38G  220G  15% /
varrun                760M   88K  760M   1% /var/run
varlock               760M  4.0K  760M   1% /var/lock
udev                  760M  156K  760M   1% /dev
devshm                760M     0  760M   0% /dev/shm
/dev/hda1             112G   72G   41G  64% /media/windows

```

now upon changing /dev/sdf1 back to /dev/sda1 the output is
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             271G   38G  220G  15% /
varrun                760M   88K  760M   1% /var/run
varlock               760M  4.0K  760M   1% /var/lock
udev                  760M  156K  760M   1% /dev
devshm                760M     0  760M   0% /dev/shm
/dev/hda1             112G   72G   41G  64% /media/windows
/dev/sdf1             3.9G  3.4G  478M  88% /media/sdf1

```

---

### Post by taurus on 2007-02-24
It didn't mount to /mnt/PSP; instead, it's mounted to /media/sdf1.

```
**/dev/sdf1             3.9G  3.4G  478M  88% /media/sdf1**
```
So, 

```
ls -la /media/sdf1
```

Otherwise, create a new mount it if you want to mount it to /mnt/PSP.

```
sudo mkdir /mnt/PSP
```
And please don't change it back to /dev/sda1 in /etc/fstab since it is NOT /dev/sda1; it is /dev/sdf1.

---

### Post by Lgndryhr on 2007-02-24
> **taurus said:**
> It didn't mount to /mnt/PSP; instead, it's mounted to /media/sdf1.

```
**/dev/sdf1             3.9G  3.4G  478M  88% /media/sdf1**
```
So, 

```
ls -la /media/sdf1
```

Otherwise, create a new mount it if you want to mount it to /mnt/PSP.

```
sudo mkdir /mnt/PSP
```
And please don't change it back to /dev/sda1 in /etc/fstab since it is NOT /dev/sda1; it is /dev/sdf1.

i made a new mount and notice a significantly faster mount and unmount time. thanks but this still has not answered my question lol. i greatly appreciate your help though with that and in organizing/cleaning up my linux since I know no one using it and have no one to ask for advice, etc.

---

### Post by taurus on 2007-02-24
Are you talking about the problem loading the kernel?  Maybe because you have a wrong entry for your /, /dev/sda1, in /etc/fstab.  You are not supposed to have this line in there.

```

/dev/sda1 /mnt/PSP vfat noauto,noatime,users,shortname=win95,check=s 0 0

```
Instead, it should have been

```

**[COLOR="Red"]/dev/sdf1[/COLOR]** /mnt/PSP vfat noauto,noatime,users,shortname=win95,check=s 0 0

```

---

### Post by Lgndryhr on 2007-02-24
ah...but why did it stop working now? i've had ubuntu since sept of 06' with that line added to fstab and never experienced any problems till today.
oh and btw can i delete the thing i added to mnt? not the PSP one but the other.

---

### Post by taurus on 2007-02-24
What do you want to delete in /mnt?

---

### Post by Lgndryhr on 2007-02-24
> **taurus said:**
> What do you want to delete in /mnt?

when you had me
```

sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hdb1 /mnt/ubuntu

```

---

### Post by taurus on 2007-02-24
> **Lgndryhr said:**
> when you had me
```

sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hdb1 /mnt/ubuntu

```

That was from the LiveCD!  What's the output of this command then?

```
ls -la /mnt
```

---

### Post by Lgndryhr on 2007-02-24
> **taurus said:**
> That was from the LiveCD!  What's the output of this command then?

```
ls -la /mnt
```

here is the result. i know what its from but when i put it in and loaded alongside my kernel, my kernel started to load normal so it didnt load using the LiveCD I believe.  i still did that anyways so you could help me. which i am thankful for.
```

total 24
drwxr-xr-x  6 root root 4096 2007-02-24 00:22 .
drwxr-xr-x 22 root root 4096 2007-02-09 15:41 ..
drwxr-xr-x  2 root root 4096 2007-02-24 00:22 PSP
drwxr-xr-x  2 root root 4096 2007-02-23 15:47 ubuntu
drwxr-xr-x  2 root root 4096 2006-08-31 17:33 win
drwxr-xr-x  2 root root 4096 2006-08-31 16:44 windows

```

---

### Post by taurus on 2007-02-24
So I guess you want to remove /mnt/ubuntu, eh.

```
sudo rmdir /mnt/ubuntu
ls -la /mnt
```
And now it's gone.

---

### Post by Lgndryhr on 2007-02-24
i could have removed it myself lol but thanks for always providing the code so i could make sure i was doing it right. yea i wanted to since i was not using it anymore. i guess then you have "fixed" my problem. if so then i greatly thank you.

---

### Post by taurus on 2007-02-24
If everything boots fine and you can use your PSP, I guess your problem's solved then!  And it means I am outta here...

---

### Post by Lgndryhr on 2007-02-24
> **taurus said:**
> If everything boots fine and you can use your PSP, I guess your problem's solved then!  And it means I am outta here...

well i did a restart and my boot was fine. my psp mounted and unmounted just fine. so i guess you're outta here. thanks again.

---

