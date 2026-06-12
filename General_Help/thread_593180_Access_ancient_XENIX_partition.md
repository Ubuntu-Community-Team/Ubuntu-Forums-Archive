---
title: "Access ancient XENIX partition"
date: 2007-10-26
forum: General Help
---

### Post by jimburt372 on 2007-10-26
I am a relative noob to ubuntu and linux in general, but I am trying to help some friends of my  parents rebuild an ancient system that runs XENIX.  

What I am thinking of trying is setting up a much newer machine than their 1987 286 system, and installing ubuntu for them.  The problem is that I need to access their information on their old XENIX System V drive.    

Does anyone know if this will work, or is the XENIX partition some retired format that I won't be able to access?  If it is accessible, will ubuntu just pop it up like it does my NTFS partition?

This computer runs the inventory for a small town parts store.  The owners are just a few years from retiring and they don't want to spend the major money that if they can help it.

Thanks in advance for your help.

JB3

---

### Post by Madstone on 2007-10-26
I doubt ubuntu or any other distro will recognize it without some tweaking but have a look here

[http://aplawrence.com/SCOFAQ/FAQ_scotec1linuxfs.html](http://aplawrence.com/SCOFAQ/FAQ_scotec1linuxfs.html)

Hope that helped a little

---

### Post by Old *ix Geek on 2007-10-26
Is it SCO Xenix by any chance?  That's what I was using in the mid-'80s, and I actually still have my manuals around here...somewhere.  Anyway...

According to **man mount**:
```
    -t vfstype
              The argument following the -t is used to indicate the file system type.  The file system types which are currently supported include: adfs,
              affs,  autofs,  coda,  coherent, cramfs, devpts, efs, ext, ext2, ext3, hfs, hpfs, iso9660, jfs, minix, msdos, ncpfs, nfs, nfs4, ntfs, proc,
              qnx4, ramfs, reiserfs, romfs, smbfs, sysv, tmpfs, udf, ufs, umsdos, usbfs, vfat, xenix, xfs, xiafs.  Note that coherent, sysv and xenix are
              equivalent  and  that  xenix  and  coherent will be removed at some point in the future — use sysv instead. Since kernel version 2.1.21 the
              types ext and xiafs do not exist anymore. Earlier, usbfs was known as usbdevfs.
```

So it looks like you should be able to use **xenix** or **sysv** with **mount -t** and see the Xenix disk.

PS  If you try this and it works, let me know!  I have an old hard drive from circa 1991 with Coherent on it.  It would be fun to see what that old sucker looks like!

---

### Post by jimburt372 on 2007-10-26
Thanks for the info.  I have just finished installing xubuntu on this P3 500mhz system, and I am creating a GHOST image of the original XENIX drive before I try and mess with it.  I will get on with trying to access it tomorrow.  

Thanks again for the info.  I will let you know how it goes.

JB3

---

### Post by dcstar on 2007-10-27
> **jimburt372 said:**
> I am a relative noob to ubuntu and linux in general, but I am trying to help some friends of my  parents rebuild an ancient system that runs XENIX.  

What I am thinking of trying is setting up a much newer machine than their 1987 286 system, and installing ubuntu for them.  The problem is that I need to access their information on their old XENIX System V drive.    

Does anyone know if this will work, or is the XENIX partition some retired format that I won't be able to access?  If it is accessible, will ubuntu just pop it up like it does my NTFS partition?

This computer runs the inventory for a small town parts store.  The owners are just a few years from retiring and they don't want to spend the major money that if they can help it.

Thanks in advance for your help.

JB3

I think that I have seen the XENIX FS option in the kernel compilation options, but I doubt if it is enabled by default in the "standard kernel.

It may be a solution to simply (!) compile your own version of the current Ubuntu kernel with this option enabled (there are HOWTOs on this in the forums).

---

### Post by jimburt372 on 2007-10-28
Ok, so I must be more of a noob then I wanted to admit up front, cause I am not having any luck with the mount command.

It could be that I just don't know how to determine what device name I should be using, which by the way, how do I determine this?  I have read through the MAN MOUNT listing several times, and I am still not getting it.

I tried 'sudo mount -t sysv /dev/hda2' and 'sudo mount -t sysv /dev/sda2' and both of these gave me the same help listing, and referred me to 'man 8 mount'

That, for all I could tell was the same as 'man mount' so it didn't gain me anything.

I am lost, again. :-)  Any advice is greatly appreciated.

---

### Post by dcstar on 2007-10-28
> **jimburt372 said:**
> Ok, so I must be more of a noob then I wanted to admit up front, cause I am not having any luck with the mount command.

It could be that I just don't know how to determine what device name I should be using, which by the way, how do I determine this?  I have read through the MAN MOUNT listing several times, and I am still not getting it.

