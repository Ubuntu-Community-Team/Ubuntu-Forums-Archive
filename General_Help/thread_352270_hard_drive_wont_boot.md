---
title: "hard drive wont boot"
date: 2007-02-03
forum: General Help
---

### Post by gmcm1979 on 2007-02-03
I have been running ubuntu 6.06 for this last few months, without any serious problems. I currently have two hard drives and i installed ubuntu onto one of these drives.
 i then disconnected my hard drive with ubuntu on it and erased all data on my second disk and installed windows xp on it in order to play some games that i have just bought. i then reconnected my ubuntu hard drive and disconnected my xp one and have then tried to boot and it doesnt start, there are no error messages of any kind. i can use the live cd but cant get access to my hard drive.
can anyone help me.

---

### Post by Bigbluecat on 2007-02-03
It sounds like you don't have a bootloader present. That would mean we need to re-install grub which is quite straightforward. Before we proceed we need to know how many disks are currently installed, which file systems and what order. 

Use the liveCD, open a terminal and enter the following command:

```
sudo fdisk -l
```

Paste the output back here.

---

### Post by gmcm1979 on 2007-02-03
output is:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30023   241159716   83  Linux
/dev/sda2           30024       30401     3036285    5  Extended
/dev/sda5           30024       30401     3036253+  82  Linux swap / Solaris

---

### Post by Bigbluecat on 2007-02-03
OK. Simple disk partitions.

Boot from the liveCD open a terminal and type:

```
grub
```

This should bring up the grub command line.

Next we need to find out where the grub boot files are so enter:

```
find /boot/grub/stage1
```

This should return an hd location - (hd?,?) where ?,? are numbers. Most likely in your case (hd0,0).

Now we need to tell grub where it's root is:

```
root (hd?,?)
```

Where ?,? are the numbers returned by your find command.

Lastly we write grub to you MBR:

```
setup (hd0)
```

This writes the grub bootloader to the first boot partition of the first drive.

```
quit
```

Exits the grub command.

Now shutdown. Remove the liveCD and boot. With luck we are back in business.

---

### Post by gmcm1979 on 2007-02-03
thanks for the help

i have now connected my second hard drive 
grub starts to load but stops and gives the following error

/dev/hda1 - superblockcould not be read or does not describe a correct ext2 filesystem

---

