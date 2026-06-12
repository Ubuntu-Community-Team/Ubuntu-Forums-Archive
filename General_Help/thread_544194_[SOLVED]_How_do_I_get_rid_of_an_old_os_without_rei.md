---
title: "[SOLVED] How do I get rid of an old o/s without reinstalling Ubuntu?"
date: 2007-09-06
forum: General Help
---

### Post by bobmac on 2007-09-06
Folks,

I installed Ubuntu on a machine with 2 disks. However, I forgot that there was already a Mandriva 2007 installation on the machine (tried it out and couldn't come to terms with it).

Now of course I've got two o/s on my machine and would like to get rid of the Mandriva. Is there any EASY way of removing the Mandriva o/s without having to reinstall Ubuntu?

If there is, please assume that I'm a complete novice when it comes to linux and Ubuntu

thanks,

Bob

---

### Post by bikeboy on 2007-09-06
Hi bobmac,

The simplest way I can think of is to install 'Gnome Partition Editor' in Ubuntu, then *carefully* delete the partition with Mandriva on it. Go to Application > Add/Remove > search for 'parted'. If you have any important information on either hard drive, it would be a good idea to make backup copies of it first.

---

### Post by bobmac on 2007-09-06
Sorry,

I should have mentioned. I installed Gnome Partition Editor but I can't figure out which partition the Mandriva o/s is on.

Bob

---

### Post by forestpixie on 2007-09-06
try running these 2 in terminal see if that sheds any light

sudo fdisk -l
df -h

---

### Post by bigboy_pdb on 2007-09-06
Also, check your fstab file (which is in "/etc") to find out which partitions are being used by Ubuntu.

---

### Post by bobmac on 2007-09-06
Folks,

I've run the command you suggested and this is what I got. I'm afraid that the info is pretty meaninless to me

calban@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/sda: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         381     3060351   83  Linux
/dev/sda2             985        2480    12016620    5  Extended
/dev/sda3   *         382         984     4843597+  83  Linux
/dev/sda5            1020        1528     4088511   82  Linux swap / Solaris
/dev/sda6            1529        2480     7646908+  83  Linux
/dev/sda7             985        1019      281074+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 20.4 GB, 20485785600 bytes
255 heads, 63 sectors/track, 2490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1019     8185086   83  Linux
/dev/sdb2            1020        2490    11815807+   5  Extended
/dev/sdb5            1020        1980     7719201   83  Linux
/dev/sdb6            1981        2490     4096543+  83  Linux
calban@ubuntu:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda3             4.6G  2.8G  1.7G  63% /
varrun                506M  228K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  120K  506M   1% /proc/bus/usb
udev                  506M  120K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
calban@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=8eedb558-11f3-4e5b-baa0-b29b6c037356 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda7
UUID=2c6ba4bc-29b2-4c17-aa13-37113c7d13f4 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
calban@ubuntu:~$

---

### Post by forestpixie on 2007-09-06
As both df -h and fstab give no reference to hdb - I assume that when you're in ubuntu you can't access mandriva,   - in which case mandriva must be on the second hd - 
/dev/sdb or /dev/hdb - 

I would wait for another opinion though :)

Also I was under the impression that gparted wouldn't let you do anything to a mounted drive

 - try ```
mount
``` in a terminal - if you get no reference to /sdb or /hdb that should be the drive with mandriva on

---

### Post by bigboy_pdb on 2007-09-06
Your "fstab" file indicates that Ubuntu is using the partition sda7 as swap space and the partition sda3 for its file system. Assuming that Ubuntu is the only system that you want installed, the information that "fdisk" printed indicates that you can delete the partitions for sda1, sda2, sda5, and sda6.

I forgot to mention this but you can also type "mount" to see which file systems are currently mounted. It might be a good idea to do this as well.

**EDIT:** I missed the hdb in there, but it looks like that would be deleted as well.

---

### Post by southernman on 2007-09-06
Please post your /boot/grub/menu.lst 

This will tell us if nothing else where Ubuntu is installed and should be able to figure out what to do from there.

