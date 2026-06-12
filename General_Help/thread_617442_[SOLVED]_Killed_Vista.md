---
title: "[SOLVED] Killed Vista?"
date: 2007-11-19
forum: General Help
---

### Post by squirage on 2007-11-19
Hi All,

  Me again.

  Fixed the grub error17, recovered the unreadable partition, and all was right with the world.

  Then I went to reboot into windows to look at some email info that I hadn't migrated and Doh!

  It ran check disk and said something about bad sectors and hung in stage 2 of 3 of something. I powered down and restarted and it started running some repair utility which I did not have time to finish before I had to head for the airport.

  Now it runs the little windows green bar splash screen but hangs on a black screen and the hd stops spinning.

cat /boot/grub/menu.lst:
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

# kopt=root=UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f ro



## Setup crashdump menu entries

## e.g. crashdump=1

# crashdump=0



## default grub root device

## e.g. groot=(hd0,0)

# groot=(hd1,2)



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

# howmany=2



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



title           Ubuntu 7.10, kernel 2.6.22-14-generic

root            (hd1,2)

kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f ro quiet splash

initrd          /boot/initrd.img-2.6.22-14-generic

quiet



title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)

root            (hd1,2)

kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f ro single

initrd          /boot/initrd.img-2.6.22-14-generic



title           Ubuntu 7.10, kernel 2.6.20-16-generic

root            (hd1,2)

kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f ro quiet splash

initrd          /boot/initrd.img-2.6.20-16-generic

quiet



title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)

root            (hd1,2)

kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f ro single

initrd          /boot/initrd.img-2.6.20-16-generic



title           Ubuntu 7.10, kernel 2.6.17-12-generic

root            (hd1,2)

kernel          /boot/vmlinuz-2.6.17-12-generic root=UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f ro quiet splash

initrd          /boot/initrd.img-2.6.17-12-generic

quiet



title           Ubuntu 7.10, kernel 2.6.17-12-generic (recovery mode)

root            (hd1,2)

kernel          /boot/vmlinuz-2.6.17-12-generic root=UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f ro single

initrd          /boot/initrd.img-2.6.17-12-generic



title           Ubuntu 7.10, kernel 2.6.17-10-generic

root            (hd1,2)

kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f ro quiet splash

initrd          /boot/initrd.img-2.6.17-10-generic

quiet



title           Ubuntu 7.10, kernel 2.6.17-10-generic (recovery mode)

root            (hd1,2)

kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=91c2e4ef-d905-4be7-938c-fcbcb4b7669f ro single

initrd          /boot/initrd.img-2.6.17-10-generic



title           Ubuntu 7.10, memtest86+

root            (hd1,2)

kernel          /boot/memtest86+.bin

quiet



### END DEBIAN AUTOMAGIC KERNELS LIST



# This is a divider, added to separate the menu items below from the Debian

# ones.

title           Other operating systems:

root





# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda2

title           Windows Vista/Longhorn (loader)

root            (hd0,1)

savedefault

makeactive

chainloader     +1

```

sudo fdisk -l :

```
 Disk /dev/sda: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x6bba44a8



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1               1         192     1536000   27  Unknown

Partition 1 does not end on cylinder boundary.

/dev/sda2   *         192        9730    76613632    7  HPFS/NTFS



Disk /dev/sdb: 100.0 GB, 100030242816 bytes

255 heads, 63 sectors/track, 12161 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x5d379805



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1               1        5225    41967765    f  W95 Ext'd (LBA)

/dev/sdb2   *        5226        5510     2289220   82  Linux swap / Solaris

/dev/sdb3            5511       12161    53424156   83  Linux