I tried 'sudo mount -t sysv /dev/hda2' and 'sudo mount -t sysv /dev/sda2' and both of these gave me the same help listing, and referred me to 'man 8 mount'

That, for all I could tell was the same as 'man mount' so it didn't gain me anything.

I am lost, again. :-)  Any advice is greatly appreciated.

Look in your /etc/fstab file for an idea of how things are mounted - the existing entries on your own system should give you an idea of what you need to do (like specifying an existing mount point....)

---

### Post by jimburt372 on 2007-10-29
here is the contents of the /etc/fstab file:

    ======================================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0554f6bb-1c3a-4b86-b2d9-c1b7702788eb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d49735a1-9a4b-403f-ae20-bbe3f583468a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

    ======================================

One other thing that I just noticed, and it seems to be a fairly large issue:  When I run GParted to try and see how the system addresses, or recognizes the drive (don't know the proper linux terminology for this), anyway, there is only one device available to be selected in GParted.  The bios recognizes the drive, and I have set the cylinders, head and sectors manually, so that it would be properly addressed by the bios.

I'm guessing that this means that I have a bigger problem than just not having the syntax down for the mount command.  

Sorry that I didn't notice this sooner and point it out, but I still live mostly in the M$ world, and I am just trying to get myself out of Windows, and into a more open world, but I am VERY 'green' in this vast new world (new to me that is).

On a Windows box, I would have immediately looked at the device mgr and made sure that the drive was 'acknowledged' although there wouldn't have been any partitions available because of the filesystem, but that is where I am right now.  

I am installing Ubuntu on my main troubleshooting computer right now, that is the computer that I used to GHOST the drive and was able to at least access it in a very basic scope a few days ago.

I know that lack of experience and/or knowledge is currently my biggest hurdle in the wide world of Linux, and I thank you all for helping me learn to walk, or at least take a step or two.  :-)

---

### Post by seuaniu on 2007-10-29
You haven't told the mount command where to mount the drive.  Since your new, I'll explain a little.  *nix (that means any unix like system) keeps all drives mounted in one big filesystem, and you can mount a drive anywhere you like.  No C: or D: drives, they all go into the same tree, starting at / .  A good place to put a temporary drive is in the /mnt directory:

```
sudo mkdir /mnt/xenix

sudo mount -t sysv /dev/hda2 /mnt/xenix
```

That ought to do the trick.  Good thinking creating a drive image before tinkering, I'm amazed that a drive has lasted that long.

---

### Post by jimburt372 on 2007-10-29
> **seuaniu said:**
> You haven't told the mount command where to mount the drive.  Since your new, I'll explain a little.  *nix (that means any unix like system) keeps all drives mounted in one big filesystem, and you can mount a drive anywhere you like.  No C: or D: drives, they all go into the same tree, starting at / .  A good place to put a temporary drive is in the /mnt directory:

```
sudo mkdir /mnt/xenix

sudo mount -t sysv /dev/hda2 /mnt/xenix
```

That ought to do the trick.  Good thinking creating a drive image before tinkering, I'm amazed that a drive has lasted that long.

===================================

Thanks for the info.

I am amazed too that the system was still running.  The only 'real' problem with it is that the monochrome monitor is going crazy, and once the system goes into its 'text-graphics mode' or whatever you want to call the screen that is not strictly a command line, then everything shifts in such a way that what should be in the center of the screen is off at the edge of the screen, and there seems to be about a 1 inch gap between what goes off the right edge, and what begins wrapping to the left edge of the screen.

They haven't even changed out the power supply or anything.  When I was first called and told that this computer was 23 years old and that is needed some help, I assumed that they had overestimated the age, but there are several dates on the system components and the newest that I have seen was july 1983.  My jaw hit the desk.

When I followed your instructions, here is what I got after the last command:

jimmy@jimmy-desktop:/$ sudo mkdir /mnt/xenix
[sudo] password for jimmy:
jimmy@jimmy-desktop:/$ sudo mount -t sysv /dev/hda2 /mnt/xenix
mount: special device /dev/hda2 does not exist
jimmy@jimmy-desktop:/$ 

Is there some command I can type, or program I can run to determine what device description I should use (i.e. /dev/hda2)?

By the way, I have switched back to my main system, and now when I go to the Ubuntu Device Manager, now the 'Conner Peripherals 40MB CP3000' is listed, so it appears that Ubuntu recognizes that the device is in the system.  However, I don't see any designation even close to the /dev/xxxx that might help me figure out how to address the device.

Thanks again.  I don't want to be a leech that is only saying "help" but for the time being that is about all I am equipped to say.

I REALLY appreciate everyone for helping me.

---

### Post by digitalbenji on 2007-10-29
dmesg will print the kernel log, which likely has some useful information as to what device it is on.

---