@frostpixie... you are correct. Gparted can't do anything with a mounted partition. I prefer using SystemRescueCD (which has gparted on it) to do any thing with hdd's.

---

### Post by bigboy_pdb on 2007-09-06
Can't he simply unmount the partition granted that it's not being used? (I've only used fdisk **[EDIT]**along with mkfs**[/EDIT]** to delete/change partitions (to date) because I haven't needed to resize them)

---

### Post by vanadium on 2007-09-06
Briefly, there is no real easy way to remove Mandriva. You will need to delete the partitions concerned, then move and resize the partitions of your current system so that they make use of all available disk space. It is in fact some "system surgery" you need to do, not too difficult but no newbie stuff neither.

You can't obviously use gparted on mounted partitions. You must first unmount them. Even then, you obviously won be allowed to unmount the system partition. In order to be able to change all partitions, you need to run a live disk. You can use the ubuntu live disk, start gparted and unmount all volumes on the hard disks. The SystemrescueCD is another option and might be more suited (I do not know).

When deleting partitions, their GRUB references to the partitions will change. You probably will need to reinstall Grub in order to be able to boot your OSs correctly again. That is not a difficult task: I saw today in another post on this forum that it simply involves running grub-install.

The partition labels will also change (sda3 might become sda1). This probably won't be a problem with Feisty, because it uses UUID, and no device names, to refer the volumes (the advantage of UUIDS in action).

In your fstab, drives are referenced as hda instead of sda. This makes me suspect that your system was upgraded from Edgy. To make sure which volumes are referenced by which UUID, you can use the vol_id command. Those UUIDS that you see in your fstab are the ones that are mounted in the /etc/fstab of your current system, and you do not want to delete these, of course.

In fact, if you are not too experienced, you might be better backing up your user data and reinstalling the system all together.

---

### Post by rsambuca on 2007-09-06
> **vanadium said:**
> Briefly, there is no real easy way to remove Mandriva. You will need to delete the partitions concerned, then move and resize the partitions of your current system so that they make use of all available disk space. It is in fact some "system surgery" you need to do, not too difficult but no newbie stuff neither.

You can't obviously use gparted on mounted partitions. You must first unmount them. Even then, you obviously won be allowed to unmount the system partition. In order to be able to change all partitions, you need to run a live disk. You can use the ubuntu live disk, start gparted and unmount all volumes on the hard disks. The SystemrescueCD is another option and might be more suited (I do not know).

When deleting partitions, their GRUB references to the partitions will change. You probably will need to reinstall Grub in order to be able to boot your OSs correctly again. That is not a difficult task: I saw today in another post on this forum that it simply involves running grub-install.

The partition labels will also change (sda3 might become sda1). This probably won't be a problem with Feisty, because it uses UUID, and no device names, to refer the volumes (the advantage of UUIDS in action).

In your fstab, drives are referenced as hda instead of sda. This makes me suspect that your system was upgraded from Edgy. To make sure which volumes are referenced by which UUID, you can use the vol_id command. Those UUIDS that you see in your fstab are the ones that are mounted in the /etc/fstab of your current system, and you do not want to delete these, of course.

I[COLOR="Red"]n fact, if you are not too experienced, you might be better backing up your user data and reinstalling the system all together.[/COLOR]
I am sorry but I really disagree with this.  There is no reason to wipe everything and start over.  The mandriva installation can easily be reformatted from within ubuntu.  Simply install gparted (you can do this from the Synaptic Package Manager).  You can then reformat the partition as ext3, and then uses it for media storage, or whatever you wish.

---

### Post by bigboy_pdb on 2007-09-06
vanadium, it isn't obvious that gparted cannot be used on mounted partitions because it is possible that gparted (or parted) might unmount the partitions themselves. Only people who are used to using these programs are going to know that they have to unmount the volumes.

The question I asked was a polite way of addressing the fact that bobmac doesn't need to boot from a SystemRescueCD in order to delete the partitions and create new partitions using the old disk space. He could technically do all of this with "fdisk" and "mkfs".

