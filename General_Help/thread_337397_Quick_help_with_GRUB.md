---
title: "Quick help with GRUB"
date: 2007-01-12
forum: General Help
---

### Post by FreakinSyco on 2007-01-12
Ive recently installed Vista and the Feisty Fawn Herd-2 and would like to dual boot them. I've read a bunch of help but have one last minor question.

Ive installed Vista on a seperate SATA hdd and Ubuntu on an IDE hdd (vista first then ubuntu). I can boot into Ubuntu but do not have the option for Vista. I know I need to add an entry to the /boot/grub/menu.lst but I dont know how to enter it correctly to get it to work.

Heres the current menu.lst

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
# kopt=root=UUID=be59f331-24bd-4806-bb3e-99f9a8183fb2 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-5-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-5-generic root=UUID=be59f331-24bd-4806-bb3e-99f9a8183fb2 ro quiet splash
initrd		/boot/initrd.img-2.6.20-5-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-5-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-5-generic root=UUID=be59f331-24bd-4806-bb3e-99f9a8183fb2 ro single
initrd		/boot/initrd.img-2.6.20-5-generic

title		Ubuntumemtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title         "Windows Vista"
root         (sd0,0)
chainloader      +1

### END DEBIAN AUTOMAGIC KERNELS LIST

```

and heres the output of "fdisk -l". The 40gig IDE is dedicated to Ubuntu only, the 80gig IDE is my music/media drive and the 250gig SATA is Vista (not all partitioned out at the moment).

```

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4665    37471581   83  Linux
/dev/sda2            4666        4870     1646662+   5  Extended
/dev/sda5            4666        4870     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9733    78180291    b  W95 FAT32

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3188    25600000    7  HPFS/NTFS
/dev/sdc2            3188        5737    20480000   83  Linux
```

Would the entry:

title         "Windows Vista"
root         (sd0,0)
chainloader      +1

in grub be correct? Thanks for any help.

---

### Post by Shatrat on 2007-01-12
Try it, it won't hurt anything if it is off by a letter or a number.

---

### Post by katalyst23 on 2007-01-12
This is what I have in my grub file to boot windows:

title		Windows XP
root		(hd1,0)
map		(hd1) (hd0)
map		(hd0) (hd1)
chainloader +1


I remember reading somewhere that you need to map the drives to pull the ol' switcheroo on windows so it thinks it's using its mbr or something like that...
Also, if you screw the spacing up, you will get a weird error from grub.  (Something like error 11: unrecognized string)

---

### Post by FreakinSyco on 2007-01-13
Well I went ahead and tried what I had and recieved an "Error 23: Error while parsing number."

I somewhat understand the switcheroo.. but since my ubuntu and vista install are on completely different drives would it not be slightly different than what you have katalyst23?

---

### Post by logos34 on 2007-01-13
Vista is sdc1, right?  And the only other bootable partition is sda1 with linux, correct?  So in addition to linux at (hd0,0) you should have an entry in menu.lst for windows like this:
> title "Windows Vista"
root (hd2,0) 
map (hd0) (hd2)
map (hd2) (hd0)
makeactive
chainloader +1

Your /boot/grub/device.map should look like this:
> (hd0) /dev/sda
(hd2) /dev/sdc

Note: grub does not distinguish between sata and pata; it sees all drives as 'hd_'.  So, sda is 'hd0' and sdc is 'hd2'

---

### Post by FreakinSyco on 2007-01-13
Thanks logos.. but that didnt work. I now get a an error that the disk is not bootable.. which is the same error I get if I point GRUB to a non-existent hard drive. I'm thinking somethings not quite right. Any other ideas?

---

### Post by Tomosaur on 2007-01-13
Try just typing:
```

sudo update-grub

```
At the command line. This makes grub rescan your drives and add entries for the operating systems it finds. It may not find Vista, but then again it might, so it's worth a try.

---

### Post by FreakinSyco on 2007-01-13
Thats a very helpful command Tomosaur. But no it didnt find Vista. I just mounted the Vista disk to /media/disc

Gparted shows the following for the disk:

EDIT: Dont ask my why theres 1mb before the Vista partion.. I have no idea why Vista did that.

---

### Post by logos34 on 2007-01-13
Ok, so your vista disk is now sda...

Can you run fdisk -l again and post it if only for my sake?  I'm still not clear on your arrangement (and I just got done helping a new ubuntu user setup a dual boot on dual sata drives and grub wasn't all that tricky except for a tiny spacing error).  Also, post your fstab and the output from mount:
> sudo mount -a
> mount
> cat /etc/fstab

---

### Post by FreakinSyco on 2007-01-13
Well Feisty was being a pain with my graphics.. it was flipping out so I went ahead and reinstalled with Edgy. Still in the same situation. Thanks for your patience. Heres what ya asked for:

Output of "fdisk -l"
```

Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4669    37503711   83  Linux
/dev/hda2            4670        4870     1614532+   5  Extended
/dev/hda5            4670        4870     1614501   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9733    78180291    b  W95 FAT32

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3188    25600000    7  HPFS/NTFS

```

Output of cat /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=bccae8df-d7b7-4817-8b86-326db2042a84 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=2a82b456-447d-4802-9ea0-962d9237686e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

Output of mount (but not going be helpful as Ubuntu is no longer mounting the drive):
```

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

And what gparted currently shows:

/dev/hda = my drive Ubuntu is installed on
/dev/hdb = my media drive
/dev/sda = the drive Vista is installed on

And a screenshot of /dev/sda/

Once again thanks for the help. I feel were close!

EDIT:

my devices.mnt now automatically has the following:
```

(hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/sda

```

---

### Post by logos34 on 2007-01-13
Try this:
> sudo cp /etc/fstab /etc/fstab_backup

Then, 
> gksudo gedit /etc/fstab

Now add these lines to the end just after your cdroms:
> /dev/hdb1 /media/multimedia_files vfat iocharset=utf8,umask=000  0 0
/dev/sda1 /media/vista ntfs defaults,nls=utf8,umask=007,gid=46  0 0

(Replace 'multimedia_files' with whatever name you desire.)  
Save and close.

Now create mount points and mount the partitions:
> sudo mkdir /media/vista
sudo mkdir /media/multimedia_files
sudo mount /dev/sda1 /media/vista
sudo mount /dev/hdb1 /media/multimedia_files

Reboot.  They should automount.

Then we'll edit grub.

---

