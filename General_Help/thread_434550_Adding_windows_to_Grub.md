---
title: "Adding windows to Grub"
date: 2007-05-06
forum: General Help
---

### Post by PricklySponge on 2007-05-06
Hi.

I currently have Ubuntu on an 160 Gig SATA harddrive. I also have an 80Gig IDE Hdd ( There is also a DVD/RW on the IDE ribbon) . When I installed windows on the IDE hdd I did not have the Ubuntu Hdd plugged in. Now the only way to boot into windows is to unplug the Ubuntu Hdd. When I have both Hdd's plugged into the computer, it automatically boots into Ubuntu ( I can also see the Hdd from Ubuntu's computer file browser)

What I would like to do is configure GRUB to allow me to choose what Hdd to boot from when I boot the computer

How do I do this?

Thanks,
PricklySponge:)

---

### Post by Martje_001 on 2007-05-06
First:
```
sudo gedit /boot/grub/menu.lst
```

Then add the following lines at the end of the file:
```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
Change (hd0,0) to your needs. The first 0 is your harddisknumber (start counting with 0), the second 0 is your partition (also; start to count with 0). If you don't know what to fill in, try some out.

---

### Post by PricklySponge on 2007-05-06
Do I type that in before or after "### END DEBIAN AUTOMAGIC KERNELS LIST"?

This is what the file looks like:

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
# kopt=root=UUID=722fb1ca-4fe6-4fad-a393-78100c377931 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=722fb1ca-4fe6-4fad-a393-78100c377931 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=722fb1ca-4fe6-4fad-a393-78100c377931 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by PricklySponge on 2007-05-06
Edit: I've done (hd1,0) and (hd1,1) and both times I got GRUB error 21. What do I do?

---

### Post by KIAaze on 2007-05-06
> **PricklySponge said:**
> Do I type that in before or after "### END DEBIAN AUTOMAGIC KERNELS LIST"?


I think it doesn't matter.
Everything that follows a "#" is just a comment.
Theoretically, it would be more logical to add it after it since it has nothing to do with Debian, unlike Ubuntu.

> Edit: I've done (hd1,0) and (hd1,1) and both times I got GRUB error 21. What do I do?

Grub Error 21 means: "Cannot find disk":
> 21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

[http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors]("http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors")

Post the result of ```
sudo fdisk -l
```.
That might help others find a solution I think.
Can you mount the windows partition from Ubuntu?

I believe the main problem comes from having 2 MBRs since you installed each OS on its own HD...

---

### Post by PricklySponge on 2007-05-06
Here are the results.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18700   150207718+  83  Linux
/dev/sda2           18701       19457     6080602+   5  Extended
/dev/sda5           18701       19457     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

---

### Post by KIAaze on 2007-05-06
Here's someone who had a similar problem, altough with LILO:
[http://www.linuxquestions.org/questions/showthread.php?t=481603]("http://www.linuxquestions.org/questions/showthread.php?t=481603")
I hope this helps. :)

Makes me want to have a desktop PC instead of a laptop so I can try stuff like this too...

---

### Post by PricklySponge on 2007-05-06
It loosk like both of that guys Hdd's were IDE. I have 1 SATA and 1 IDE

---

### Post by KIAaze on 2007-05-06
Ok, posted at the same time. ^^

Well, it appears an obvious solution would be to replace (hd0,0) by something like (sdb1,0) or (hda1,0) when editing /boot/grub/menu.lst.
Just try. With Grub, there no big risk if you back up your previous menu.lst. ;)

And it's apparently also possible to edit Grub bootup commands directly at startup by pressing "e", but I never really understood how it works.
Set the timeout to -1 so you can have time to play with grub at startup if you want. (timeout=-1 means infinite time to choose)(putting "#" in front of it also works I think)

---

### Post by PricklySponge on 2007-05-06
> **KIAaze said:**
> Ok, posted at the same time. ^^

Well, it appears an obvious solution would be to replace (hd0,0) by something like (sdb1,0) or (hda1,0) when editing /boot/grub/menu.lst.
Just try. With Grub, there no big risk if you back up your previous menu.lst. ;)

How do I edit it like that, and back up my grub menu?

---

### Post by PricklySponge on 2007-05-06
This is what my grub thing looks like

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
timeout		-1

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
# kopt=root=UUID=722fb1ca-4fe6-4fad-a393-78100c377931 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=722fb1ca-4fe6-4fad-a393-78100c377931 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=722fb1ca-4fe6-4fad-a393-78100c377931 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Microsoft Windows XP Home
root		(hd1,1)
savedefault
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by PricklySponge on 2007-05-06
someone wanna help me out?

---

### Post by KIAaze on 2007-05-07
> **PricklySponge said:**
> How do I edit it like that, and back up my grub menu?

To back it up, just copy it to another file while in Ubuntu like this:
```
sudo cp /etc/grub/menu.lst /etc/grub/menu.lst.bkp
```

If you have problems booting up Ubuntu again, boot from the Ubuntu live-CD, mount the Ubuntu partition and restore the backup:
```
mkdir /mnt/ubuntu
mount /dev/sda1 /mnt/ubuntu
cp /mnt/ubuntu/etc/grub/menu.lst.bkp /mnt/ubuntu/etc/grub/menu.lst