Also, he only needs to make the changes that you mentioned if the partitions that get deleted have partitions between them and it bothers him that all of them cannot be made into one partition (or a series of back to back partitions). We should wait to see what additional information there is from him using the other commands that were suggested (such as "mount") before telling him how to proceed.

Using the command vol_id was a good additional suggestion.

---

### Post by bobmac on 2007-09-06
Folks,

Many thanks for all the info. The contents of my menu.lst file are:

calban@ubuntu:/boot/grub$ cat menu.lst
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
# kopt=root=UUID=8eedb558-11f3-4e5b-baa0-b29b6c037356 ro

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=8eedb558-11f3-4e5b-baa0-b29b6c037356 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=8eedb558-11f3-4e5b-baa0-b29b6c037356 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=8eedb558-11f3-4e5b-baa0-b29b6c037356 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=8eedb558-11f3-4e5b-baa0-b29b6c037356 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title           linux (on /dev/hda1)
root            (hd0,0)
kernel          /boot/vmlinuz root=/dev/hda1  resume=/dev/hda5 splash=silent 
initrd          /boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title           linux-nonfb (on /dev/hda1)
root            (hd0,0)
kernel          /boot/vmlinuz root=/dev/hda1  resume=/dev/hda5 
initrd          /boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title           failsafe (on /dev/hda1)
root            (hd0,0)
kernel          /boot/vmlinuz root=/dev/hda1  failsafe resume=/dev/hda5 
initrd          /boot/initrd.img
savedefault
boot

calban@ubuntu:/boot/grub$ 

I notice that there is some chat about how I would go about actually deleting the old stuff and  how to let Ubuntu know that there was now more disk space available.

Bob

---

### Post by bigboy_pdb on 2007-09-07
Can you please use the command "mount" and post the results of that as well?

---

### Post by bobmac on 2007-09-07
Folks,

This is what  mount returns:

calban@ubuntu:~$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
calban@ubuntu:~$ 


Bob

---

### Post by bigboy_pdb on 2007-09-07
Everything that you posted indicates that /dev/sda3 corresponds with your Ubuntu installation, meaning that you shouldn't modify/delete the partition /dev/sda3.

Could you please run "sudo vol_id /dev/sda7" just to verify that /dev/sda7 is your swap space? I'm pretty sure that it is, but I'd like to be certain. If one of the lines that is outputted to the screen reads "ID_FS_UUID=2c6ba4bc-29b2-4c17-aa13-37113c7d13f4" then that means that you shouldn't delete the partition /dev/sda7 either.

If you think that there are any files that you want to keep from the other partitions (or you want to check before deleting the partitions) then you can do the following:

**NOTE:** You don't need to bother reading the next 2 paragraphs if you only want what is from your Ubuntu installation.

**[Finding devices for partitions you want to keep]**
Click on "Places" and then "Computer" in the tool bar on the top of your desktop. There should be a list on the left entitled "Places" and in it you should see your other drives listed. Double click on each drive to view its contents (if one of them isn't mounted, you will be asked for your password and when it is entered correctly you can mount them without being asked again). Back up anything that you want from the partitions that you want to delete. If there are any partitions that you want to keep (excluding your Ubuntu installation which will be labelled "File System") then do the following.

For each drive that you don't want the contents of or that you have backed up, right click on the drive and select "unmount". Once you're done doing this, some of the drives (other than "File System") should still be mounted (meaning that you want to keep those partitions). Open a terminal and type "mount". For the leftmost set of characters some of them will be something like "/dev/sda1" (where the 1 could be another number). All of these are the additional partitions that you want to keep. You will also see "/dev/sda3" on the list because that's your Ubuntu root partition (but we already knew that partition shouldn't be modified/deleted from what I said at the beginning of this post).
**[/Finding devices for partitions you want to keep]**

Once you're done all this you can use gparted to delete your old partitions and create new ones. 