### Post by heldal on 2007-10-29
First list the partitions on the drive:

sudo fdisk -l /dev/hda

Then use the specific hdaX partition you find in the mount command

Btw if you're afraid of doing anything wrong you might consider the read-only option to mount

ex: sudo mount -t xenix -o ro /dev/hda1 /mnt/xenix

(or mabe  "-t sysv")

---

### Post by jimburt372 on 2007-10-29
> **heldal said:**
> First list the partitions on the drive:

sudo fdisk -l /dev/hda

Then use the specific hdaX partition you find in the mount command

Btw if you're afraid of doing anything wrong you might consider the read-only option to mount

ex: sudo mount -t xenix -o ro /dev/hda1 /mnt/xenix

(or mabe  "-t sysv")

================================

jimmy@jimmy-desktop:/$ sudo fdisk -l /dev/hda
[sudo] password for jimmy:

Disk /dev/hda: 43 MB, 43130880 bytes
5 heads, 17 sectors/track, 991 cylinders
Units = cylinders of 85 * 512 = 43520 bytes
Disk identifier: 0xae57ae57

   Device Boot      Start         End      Blocks   Id  System
/dev/hda4   *           1         976       41471+   2  XENIX root

jimmy@jimmy-desktop:/$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)

jimmy@jimmy-desktop:/$ sudo mount -t sysv /dev/hda4 /mnt/xenix
mount: special device /dev/hda4 does not exist

jimmy@jimmy-desktop:/$ 


I hope that this makes sense to someone, because I am still mostly lost, but at least I did make a little sense of the returned information about the XENIX drive, I think.

I will be away from this computer for several hours, but I will check for more advice and get back to this later this evening.

Thanks again.

---

### Post by heldal on 2007-10-29
What exactly do you want to achieve from your "re-build"? I suspect you might have quite a bit of work ahead if you aim to rebuild full functionality on a modern system. Such old boxes were usually running some custom application which may be anything but trivial to port to linux (or any other current system). I did my share of development and administration of xenix boxes back in the 80s and my experience wrt porting is that it involves export of all data to flat-files and re-design/re-build everything with current tools and applications. The exception may be old oracle databases for which there are tools to convert dumps even of ancient 80s systems into something that can be imported into a current version, but even there you'll have to reconstruct all other application logic.

---

### Post by digitalbenji on 2007-10-29
Is the Xenix hard drive in the Ubuntu computer?

---

### Post by jimburt372 on 2007-10-29
> **heldal said:**
> What exactly do you want to achieve from your "re-build"? I suspect you might have quite a bit of work ahead if you aim to rebuild full functionality on a modern system. Such old boxes were usually running some custom application which may be anything but trivial to port to linux (or any other current system). I did my share of development and administration of xenix boxes back in the 80s and my experience wrt porting is that it involves export of all data to flat-files and re-design/re-build everything with current tools and applications. The exception may be old oracle databases for which there are tools to convert dumps even of ancient 80s systems into something that can be imported into a current version, but even there you'll have to reconstruct all other application logic.

=================

This system has an inventory system for a small parts store on it.  The owners are friends of my dad, and he asked me to try and help them out.

My goal is to be able to pull up the system to a point that I can transfer the inventory program and data onto a newer system for them.  This is an older couple that are planning to retire in a few years and it's not really worth them having to completely start over with a new Point of Sale system.  They would rather just use spiral notebooks and pencils than have to spend the money for a whole new system.  i haven't shopped around for them, looking for a new POS system, but they said that this one was $27,000.  Of course, in 1983 when they bought this, the PC alone probably cost $5,000.  

I am just trying to get to their inventory information right now, and then we will see what works best for them, if I can get anything pulled up.

I ramble.  I hope that helps shed some light on my objectives.  I still have no idea if any of that is realistic, but I am trying to just jump in with both feet and see if I can get anywhere.

---

### Post by jimburt372 on 2007-10-29
> **digitalbenji said:**
> Is the Xenix hard drive in the Ubuntu computer?

=================

Yes, the Xenix drive is now in the Ubuntu system.

My Ubuntu drive is SATA, and that is where the system boots, and the Xenix is antique IDE.

---

### Post by seuaniu on 2007-10-29
> **jimburt372 said:**
> ===================================

Thanks for the info.

I am amazed too that the system was still running.  The only 'real' problem with it is that the monochrome monitor is going crazy, and once the system goes into its 'text-graphics mode' or whatever you want to call the screen that is not strictly a command line, then everything shifts in such a way that what should be in the center of the screen is off at the edge of the screen, and there seems to be about a 1 inch gap between what goes off the right edge, and what begins wrapping to the left edge of the screen.

They haven't even changed out the power supply or anything.  When I was first called and told that this computer was 23 years old and that is needed some help, I assumed that they had overestimated the age, but there are several dates on the system components and the newest that I have seen was july 1983.  My jaw hit the desk.