```

But if you don't touch the Ubuntu entry in you menu.lst file, this shouldn't happen at all.

Now for your current menu.lst, have you tried (hd1,0)?

And maybe you could also try to restore the MBR with the Ubuntu CD:
[http://ubuntuforums.org/showthread.php?t=76652]("http://ubuntuforums.org/showthread.php?t=76652")
This should hopefully work and is an easy solution.
========================
About the editing:
I installed Debian after Ubuntu, so my GRUB was reinsatlled by Debian automatically and I have the possibility to press "e" to go into a so-called edit-mode. I don't remember if the Ubuntu Grub offers the same option.

However I found this in the Grub manual:
> When booting with GRUB, you can use either a command-line interface (see Command-line interface), or a menu interface (see Menu interface). Using the command-line interface, you type the drive specification and file name of the kernel manually. In the menu interface, you just select an OS using the arrow keys. The menu is based on a configuration file which you prepare beforehand (see Configuration). While in the menu, you can switch to the command-line mode, and vice-versa. You can even edit menu entries before using them.

So it's just a matter of configuration. Unfortunately, I never went further into grub than the menu.lst file.

If you have some time and don't mind reading a lot, you could probably find a solution by reading the [GRUB manual]("http://www.gnu.org/software/grub/manual/grub.html").

Otherwise, I'd recommend that you post your question on a forum more populated by Linux-gurus like [linuxquestions.org]("http://www.linuxquestions.org/questions/index.php") or a gentoo/debian forum.

Here the questions tend to get drowned very fast and most complex things remain unsolved.

But once you find the solution, post it back here. It might always be useful to somebody else. ;)

---

### Post by public_void on 2007-05-07
Hopefully this might help [http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows)

It says that Windows has to boot from the first hard drive, however grub can overcome this problem by using the map command. You would have to boot to the grub command line in order to do this. One thing I couldn't find was how this effects menu.lst, and the drives/partitions specified.

---

### Post by Nehvrook on 2007-05-07
Hi, I'm new to Linux and Ubuntu. I installed it the other day just like OP.
Only I have two SATA hard drives. One with Windows XP pro installed, the other with Ubuntu 6.10 installed. I'm having the same problem with trying to get grub to let me boot Windows.
I've tried the suggestions here but I don't really know what I'm doing.
One thing worth noting I think is I can't see the hard drive with windows installed while running Ubuntu (It's plugged in and in the bios and everything, but I cant access or even find it in the ubuntu file browser) however I can see my external hard drive.
I edited the grub menu thing and added Windows and I put the hard drive down as (hd1,0) and when I go to boot it it says "Starting up" but then just does nothing at all. When I tried different hard drive settings ( like (hd1,1)) I got the error that there's no such partition.
If anyone give any suggestions or help I'd apreciate it

---

### Post by KIAaze on 2007-05-07
I can't help you more than the original poster except for one thing: accessing the windows partition from Ubuntu.

You can't see the windows partition under Ubuntu if you haven't mounted it.
But, if the hardware is set up properly (master/slave stuff), you should see the windows partition by typing:
```
sudo fdisk -l
```

Here's a tutorial about how to mount the windows partition under Ubuntu:
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

---

### Post by Nehvrook on 2007-05-07
Thanks, I'll give it a go :)

---

### Post by Nehvrook on 2007-05-08
Hi, just to let you know. I downloaded Ubuntu 7.04 and ripped it to a CD. I booted it up as a live CD and did a fresh install of Ubuntu with my windows hard drive still plugged in. This time Ubuntu automaticaly detected the other hard drive, and Grub automaticaly has it listed as a choice at startup.
I can also now see my other hard drive and access it while in Ubuntu by mounting it.

Thanks for the help, and I hope this helps the op too :)

---

### Post by eks on 2007-05-22
The best solution indeed is Nevhrook one. But if you were afraid to partition and format another hard drive just for Ubuntu and disconnected the previous one with Windows during the installation, you will run into this problem to have to add Windows boot manually, like I did. And if searching Ubuntu forum you reach this thread like I did, the solution is simply adding this to /boot/grub/menu.lst:

```

title		Windows XP Professional
root		**(hd1,0)**
savedefault
makeactive
chainloader	+1
map **(hd0) (hd1)**
map **(hd1) (hd0)**

```

The bold parts depends on where your Windows partition is, which you can find out by typing:
```

sudo fdisk -l

```

The problem is that [Windows boot must be on the first hard disk/partition in order to boot]("http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows"). You trick it into thinking that by adding those two lines.



**_[SIZE="6"]COMPLETE TUTORIAL[/SIZE]_**

Backup your menu.lst first:
```

sudo cp /etc/grub/menu.lst /etc/grub/menu.lst.bkp

```

Find out where your Windows hard disk is with (if you are confused here just post the result here and someone might help)
```

sudo fdisk -l

```

Then you need to add the new entry to grub with
```

sudo gedit /etc/grub/menu.lst

```

And then add the entry:
```

title		Windows XP Professional
root		**(hd1,0)**
savedefault
makeactive
chainloader	+1
map **(hd0) (hd1)**
map **(hd1) (hd0)**

```

If your Windows is on a second SATA you have to use sd1 instead of hd1, I think. The second line of the map command is just so your Ubuntu hard drive will be recognizeable on Windows. If you need to read/write on Ubuntu partitions from Windows or vice-versa, you need to search for other tools (ntfs-3g and ntfs-config for Ubuntu and ext3 for Windows), but that's outside the scope of this thread.

If you need more information on grubs map command you can find it [**here**]("http://www.gnu.org/software/grub/manual/html_node/map.html#map").


eks

---

### Post by gee42 on 2008-06-28
eks,

thanks for the post it worked perfectly for me. I wanted to feedback on the comment about not being sure if you needed "sd1" for SATA drives; I'm not a grub or linux expert but I've done this with two SATA drives, ubuntu first XP second, and using "hd1" worked fine. Here's my grub entry (in my case I had a diagnostic partition before XP on my Dell system, hence (hd1,1) ):

title           Windows XP Professional
root            (hd1,1)
savedefault
makeactive
chainloader     +1
map (hd0) (hd1)
map (hd1) (hd0)

XP boots quite happily. Hope this helps clarify.

Guy.

---