I installed gparted to try it and I found that it had a very user friendly interface. I had an issue with trying to delete a partition and create it again while Ubuntu was running (something tried to mount it before the file system was made), meaning you might have to restart your computer with the SystemrescueCD in the tray. I'm sure that most of the other people in this thread have far more experience with using gparted so perhaps one of them can walk you through it (I can learn to do it if need be but I'd rather someone else help you with that to be on the safe side).

---

### Post by forestpixie on 2007-09-07
Hi - I personally found it a whole lot easier to burn a live gparted - then boot from it - nothing gets mounted so you can deal with partitions as you need to. 

BUT you really need to know which partitions you're going to be dealing with.

I would agree mostly with the partition talk but being quite new myself can't see the difference between sda7 and sda5 - perhaps someone would point it out to me.

I think I'd be safe in saying that sdb is the drive with the other linux on.

I had to do a similar option - only I was finally getting rid of my win stuff - and found it much easier to deal with it booting gparted and reformatting in there.

Once that was accomplished - sorted out mounting the new clean drive and bob was my uncle :)

---

### Post by bigboy_pdb on 2007-09-07
forestpixie, the swap partition is used for writing data from RAM to avoid having the RAM completely filled with data.

What vanadium had said about the devices being changed from things like "hda7" to "sda7" due to an upgrade from Ubuntu Edgy (6) to Fiesty (7), is true. From what I've seen it looks as though the devices are changed from from "hdaN" to "sdaN" (where N is the partition's number). That might not always be the case because the numbering might change because a person already has other sda devices present or for other reasons (that's why I was waiting for more information such as the "mount" command). When I looked at the "fstab" file, the comments (lines preceded by the # character) indicated that hda7 was the partition for the swap file in Ubuntu Edgy Eft so I was guessing that sda7 should be the corresponding partition in Fiesty Fawn. The "vol_id" will give us the UUID of sda7 and that will tell us if it is or isn't the swap file that Ubuntu is using (based on the entry in the "fstab" file). If you look at your "fstab" file and run the "vol_id" command, you'll better understand what I'm talking about.

A more general response would be:
Both sda5 and sda7 are swap partitions, but from all the information that we've been given it would appear that he's currently using sda7 as his swap partition (and "vol_id" will either confirm or refute this). Granted that sda7 and sda3 are right beside each other (you can tell this from the information about the starting and ending blocks in the "fstab" file) it would be a good idea to continue using sda7 as the swap partition so that we don't cause more gaps between the partitions.

---

### Post by vanadium on 2007-09-07
rsambuca, I certainly agree with you that a simple solution is to just reformat the mandriva partition and use that as an extra volume for data. The Mandriva swap partition would then remain unused, but that is only perhaps two megabyte anyway (could also be made into a very small additional storage space). 

What I suggested, deleting partitions and rearranging the remaining partitions, is more complicated. For people not yet very used to partitioning, reinstalling might be easier and safer to obtain the same effect. Anyway, I find the current partition scheme strange and confusing.

The only partitions that currently are used by Ubuntu are

/dev/sda3 is the root (including /home and the user data)
either sda5 or sda7 as  swap (I would need to see /etc/fstab/ )

You have two drives in your system. The other drive is not at all used. Indeed, in df -h, only your sda3 is listed. indeed, there is a lot of space to reclaim!

The more simple solution would thus be to leave all partitions in place, format the ones not in use to ext3, then have these mounted automatically in /etc/fstab.

The more complicated solution is to delete partitions and move and resize the others. This would yield less, but larger partitions.

---

### Post by forestpixie on 2007-09-07
> myself can't see the difference between sda7 and sda5

big_boy - I was having trouble with which swap was which - not what it accomplishes, thanks though :) 

> either sda5 or sda7 as swap (I would need to see /etc/fstab/ )

vanadium - the fstab does indeed show sda7 as swap - missed that one

All that aside I would be thinking about repartioning both drives and just reinstalling - I dare say in a couple of months the OP's likely to be thinking about gutsy. A separate /home might be worth thinking about now

---