### Post by igknighted on 2007-02-03
Sounds like your system wants to call hda as (hd0).  You can change any instance of (hd0,#) to (hd1,#) and see if that works.  Also, if you do that, you need to put the (hd1,#) in front of the path to the kernel and initrd files, otherwise it will get very confused:
```
title Ubuntu
root (hd1,0)
kernel (hd1,0)/boot/*kernel_filename* root=/dev/sda1 *boot-options*
initrd (hd1,0)/boot/*initrd_filename*
boot
```

---

### Post by Bigbluecat on 2007-02-03
OK. Now you have changed the drive configuration it would be wise to check again the order of the drives and partitions. 

Can you go back to the liveCD and run another sudo fdisk -l. Post the output back here please.

We may need to edit your menu.lst file to have everything pointing to the correct partitions.

---

### Post by Bigbluecat on 2007-02-03
I forgot to ask. 

Did the system boot before you added your second drive back in.

---

### Post by gmcm1979 on 2007-02-03
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30023   241159716   83  Linux
/dev/sda2           30024       30401     3036285    5  Extended
/dev/sda5           30024       30401     3036253+  82  Linux swap / Solaris

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9963    80027766    7  HPFS/NTFS

---

### Post by Bigbluecat on 2007-02-03
Now once more open a terminal and type grub to get to the grub command line. We are going to use grub to tell us exactly what it calls the disks an partitions. There is a very useful way to get grub to list the options and that is by using the "TAB" key before completing a command.


```
geometry (hd
```
Instead of hitting enter hit the tab key. It should return with 

"possible disks are" and a list - lets say hd0 and hd1.

We can then enter:

```
geometry (hd0)
```

This will list the partitions and file types in grub terms. You can repeat this for  each of the drives.

```
find /boot/grub/stage1
```

And:

```
find /vmlinuz
```

This finds the linux kernel.

Post the results of the above and we will have a pretty complete view of how grub is numbering the disks and where your boot and kernel reside. With this in hand we should be able to install grub and fix up the menu.lst without having to guess.

---

### Post by gmcm1979 on 2007-02-03
grub> geometry (hd0)
drive 0x80: C/H/S = 9964/255/63, The number of sectors = 160086528, /dev/hda
   Partition num: 0,  Filesystem type unknown, partition type 0x7

grub> geometry (hd1)
drive 0x81: C/H/S = 30401/255/63, The number of sectors = 488397168, /dev/sda
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

grub> find /boot/grub/stage1
 (hd1,0)

grub> find /vmlinuz
 (hd1,0)

---

### Post by Bigbluecat on 2007-02-03
OK. 

When you added your second disk it is being seen as hd0. So the way we set up grub is not longer valid.

You can see that /dev/hda is now seen by grub as hd0. I know that this is you windows drive as it cannot recognize the file system (grub does not recognize NTFS).

We need to re-install grub to point to the correctly name locations for boot files and kernel. This is now (hd1,0) and set up grub in the MBR of hd0 (which is now /dev/hda).

So - back to the grub command line:

```
root (hd1,0)
setup (hd0)
quit
```Now reboot.

---

### Post by gmcm1979 on 2007-02-03
i now get the following error message

root (1,0)
Filesystem type unknown, partition type 0x7
kernel /boot/vmlinux-2.6.15-27-386 root = /dev/sda1 ro quiet splash
Error 17: cannot mount selected partition

---

### Post by Bigbluecat on 2007-02-03
My fault. I should have also said we need to edit your menu.lst so that it points to the right place to find your kernel. This is what igknighted pointed out in his post.

So we need to mount your drive and edit the menu.lst

Back to the liveCD and open a terminal. Now just as a caution I have not had to mount a drive from the liveCD before but I think this is how it is done.

```
sudo mkdir /mnt
```

Creates a point where we can mount your drive.

```
sudo mount /dev/sda1 /mnt
```

Mounts your drive on /mnt

```
cd /mnt/boot/grub
```

now we should be in the directory that contains the menu.lst file. If you type ls you should see it.

First make a backup - good habit to get into

```
sudo cp menu.lst menu.lst_backup
```

Now we edit your menu.lst file

```
sudo gedit menu.lst
```

You are looking for the lines that point to your Ubuntu Kernel. They need to be changed to point to (hd1,0) as igknighted stated. Right now I think they are pointing to (hd0,0) because you only had one drive present at setup.

Find lines like this:

title Ubuntu
root (hd1,0)
kernel (hd1,0)/boot/*kernel_filename* root=/dev/sda1 *boot-options*
initrd (hd1,0)/boot/*initrd_filename*
boot
and make sure they are pointing to (hd1,0) and not (hd0,0). Save and exit. Then reboot again.

If you are not sure about this copy and post the contents of your menu.lst so that we can look at it first.

---

### Post by gmcm1979 on 2007-02-03
i have already changed the menu.lst here is a copy of it, hopefully this will help:

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
# root		(hd1,0)
# kernel	/vmlinuz root=/dev/sda1 ro
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

title		Ubuntu, kernel 2.6.15-27-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Bigbluecat on 2007-02-03
Interesting.

Why don't we try putting (hd1,0) in front of the kernel paths as suggested by igknighted.

kernel (hd1,0)/boot/*kernel_filename* root=/dev/sda1 *boot-options*
initrd (hd1,0)/boot/*initrd_filename*

---

### Post by gmcm1979 on 2007-02-03
same problem error 17: cant mount selected partition

---

### Post by Bigbluecat on 2007-02-03
OK. 

One more thing to check.

In your /boot/grub directory there is a file call device.map. Open this and paste the contents. It's possible that this may be re-mapping the drives.

---

### Post by gmcm1979 on 2007-02-03
(hd0)	/dev/hda
(hd1)	/dev/sda

---

### Post by Bigbluecat on 2007-02-03
Well. The map looks OK.

I'm struggling to come up with more suggestions. I have seen some threads that suggest the some bios can in effect hide a drive until the system is booted so it may be worth checking your bios settings. Make sure that the boot order is the same as we think it is.

My last few suggestions are to download SuperGrubDisk. It is a very useful utility to keep around.

Once you have this we can try to manually boot your kernel. This will take us step by step through the exact boot sequence and drive numbers. If we find any differences between this process and your menu.lst then we can adjust after that.

---

### Post by gmcm1979 on 2007-02-03
i have the floppy version of super grub disk

---

### Post by Bigbluecat on 2007-02-03
The floppy version will work.

In the past I've had some tricky dual boot problems and Herman's dual boot guide together with SuperGrubDisk have never let me down.

Boot from SuperGrubDisk and use that to get to a grub command line.

Here's the link to Herman's guide:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Scroll down until you find:

                                                  How to get GRUB's Command Line to investigate a computer

                                                  How To Boot Linux from GRUB's CLI

If you click on the first link it will take you through the investigation. Essentially the same geometry and find commands we used before. Continue scrolling down this page and it will step you through the manual boot process. Make a note of anything useful in the way of drive numbers and names as you go.

I suggest reading through this a couple of times first and printing relevant pages so you have them in front of you - I had a separate laptop that I could use for online reference.

Follow the instructions step by step and it is quite easy.

---

### Post by gmcm1979 on 2007-02-03
ill give that a try

thanks for your time and help, hopefully can get it working again

---

### Post by Bigbluecat on 2007-02-03
If you get it running post back. I'd like to understand what is really going on.

Good luck

---

### Post by Bigbluecat on 2007-02-03
One last thing.

On my system I have two internal drives and one external which is used as a windows backup.

/dev/sda is NTFS windows
/dev/sdb is Linux
/dev/sdc is the external drive

Now in normal grub terms my linux drive should be (hd1,0). But it's not. I have to use (hd2,0).

I could only find this through manually booting the kernel.

---

### Post by gmcm1979 on 2007-02-04
i dont understand how to use super grub disk when i boot from it i get a command prompt but the instructions seem to be about a version with a gui can anybody help

---

### Post by Bigbluecat on 2007-02-05
Looks like you may need a new version of supergrubdisk:

[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

Herman's guide also very useful:

[GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by gmcm1979 on 2007-02-05
i had previously mounted my drive that has windows as an extra drive in ubuntu, do you think this could have something to do with my problem, could ubuntu still think that this drive is an ubuntu filesystem

---

### Post by gmcm1979 on 2007-02-05
fixed it 

had to comment out the line in fstab that mounted my hard drive as an ubuntu partition

now going to find out how to dual boot off 2 disks, i think i have seen a thread in here before

---

### Post by Bigbluecat on 2007-02-05
Happy to hear you are up an running.

There is plenty of help on dual booting with 2 hard drives. That is what I do. 

The favoured method seems to be to install a single drive and load windows. Get this running. 

Takes this drive out then put in your new drive for Ubuntu in the primary position and get this running.

Lastly put the windows drive into the slave position and modify menu.lst to boot it. In this way grub does not overwrite the windows MBR and if you need to get back to windows in a hurry and Ubunutu is not working just take out your Ubuntu drive, move the windows drive to primary and it should boot straight away.

Enjoy

---