When I followed your instructions, here is what I got after the last command:

jimmy@jimmy-desktop:/$ sudo mkdir /mnt/xenix
[sudo] password for jimmy:
jimmy@jimmy-desktop:/$ sudo mount -t sysv /dev/hda2 /mnt/xenix
mount: special device /dev/hda2 does not exist
jimmy@jimmy-desktop:/$ 

Is there some command I can type, or program I can run to determine what device description I should use (i.e. /dev/hda2)?

By the way, I have switched back to my main system, and now when I go to the Ubuntu Device Manager, now the 'Conner Peripherals 40MB CP3000' is listed, so it appears that Ubuntu recognizes that the device is in the system.  However, I don't see any designation even close to the /dev/xxxx that might help me figure out how to address the device.

Thanks again.  I don't want to be a leech that is only saying "help" but for the time being that is about all I am equipped to say.

I REALLY appreciate everyone for helping me.

Its hard to tell what device Ubuntu has assigned the drive, since I don't know what type of drive it is.  I'm fairly surprised that it can recognize it all, considering its age.  Hda is usually reserved for the master drive.  A slave drive or a drive on another controller will be hdb, hdc, and so on.  Also, some drives get assigned an s instead of an h if the OS thinks its scsi or some scsi derivative.  I usually figure out what it is by trial and error.  The number after the hda refers to the partition number.  hda1 refers to the first partition on the drive, hda2 the second, and so on.

You might be able to get some info by having a look at dmesg output.  These are messages that the system spits out on boot, and are hidden from view by the ubuntu start up graphic.

```
sudo dmesg | less
```

That will get you the dmesg through the less command, which will let you pageup and down through the messages, since they typically take up several screens.  Its like the old dos "more" command, but better.  Type q to quit the less program.

---

### Post by heldal on 2007-10-29
fdisk found the xenix-partition on hda4 so we know that the kernel at least is able to talk to the drive. For this there should be corresponding files in /dev (really device-files or pointers to kernel-space functions if you like). The error message indicates that /dev/hda4 doesn't exist. fdisk could read /dev/hda so you might have a look at the minor device-number of that one and create /dev/hda4 with the same major-device number and 4 added to the minor-number (it was the 4th partition according to fdisk). Then try mount with /dev/hda5 again.

"ls -l /dev/hda*"   will show the devices associated with the harddrive similar to this one (from a SATA system - hence sda as it is handles as scsi):
 ```
ls -l /dev/sda*
brw-rw---- 1 root disk 8, 0 2007-10-29 08:34 /dev/sda
brw-rw---- 1 root disk 8, 1 2007-10-29 08:34 /dev/sda1
brw-rw---- 1 root disk 8, 2 2007-10-29 08:34 /dev/sda2
brw-rw---- 1 root disk 8, 3 2007-10-29 08:34 /dev/sda3
```

The number 8 after the groupname "disk" is the major device number and the number after the comma (0 1 2 3 ) is the minor device-number.

If I were to create a device for a 4th partition on this drive I'd have to use the command:

```
sudo mknod -m 660 /dev/sda4 b 8 4
sudo chgrp disk /dev/sda4

```
chgrp is just used to set group ownership to the same as the other device-files. Use "ls" like above to verify.

---

### Post by jimburt372 on 2007-11-01
Hey folks!

Sorry for the delay, but I've been on the raod the last couple days.  

It appears that this problem has been settled for me, unfortunately, not in the way I would have hoped.

When I got back and fired everything back up, the system hung when booting for a long time (I hit the power button, then left to go to the gas station down the street for more Mountain Dew) and when I got back, it was still only about 10% booted, by the progress bar on the boot splash.  So I switched to a console view and it was listing bad sectors one after the other.  I have switched to a drive that I greated from the GHOST image I created when I started all of this, and it boots fine, and it shows up in device mgr, but when I try to mount it, here is what I get:

      ===========================

jimmy@Ubuntu710:~$ sudo mount -t sysv /dev/hda1 /mnt/xenix
[sudo] password for jimmy:
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

jimmy@Ubuntu710:~$ sudo mount -t xenix /dev/hda1 /mnt/xenix
mount: unknown filesystem type 'xenix'
jimmy@Ubuntu710:~$ 

      ===========================

So it appears that the sysv is the proper filesystem, but maybe the drive was already failing when the image was created and that is why the system started acting up initially, I mean besides the fact that it was built in 1983, and still running into 2007.

I am gonna try a few other things on this, but I fear this is the end for this 'valiant system' that has survivied all these years :-)  I guess we will all meet our own 'hard drive crash' someday.

Thank you all for all of the advice and guidance.  You have been most helpful in this a pretty bizarre situation.

Thanks again,

JimmyB

---