### Post by bigboy_pdb on 2007-09-07
> **forestpixie said:**
> 
big_boy - I was having trouble with which swap was which - not what it accomplishes, thanks though :)


Sorry, I wasn't trying to imply that you didn't know what swap partitions were for. I figured that you already knew. I wrote that additional information because some people who are reading (or will read) this thread won't understand and I'm trying to give them a better understanding.

bobmac, I forgot to mention that your whole second hard drive "sdb" can be reformatted as well, but you should check those partitions as well to see if you want to keep anything from the hard drive (technically the method that I mentioned before should show you those partitions but you might be confused as to why they start with "sdb" instead of "sda").

vanadium, I somewhat agree that reinstalling might be better. It's dependent on what sort of effort bobmac has put into getting Ubuntu running and set up. Also, if he can use gparted without any problems from within Ubuntu I'd say that it shouldn't be too much work to delete/change those partitions provided that he doesn't mind that there may be 3 or more partitions for additional files, but if using gparted involves creating and using a bootable CD then I think that it might just be better to reinstall Ubuntu because he can reinstall it and use all of the first hard drive for his installation.

What would you like to do bobmac? If you want to learn gparted and have some time to tinker with partitions then it might be beneficial to go through all of this. If time is a problem then re-installing the system might be better. Either way you'll be receiving help so it's up to you.

Sorry if it my posts appear as though I'm talking through people. It should be easier to read my posts if I address one person at a time. Basically, most of what I'm writing is addressed to everyone.

---

### Post by bigboy_pdb on 2007-09-07
> **vanadium said:**
> 
I would need to see /etc/fstab/


It's hard to see but it's at the bottom of the post with the results for "fdisk -l" on the first page.

> **bobmac said:**
> 
I notice that there is some chat about how I would go about actually deleting the old stuff and  how to let Ubuntu know that there was now more disk space available.


Regarding what program you should use if you decide not to reinstall, I think that everyone who has posted would agree that you should use gparted. The debate is more about whether or not you should reinstall everything (which as I mentioned in my last post is up to you).

> **bobmac said:**
> 
I've run the command you suggested and this is what I got. I'm afraid that the info is pretty meaninless to me


Sorry that a lot of this wasn't explained.

**NOTE:** This last part is about explaining some things in Linux. Anyone who's already aware of how Linux works or doesn't have the time to read it might want to skip it.

In Linux can refer to different partitions by using devices. Your devices are in the folder "/dev". Devices allow you to interact with different hardware devices (i.e. hard drives, tablets, printers, your mouse, joysticks, and so forth). Windows uses drive letters to represent different partitions, but in Linux you can attach a drive to any folder (and this is referred to as mounting the device). For example, if you wanted to play a practical joke on a family member, (as root) you could mount an empty partition over his/her home directory.

Hard drives can be separated into partitions. This allows you to do things such as installing more than one type of operating system or files system on one hard drive. It can also keep problems in one section of your hard drive from affecting other sections. For example, if for some reason a program continuously makes temporary files in the "/tmp" folder and that folder has its own partition then your whole hard drive won't become filled with files (and your system won't crash).