/dev/sdb5               1        5225    41962884+   7  HPFS/NTFS
```

Looking in the file browser the windows partitions are there, but don't have any files. In Disk manager they are there and the correct sizes but don't say that anything is being used. In GParted they are there and the right sizes but they have the ! warning and don't show any data. It also says they are not mounted.

I've seen EasyBCD, but it would not load into Wine for me. I originally recovered sbd5 with systemrescuecd. I'm not sure what the best tack is to take.

Here is the thread that shows the procedure I used for fixing grub [http://ubuntuforums.org/showthread.php?t=614074](http://ubuntuforums.org/showthread.php?t=614074)

Any direction is appreciated, I'm off to start backing up what I have before I lose everything.

---

### Post by malfist on 2007-11-19
Stopping the recovery before it finished might have caused a problem. I can't help much, but I'd get the norton suite, I think it has some stuff to recover partitions and recover files from windows.

---

### Post by Computer Guru on 2007-11-19
EasyBCD does not run in Wine - it runs in Windows only.
 
These links should be of use:
1) How to recover Vista's bootloader: [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)
2) How to dual-boot Vista and Ubuntu: 
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
 
Hope it helps.

---

### Post by squirage on 2007-11-19
Hi malfist and Computer guru,

  Thanks. I scanned one of the windows partitions with Data RescuePC and it seemed to find everything on that partition. Only problem now is that I don't have a fat partition of any size available right now and the software did not seem to see my 250GB USB drive. So I'm not even sure if creating a fat partition on that will help.

  Thanks for the link to the vista repair iso. that seems like the option to go with. I think that it tried to do that from the Toshiba partition. The did not give me a vista disk. I do have a recovery disk somewhere.

Thanks again. I'll post when I have results.

---

### Post by squirage on 2007-11-21
Hi All,

  Nothing thus far has worked for me. The Vista bootloader recovery looked promising but it hangs on the blue wallpaper.

  I have downloaded images of tons of Data recovery, cloning, you name it. Nothing has worked thus far. As I may or may not have mentioned earlier for some reason Knoppix stuff won't run for me, I haven't figured out why. 

  I can see everything running test disk in system rescue cd, but it says the boot record is okay and matches the backup and all the partitions are green after analysis.

  Thus far the only thing that seems to even see my files and offer the chance of recovery is Data Rescue PC. The only rub is  that my version, 1.6, doesn't seem to see my external HD's. Of course the new version 2.0, does but I can't recover with the demo so it's $99 dollars. 

  I suppose I should be happy that something can see my files. Does anyone here have any better idea for a program to use? I can send you the website if you like. I don't know that I want to advertise for them at this juncture.

Any thoughts are appreciated.

---

### Post by squirage on 2007-11-29
Hi Again,

  Well, I recovered my data using a software that cost me $99, but it worked. I attempted to re-install Gutsy from the Live CD but balked for some reason at the partition setup. I suppose I could just select the current gutsy partition since that doesn't work anyway, but I can't seem to get at the windows stuff. I can't boot in windows and all of the recovery disks hang.

  I called toshiba and they want me to send the computer in. I wonder what happened and if I am stuck with one of those Vista only phoenix bioses I read about?

  Any way I 'm not real jazzed about the idea of sending my computer in, and I was wondering if using Gparted to reformat might be the way to go and start from scratch. I don't know if that will do the trick?

  My install of gutsy works like crap so I wanted to do a clean install anyway, I have an XP Pro disc lying around somewhere and I don't really care for Vista anyway if I can't get it back. 

  I'm trying to figure out what I did to be so cursed with bad luck this year, especially on computers.

  I guess I'll try the system rescuecd one more time and write the partition info to see what happens. Like I said at this point this computer is a glorified word processor at this point and I'm ready to rip it open.

For what it's worth, thanks to the community for all past and future support. That is the one thing that has been cool, people helping each other out.

---

### Post by squirage on 2007-12-07
Hi All,

  Just an update. Somehow when I tried to fix my Grub error 17, I trashed my vista MBR and could not boot into windows. Not a problem except for the fact that I had some data I needed that could not be accessed. I could not fix the problem with the supergrub disc and I could not use the recovery discs to fix it either. Everything vista would hang. Eventually in trying different things I got grub error 22 and could not boot into anything.

  So I used the gparted live cd to reformat my drives and restore the factory partition setup and then ran the recovery discs. By the way Toshiba wanted me to send my laptop in when I called them and the recovery discs wouldn't work. I'm really tired of people on support lines not being able to tell me simple things to fix the things I need.

  So this is sort of solved. I just had to wipe everything. And before I forget I was able to recover my data after paying $99 for a newer version of a software I already owned. Yea!

  Lastly, thanks to computer guru for the suggestion of EasyBCD. I have not installed an extra OS yet but I was thinking about it soon. The only problem is I ran clamwin and it returned back that the exe file and the uninstall file were adware. Hmm.

---

