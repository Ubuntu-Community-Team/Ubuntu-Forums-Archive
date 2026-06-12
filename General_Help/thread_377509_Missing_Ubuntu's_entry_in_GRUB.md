---
title: "Missing Ubuntu's entry in GRUB"
date: 2007-03-06
forum: General Help
---

### Post by vnt87 on 2007-03-06
I just recently screwed up the permission settings in my Edgy to an unrecoverable point, so I had to make a clean install.
The re-installation process went smoothly but after restarting, the GRUB screen only shows me 2 entries: the Ubuntu memtest, and Windows XP (which I had installed on a different partition). There were no entry with the kernel version which I often see when booting into Ubuntu. I wonder how I can add them back.
Sorry for my broken English, hope you can understand what I mean.

---

### Post by Herman on 2007-03-06
Hello vnt87,
You might need to use [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to boot with so you can fix your menu.lst file easliy. Right now you can't fix the file because you can't boot, and you can't boot because you can't fix the file... so you are stuck! 
  Don't worry, SGD to the rescue!
  [LIST=1]
[*]boot your SGD floppy disk, USB disk or CD-ROM
[*]English Super Grub Disk
[*]Gnu/Linux
[*]Boot Gnu/Linux Directly[/LIST]   
  'Boot Gnu/Linux Directly' will bypass the menu.lst file and boot your Linux OS via symlinks to the kernel in the root of the filesystem.

Now that you have Ubuntu booted up, run 'sudo update-grub', that runs a script that should regenerate your menu.lst file for you automatically, and with good luck it should be fixed.```
sudo update-grub
```
If that doesn't fix it, try making a backup copy of the file and deleting the original one and try again.
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```
```
sudo update-grub
```
If it still doesn't work, tell me and I'll think of a new idea. Probably you can just type it in yourself or paste it in, but only if you have to.

Regards, Herman :)
****[B]
  [/B]

---

### Post by vnt87 on 2007-03-07
Thanks for your help. I got it. I simply made a fresh reinstall and it worked! But I'll keep your advice in mind, it'll sure come in handy for the future. I have a tendency to crash my computer every week or so :D

---

### Post by Watergeus on 2007-03-07
Sorry to break in. Have more or less the same problem with a different cause...

I'm running Ubuntu Edgy Eft and have a problem with upgrading to a newer kernel.

I still run with an 2.6.17-10-generic while I can see the new kernel in the root of the system. I want to run the newest version but this doesn't show up in the Grub startup screen.

Sysinfo while running:

Kernel: 2.6.17-10-generic
Build time: #1 SMP Fri Dec 15 02:09:09 CET 2006
Gnome version: 2.16.1 - Ubuntu (2006-10-02)
GCC version: 4.1.2 - i486-linux-gnu 

After I manually edit the grup-menu (with "e" and then changing the 10 for 11) in the two relevant lines of the startup the following sysinfo:

	Kernel: 2.6.17-11-generic
	Build time: #1 SMP Wed Feb 14 07:22:03 CET 2007

So, the new kernel is installed and can work.

I manually edit the grub-file (see below for the content of the file):

sudo nano /boot/grub/menu.lst
I think everything is OK, close the file and do:

sudo update-grub, and that gives:

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... found: (hd0,4)/boot/grub/splashimages/bike_gua.xpm.gz

Found kernel: /boot/vmlinuz-2.6.17-11-386
Found kernel: /boot/vmlinuz-2.6.17-11-generic
Found kernel: /boot/vmlinuz-2.6.17-10-386
Found kernel: /boot/vmlinuz-2.6.17-10-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Reboot, but don't see my newer kernels in the grub-menu.
How can I get the newer kernels in my grub-startup menu?

Downloaded SuperGrub ([http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)) but don't know how to use it in my situation. (I still can startup with the "10"-kernel.

Tia,
Paul.

------------------output of /boot/grub/menu.lst-------------------------------

# Splashimage line added by kubuntu-grub-splashimages package
splashimage=(hd0,4)/boot/grub/splashimages/bike_gua.xpm.gz

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
# kopt=root=UUID=a124ac36-cbae-409e-8f72-23ef3879f9ae ro
# kopt_2_6=root=/dev/sda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
# defoptions=quiet splash resume=/dev/sda3

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

title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-386 root=/dev/sda5 ro quiet splash resume=/dev/sda3
initrd		/boot/initrd.img-2.6.17-11-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-386 root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.17-11-386
boot

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda5 ro quiet splash resume=/dev/sda3
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda5 ro quiet splash resume=/dev/sda3
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash resume=/dev/sda3
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1

----

---

### Post by Herman on 2007-03-09
Hello Watergeus,
I cannot see any problem with your menu.lst file. You should be getting a grub menu with the choice to select the new kernels from that menu.lst.
To make sure of it, I copied the bottom part of your menu.lst out of your post and made a backup of my Edgy Eft menu.lst. Then I pasted your grub entries over the top of mine, overwritting my own with a copy of yours.
the result was on reboot I have a grub menu with your new up to date kernels all showing all A-OK! :)

I am trying to imagine what could be wrong, and make some sort of a guess. I can only guess that possibly your grub menu that you are booting from is not the grub menu from the menu.lst you are currently maintaining in your Edgy Eft /boot/grub directory.
Do you have another Ubuntu install somewhere in this computer? Or maybe a separate grub partition? There must be some logical reason for this strange problem.
Please post the output from 'sudo fdisk -lu' here along with an explanation of what each partition has in it. ```
sudo fdisk -lu
```Also, are you booting up with any other drives plugged in, such as a USB disk? If so can you try unplugging that and see if that makes a difference.  

Regards, Herman :)

---

### Post by Watergeus on 2007-03-09
Hello Herman, 

I think you pointed me in the right direction, but I have no idea how to repair it.

>...possibly your grub menu that you are booting from is not the grub menu from 
>the menu.lst you are currently maintaining in your Edgy Eft /boot/grub 
>directory.
>Do you have another Ubuntu install somewhere in this computer? Or maybe a 
>separate grub partition? There must be some logical reason for this strange 
>problem.

I have an other partition with an experimental Debian OS...it's not working any more and I would like to reformat the partition. In fact in the GRUB startup menu I first get a number of Debian startup options, then the Ubuntu options and then the Window-option.
Does this mean that GRUB starts from the Debian Partition?

grub> find /boot/grub/stage1
 (hd0,4)
 (hd0,6)

hd0,4 = My current /root partition of Ubuntu Edgy
hd0,6 = Debian /root partition that is of no use any more

So, how to I get the MBR(?) to hd0,4? 
I want to be absolutely sure. I don't want to reinstall my edgy.

I notice now that it is a terrible mess. 
I can mount sda(1,2,6,7,8).
sda6 it's content is my old Debian system??!! It should be sda7, at least that's how it is in the fstab.
And sda7 and sda8 don't show any files (not even with sudo).

Can you give me an advice to repair this mess foolproof?
Do I have to use qtparted first? And then edit fstab? And then do something with GRUB?
Or first GRUB?

Tia,
Paul.

------------------------
EXTRA INFO
------------------------
```

---
~$ sudo fdisk -lu
---
Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders, total 153356490 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  de  Dell Utility
/dev/sda2   *       96390    61528949    30716280    7  HPFS/NTFS
/dev/sda3       147075075   153356489     3140707+  82  Linux swap / Solaris
/dev/sda4        61528950   147042944    42756997+   f  W95 Ext'd (LBA)
/dev/sda5        61529013   102494699    20482843+  83  Linux
/dev/sda6       106591338   108695789     1052226    b  W95 FAT32
/dev/sda7       108695853   123363134     7333641   83  Linux
/dev/sda8       123363198   147042944    11839873+  83  Linux

Partition table entries are not in disk order

```
---
Output of parted print:
---
```

Disk /dev/sda: 78.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  49.4MB  49.3MB  primary   fat16
 2      49.4MB  31.5GB  31.5GB  primary   ntfs         boot
 4      31.5GB  75.3GB  43.8GB  extended               lba
 5      31.5GB  52.5GB  21.0GB  logical   ext3
 6      54.6GB  55.7GB  1077MB  logical   fat32
 7      55.7GB  63.2GB  7510MB  logical   ext3
 8      63.2GB  75.3GB  12.1GB  logical   ext3
 3      75.3GB  78.5GB  3216MB  primary   linux-swap

```
---
Here comes the /etc/fstab of the Edgy (hd0,4)...
---
```

::::::::::::::
/etc/fstab
::::::::::::::
# /etc/fstab: static file system information.
#
# <file system>         <mount point>  <type>  <options>                <dump>  <pass>
proc                             /proc           proc    defaults                0       0

## /dev/sda5 = Ubuntu part (ext 32, 20Gb)
UUID=a124ac36-cbae-409e-8f72-23ef3879f9ae       /               ext3    defaults,errors=remount-ro 0       1

## /dev/sda1  = Dell toolbox (fat16, 47Mb)
UUID=07D6-0703                                  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1

## /dev/sda2 = Windows partition (ntfs, 30 Gb), BOOT
#UUID=4C84E23784E222E6                          /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
#/dev/sda2                              /media/sda2     ntfs-3g auto,gid=1003,umask=0002        0       0
#this worked exept 2byte chars, Ktorrent crashed!
#Have to find correct option description for ntfs-3g to accept Spanish, French... 
/dev/sda2                               /media/sda2     ntfs-3g  auto,user,nls=utf8     0       0

## /dev/sda6 = Windows part (fat32, 1Gb), check content & reformat
UUID=5BD9-D183                                  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1

## /dev/sda7 = Debian part ROOT (ext32); cleanup needed
UUID=ed08d89a-a565-4a39-8527-d41e8b318173      /media/sda7     ext3    defaults, errors=remount-ro        0       2

## /dev/sda8 = Ubuntu and Debian HOME, why is de UUID commented out and is the old style used?
# /dev/sda8                                     /home ext3 nodev,nosuid 0 2
# /dev/sda8     (this was there)                /media/sda8     ext3                    0       2
UUID=be2987ab-8300-4115-aaf3-b34f94aca24b       /home           ext3    nodev,nosuid    0       2

## /dev/sda3 = SWAP part
#UUID=2aea654e-890a-4766-b148-a4fe286051ed      none            swap    sw              0       0
#bug?? try this:
/dev/sda3                                       none            swap    sw              0       0

## CDROM
/dev/scd0

```

---

### Post by Herman on 2007-03-09
> I have an other partition with an experimental Debian OS...it's not working any more and I would like to reformat the partition. In fact in the GRUB startup menu I first get a number of Debian startup options, then the Ubuntu options and then the Window-option.
Does this mean that GRUB starts from the Debian Partition?Yes, that's most likely what your problem is then. :)

Here's what you should do,
```
sudo grub
``````
 grub> find /boot/grub/stage1
 (hd0,4)
 (hd0,6)
``````
grub> root (hd0,4)
``````
grub> setup (hd0)
``` ```
grub> quit
``` That should clear up your booting problems. :)

Now for what to do with your old debian partition. You can just delete it or re format it with QTParted if you like, or just leave it there. What was the problem with it anyway? Maybe it can easily be repaired. The fact that you can't mount it seems to me to indicate that possible it has a corrupted file system. Most of the time, that can easily be repaired. The simplest way to have your filesystems repaired is to use a [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") and just right-click on the partition and click 'check' from the menu. GParted Live CD can automatically check repair most filesystem problems for you even if you don't know any Linux commands yet. If it can't you can can also click the little triangular arrows to expand GParted LiveCD's operation report to see the details of what has been done and what's left that needs doing. Sometimes it will advise you to run another command manually. You might want to try that before you give up and delete the partition. 
This might fix it, from Ubuntu, while it is not mounted, ```
 sudo e2fsck -C0 -p -f -v /dev/sda7
```If you still want to re-format or delete your old debian partition, you should comment out the line in your /etc/fstab file that refers to the that partition by placing a hash mark before the UUID number for it for now. Like this,
```
 ## /dev/sda7 = Debian part ROOT (ext32); cleanup needed
[COLOR=Red]** # **[/COLOR]UUID=ed08d89a-a565-4a39-8527-d41e8b318173      /media/sda7     ext3    defaults, errors=remount-ro        0       2
```GParted LiveCD is also my favorite software for doing all kinds of operations like that. QTParted is fine too, but GParted LiveCD is the most advanced and  up to date partitioning software available at the moment. The GParted developers are extremely active, and are doing a lot of hard work on it every day so it just keeps getting better and better.:)

Regards, Herman :)

---

### Post by Watergeus on 2007-03-16
Herman,

You hit the nail on the head.

I had no idea that the 'GRUB' first was looking at the 'wrong' partition. Now I know.

Will reformat the other partition and use it to do some fun stuff like trying out Feisty :) 

Thanks for helping me,
Paul

---

### Post by Herman on 2007-03-17
Hello Watergeus,
Thanks for the feedback, and yes, Fiesty is very nice, The Ubuntu developers are hard workers and they are doing a brilliant job. They are always coming up with new ideas and making Ubuntu better and better. It's fun to have a test install just to see how they are getting along.

Regards, Herman :)

---