For information on partitions (primary, extended, and logical) you can read the following:
[http://www.faqs.org/docs/linux_admin/x1139.html](http://www.faqs.org/docs/linux_admin/x1139.html)
[http://tldp.org/HOWTO/Partition/partition-types.html](http://tldp.org/HOWTO/Partition/partition-types.html)

The command "fdisk -l" prints information about hard drives regardless of whether or not they've been mounted (and typing "sudo" in front indicates that you want to use the program as the root user). The first entry in the line is the device (partition) that is being referred to. If there is a star following it then the partition is a primary (bootable) partition. The next two entries are the cylinders that the partition starts on and ends on (respectively), and the number following that is total number of blocks within the partition. The last number indicates what type of *generic* file system is being used on the partition. For example, Windows uses "HPFS/NTFS", Linux uses "Linux", and Linux swap space uses "Linux swap / Solaris".

To understand what a cylinder is look at the diagram on this page (and you could read it):
[http://www.storagereview.com/guide2000/ref/hdd/geom/tracksDifference.html](http://www.storagereview.com/guide2000/ref/hdd/geom/tracksDifference.html)

The command "mount" prints the devices that have been mounted, their mount points, the type of file system being used, and some addition information (such as who can access the device). For example, the line "/dev/sda3 on / type ext3 (rw,errors=remount-ro)" from when you typed mount tells me that the device /dev/sda3 is your root partition because it is mounted to "/" and the file system is ext3 which is the 3rd Linux journaling file system. If you type "mount" before and after putting CD-ROMs in the drive or plugging in USB devices and turning them on you'll see other additional entries. For example, when I use the mound command, the following information: "/dev/sdc1 on /media/USB-HDD type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)" indicates that the device /dev/sdc1 (which is my USB hard drive) has been mounted to /media/USB-HDD (meaning if I go to that folder I'll be able to see what's on it) and it has a VFAT file system.

The file "/etc/fstab" contains information on file systems on your computer. It is used at boot time to see what partitions should be mounted, where they should be mounted to, and the order in which they should be scanned. The first entry on a line is the device or UUID for a file system. UUIDs are unique sequences of characters that are supposed to be used to identify a partition. You can use "vol_id *device*" to see a partition's UUID (for example, "vol_id /dev/sda3" will show you the UUID of your root partition). The second entry is the mount point (the folder where you can find the files on the hard drive). The third entry is the type of file system that the partition is using. The fourth is a list of options (such as who can access the drive and whether or not the drive should be mounted when Linux is starting up). The fifth has to do with whether or not a file system should be dumped (this has to do with backing up file systems). The sixth is to determine which file systems should be scanned and in what order (a 1 means the file system is bootable, a 2 means it is not bootable but should be scanned, and 0 means that it shouldn't be scanned).

That's a lot of information, but I'll try to give a brief description of how these things can be used to find out about your file system.

When you typed "mount" we were able to see which partitions you've been using while you're using Linux. I told you to mount the other drives to check their contents since they weren't mounted at the time. We checked your "fstab" file to see which file systems were being mounted when Ubuntu starts up. We used "fdisk -l" to see what partitions exist on your hard drive other than the ones that are mounted.

---

### Post by vanadium on 2007-09-08
This is getting pretty long, although we learned a lot in the mean time. Now it is time for action: I think we pretty much have all information. Summarizing, there are three options, from easy to more complex (never really difficult though ;) ):

1) just mount all existing partitions in the current Ubuntu install so that all drive space is available

2) reinstall altogether, wiping the entire disk

3) Repartition the drive, keeping the existing Ubuntu installation

Bobmac, it is your call now, If you decide on one of the strategies, we now have all the people and all the information to give you step by step instructions. (1 will be easy, 2 is standard, 3 will be a bit more tricky and require this thread to grow a bit more).

---

### Post by bobmac on 2007-09-09
Folks,

I'm grateful for all the assistance and information. I've learned an amazing amount in such a short time.

Since I'm such a novice and a bit chicken (cluck, cluck), I'd be grateful if you could guide me through option 1.

If you don't have the time or have got fed up with my stupid questions and ideas then not to worry I'm still grateful for all your hard effort at trying to help an old codger like me.

Many thanks again,

Bob

---

### Post by vanadium on 2007-09-09
I think that is a wise decision. Indeed, you still could reinstall freshly a bit later this year with thenext ubuntu release if you wanted. I am doing some homework now, be back in a minute ...

---

### Post by vanadium on 2007-09-09
To mount your partitions requires two things: 1) you need to create a "mount point". This is nothing else than an empty directory where your new partition will be mounted 2) you need to mount the partition, i.e. connecting the partition to the mount point. This can be done once using the mount command, but can also be done automatically by including the mount commands in /etc/fstab, which is what we will do. I will show you how to add /dev/sdb1, and I hope you will be able by this example how to proceed for the other partitions.

Part 1: creating the mount point.

