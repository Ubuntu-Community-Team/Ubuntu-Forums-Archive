---
title: "Grub error 17"
date: 2007-08-12
forum: General Help
---

### Post by Hardi on 2007-08-12
Hey. I have a strange problem. I have 2 OSses - Windows and Ubuntu 7.04. I used PartitionMagic 8.0 under Windows XP and managed to get a grub error 17.

Here are the file systems from System Monitor:

Device Directory type 
/dev/hda5 /media/BACKUP ntfs
/dev/hda1 /media/disk-1 ntfs
fusectl /sys/fs/fuse/connections fusectl

I am not sure what info Id have to post. I would like grub to load fine, but it doesnt / error 17 and I dont know why.

thanks in advance.

---

### Post by dougfractal on 2007-08-12
[http://odzangba.wordpress.com/2007/03/10/how-to-restore-grub-using-the-ubuntu-live-cd/](http://odzangba.wordpress.com/2007/03/10/how-to-restore-grub-using-the-ubuntu-live-cd/)
> How to restore GRUB using the Ubuntu Live CD

After deleting my fiesty fawn partition late yesterday, Grub came choking with an Error 22 message. No big deal, I thought&#8230; all I have to do is re-install grub. So I got out my dapper livecd and fired the pc up. I executed the grub-install command with the appropriate options and rebooted the pc&#8230; Error 22 again! Repeated the process&#8230; no change. So I got out my breezy alternate install cd and skipped to the &#8220;install grub boot loader step&#8221;. Grub installation failed! Now I was in big trouble. If all else fails, google is the way. :) I found some instructions on using the grub shell to install grub and that worked! So for those who need to install grub using the ubuntu dapper (and above) livecd, here they are:
Open the terminal and enter the following commands

sudo grub
root (hd0,1)
setup (hd0)
quit

You may have to modify the hard disk parameters to suit your setup. My root partition is the second on my first hard disk. If yours is the first for instance, then you&#8217;ll have to modify the &#8220;root&#8221; step as follows:

root (hd0,0)

Hope this helps someone. :D

---

### Post by merlinus on 2007-08-12
Boot from live cd.  Open a terminal and post results of:

```

sudo fdisk -l

```

-merlin

---

### Post by Hardi on 2007-08-13
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5749    46178811    7  HPFS/NTFS
/dev/hda2            6375        9733    26981167+   f  W95 Ext'd (LBA)
/dev/hda3            5750        6374     5020281   83  Linux
/dev/hda5            6375        9733    26981136    7  HPFS/NTFS

Partition table entries are not in disk order

---

### Post by Hardi on 2007-08-13
hda1 is the for windows xp.
hda3 is for linux
hda5 is the backup space i use to copy files to and from.
I don\t know what hda2 is though - it must have been created while PartitionMagic messed up(During the process it said: Error, unknown file system.)

I managed to copy my vital data though and moved it to another computer, buyt it would be great if Id get this one to work.

thanks

---

### Post by OzzyFrank on 2007-08-13
Here's my guide on restoring GRUB. Hope this can be of help!

[COLOR="#800080"]**[COLOR="Blue"]GRUB Error: Partition Not Found[/COLOR]**[/COLOR]

**[COLOR="Purple"]Check for Incorrect Drive References[/COLOR]**
If GRUB can load its menu, then obviously the partition exists, so there is no need to panic. Even if Ubuntu is on a second drive and you let the install do its default of putting GRUB in the MBR of your first drive (ie: your Windows drive), it's getting its information from fstab on your Ubuntu partition. The most common culprits for this error occurring are programs that change fstab entries without your knowledge (eg: hard drive mounting programs) and programs or processes that rename drives from &#8220;hda1&#8221; to sda1&#8221;, etc (eg: kernel updates, partition programs, hard drive utilities). Then there is the possibility that something is amiss with GRUB itself, which is evident when your drives and fstab entries match. All of these scenarios can be fixed, but first you have to find out what is actually happening.

**sudo gedit /boot/grub/device.map**
will let you check and edit drive listings in Ubuntu. The output will be something like this:
(hd0)	/dev/sda
(hd1)	/dev/sdb

**sudo gedit /etc/fstab**
will let you check your fstab for errors. The output will be something like this (the Ubuntu partition is highlighted; below it is the swap partition):
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#** /dev/sdb1**
UUID=2d0e29e9-b3c6-4fb7-b2fa-7e876dc2f630 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=ae50f6e3-cae4-4313-8876-fd919322f913 none            swap    sw              0       0

If you suspect something like a kernel update or playing around in a partition program has changed the names of your drives, you can check this by running **fdisk -l **or **gparted** from the Live CD command prompt or terminal (or System > Administration > GNOME Partition Editor from the desktop). Then you can see if your &#8220;hdb1&#8221; is now an &#8220;sdb1&#8221;, and if so simply change those letters in the fstab entries and reboot. This scenario usually only affects drives other than your boot drive that you are trying to mount at boot with fstab (so your Ubuntu on &#8220;hdb1&#8221; will still boot even though technically all your drives now start with an &#8220;s&#8221;, but the others won't mount because of this). That said, the biggest cause of this error is by far wrong entries in fstab (and device.map), so your solution should lie there. If not, then something probably messed up GRUB, so it may be that you need to restore it, which is easily done.

**[COLOR="Purple"]Restoring GRUB[/COLOR]**
You will either need a Super GRUB Disk or your Ubuntu disc, and as long as your drive references are fine everywhere, it will only take a couple of commands to fix things. You will need to decide if GRUB is going in the MBR (master boot record of the drive) or on the partition. If Ubuntu is sharing a drive with Windows, choosing MBR will get back the GRUB menu and let you boot either. If Ubuntu is installed on another drive, and you use a boot manager to boot your partitions, then choosing to install GRUB on the partition may be better. If one doesn't work, then try the other. Simply enter the first command followed by the other. To get to the command prompt on the Super GRUB Disk, type C; to get to the grub> prompt on your Ubuntu CD, go to command line and enter the following before entering the GRUB restore commands:

**grub**

[COLOR="#800080"]**Restore GRUB to the Master Boot Record (eg: 1st partition on 2nd drive)**[/COLOR]
**root (hd1,0)**
**setup (hd1)**

[COLOR="#800080"]**Restore GRUB to a Partition (eg: 1st partition on 2nd drive)**[/COLOR]
[B]root (hd1,0)
setup (hd1,0)[/B]

[COLOR="#800080"]**Note sure? Find the Partition where GRUB is**[/COLOR]
At the grub> prompt enter:
**find /boot/grub/stage1**

---

### Post by Hardi on 2007-08-14
> **OzzyFrank said:**
> Here's my guide on restoring GRUB. Hope this can be of help!

[COLOR="#800080"]**Restore GRUB to the Master Boot Record (eg: 1st partition on 2nd drive)**[/COLOR]
**root (hd1,0)**
**setup (hd1)**


This worked. Thanks.

---