I prefer mounting partitions of internal, non-removable drives under the traditional /mnt directory instead of under /media. Thus, I create a mount point under /mnt. If you do this under /media instead, ubuntu will automatically display icons to the volumes on the desktop (if you like that, choose /media instead of /mnt).

sudo mkdir /mnt/sdb1

(use a more descriptive directory name rather than sdb1 if you want to)

Part 2: mounting the partition in /etc/fstab

Load your /etc/fstab in an editor with root privileges (make a backup copy of /etc/fstab first):

gksudo gedit /etc/fstab &

(note: I added the appersand, so the process starts in the background and your prompt is free again). 

First obtain specific information on your partition:

sudo vol_id /dev/sdb1

ID_FS_TYPE tells the file system type, using the tag we need to include in /etc/fstab. If there is an UUID (ID_FS_UUID), we will use that to mount. If there isn't, we use the device name. (UUIDS do not change when the partition of the drive changes and therefore are more persistent)

In /etc/fstab, add first a comment, then add the actual line. The result will look like:

# Entry for /dev/sdb1 :
UUID=113d4806-2eb3-492a-bf81-de560d9ed70d /mnt/sdb1 ext3 defaults 0 2

If there is no UUID (older Linux partitions), you could make one yourself, but for the sake of simplicity, we will just mount such drives the old way, i.e. referring by device name instead of by UUID. Then, it would look like:

/dev/sdb1 /mnt/sdb1 ext3 defaults 0 2

The first item is what you are mounting, referred to either by UUID (recommended nowadays) or by device name.

The second item is the mount point, i.e. where to mount.

The third item is the file system. You can learn the correct tag from the vol_id command.

The fourth one are the options. Here, I just specified "defaults" for the default options. For fat or ntfs volumes, look up appropriate options elsewhere.

The fifth is whether the fs needs to be dumped. Don ask me what that means! 0 means it does not need to be dumped.

The sixth tells about the need to check. For your root file system, this is always set to 1. Other drives have order 2, thus we put two. Some file systems that cannot be checked would have a 0 here. Indeed, you can disable checking by specifying 0. Not recommended indeed.

That is all: one line for one partition. Save the file (but do not exit if you want to continue mounting other partitions).

Now reload /etc/fstab (in ms windows, you would need to reboot, not so in Linux):

sudo mount -a

There should be no output! If there is output, it indicates an error in the lines you added (this supposes your /etc/fstab was error free to start with!)! If there is no error, congratulations: you mounted your partition and you can see it navigating to /mnt/sdb1.

You can't write to it as a regular user, though, because you do not have the permissions. This leads us to an unexpected part 3: setting permissions for you to write as a user.

Part 3: setting permissions.

Here my advice will differ slightly from advice commonly found on this. It is my opinion that mount points of fixed drives belong to the root. Thus, I do not recommend the approach of giving the mount point to the user, although you can (and it makes sense for a system where you are the sole user). My recommendation is instead to give directories on the fixed drive to users. This allows for a great deal of flexibility in organizing use of the drive by different users.

The approach is: (1) create a directory, (2) give it to a user. For convenient access to the storage room, (3) link to it from the user's home directory. Three steps, three commands:

sudo mkdir /mnt/sdb1/userdirectory
sudo chown $USER:$USER /mnt/sdb1/userdirectory
ln -s /mnt/sdb1/userdirectory /home/$USER/userdirectory

If the user is yourself, feel free to type $USER: this is expanded to your login. If it is for another user, you will need to replace $USER by the login of that user.

userdirectory is just a name for the example: you should choose a name that is convenient to you.

Appendix: in your particular case, you will need to free space to remove the remnants of your previous Mandriva install. It is perhaps most convenient to go to the new partition with a nautilus with root privileges (gksudo nautilus), inspect what's there and delete what you do not need.

---

### Post by bigboy_pdb on 2007-10-17
bobmac, with Ubuntu 7.10 being released tomorrow, now might be a good time to consider backing up your data and deleting the partitions we were talking about or performing a fresh installation of Ubuntu over everything.

If you need help with any of this then you can make a post about it.

---

