---
title: "Grub Errors &amp; External USB Hard Drive"
date: 2007-07-11
forum: General Help
---

### Post by jasdparker on 2007-07-11
Hello, this is my first post with a rather peculiar problem.

I have a dell 8400 and a USB Iomega 200 GB external hard drive.

I have Windows Vista on the first partition of my first drive, and then Ubuntu on the 2nd partition of the first drive.  All that exists on my 200 gb external drive is data, no operating systems.

Here are the conditions I run in to.

If my usb drive is connected and been powered on for a while, I get GRUB Error 17 (after a few seconds of grub 'thinking' about what to do)

If I turn off and unplug the USB drive I instantly get Error 21 when I boot.

If I plug the usb drive in and turn it on, it seems I have a window of about 10-15 seconds where if I reboot in that timeframe, I'll be shown the grub menu with the Ubuntu choices and Windows Vista.  If I wait any longer, I get the error 17 again.

This is a repeatable process, I've even tested it to make sure it wasn't a fluke.  I've looked through the Grub menu.lst files and don't see any reference at all to the USB drive, and can't think where else to look for it (relative newbie).

It would be nice if I could somehow make grub not even consider the USB drive and only see the internal drive at boot.

Any help would be appreciated.

Thanks in advance!

---

### Post by confused57 on 2007-07-11
Boot into Ubuntu, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

```
gedit /boot/grub/menu.lst
gedit /etc/fstab
gedit /boot/grub/device.map
```
menu.lst is short for menu.list...

You probably don't need to post /etc/fstab, but won't hurt to do so...

---

### Post by jasdparker on 2007-07-11
Thanks so much, kind of pulling my hair out here!!


Contents of fdisk -l
***********************************
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        7655    61440000+   7  HPFS/NTFS
/dev/sda3           18961       19452     3951990   db  CP/M / CTOS / ...

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24720   198563368+   b  W95 FAT32
/dev/sdb2   *       24721       38539   111001117+  83  Linux
/dev/sdb3           38540       38913     3004155    5  Extended
/dev/sdb5           38540       38913     3004123+  82  Linux swap / Solaris
***********************************
end fdisk -l

menu.lst
***********************************
## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=eaa9ef4b-1e67-4805-8e34-0c616c032276 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=eaa9ef4b-1e67-4805-8e34-0c616c032276 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=eaa9ef4b-1e67-4805-8e34-0c616c032276 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=eaa9ef4b-1e67-4805-8e34-0c616c032276 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

***********************************
end menu.lst

fstab
***********************************
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=eaa9ef4b-1e67-4805-8e34-0c616c032276 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=70e42e64-66d3-45d1-a1ff-42ed3f826eac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
***********************************
end fstab


device.map
***********************************
(hd0)	/dev/sda
(hd1)	/dev/sdb
***********************************

---

### Post by confused57 on 2007-07-11
> I have Windows Vista on the first partition of my first drive, and then Ubuntu on the 2nd partition of the first drive. All that exists on my 200 gb external drive is data, no operating systems.
This doesn't really agree with the output of your fdisk -l:
```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 6 48163+ de Dell Utility
/dev/sda2 * 7 7655 61440000+ 7 HPFS/NTFS
/dev/sda3 18961 19452 3951990 db CP/M / CTOS / ...

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 1 24720 198563368+ b W95 FAT32
/dev/sdb2 * 24721 38539 111001117+ 83 Linux
/dev/sdb3 38540 38913 3004155 5 Extended
/dev/sdb5 38540 38913 3004123+ 82 Linux swap / Solaris
```
Your fdisk -l shows Vista on sda(your internal drive?) and Ubuntu on /dev/sdb(your external drive?)

Is the 320 Gb drive a 2nd internal drive and your 200 Gb external drive isn't being shown by fdisk -l?

---

### Post by jasdparker on 2007-07-12
That's what I initially thought too when I looked at it a few days ago.  And, you're right, it is a 320 gb external usb drive, not 200.  I only said 200 because in the file browser it shows that drive as 189gb.

I'll tell you the story from the beginning.

What I originally had:

160GB drive dedicated to Vista minus the dell recovery and other dell partition & 1 320 GB external usb drive with data only.

I wanted to preserve my windows settings, and I read that you could use the Knoppix Live cd and use the qtparter to resize the windows partition.  I did that, and set the windows partition to 60 gb, and the 2 dell partitions coming to about 20 gigs or so, which left me 80mb's for Ubuntu.

I then launched the Ubuntu installer 7.04 (I think) 64 bit.  I went through the guided setup and asked it to use the free space on hd0 or sda.  I wanted to leave my external drive alone since it only holds data.

But, what it seems like it did was go ahead and use some space on my external drive even though that's not what I wanted.  I don't know how it could have done that though, because I was sure when I used that knoppix partition manager that I stayed clear of my external drive.

So, here's what I'm wondering...  

1) Are fdisk, fstab, and menu.lst completely wrong?

2)  Or is there a bug in the Ubuntu install that even though I specified my internal drive, it chose the external instead?  I can't imagine it could have done that because when I used knoppix partition tool, it resized my internal drive.  My windows drive shows as 60 gb's.  Instead of it's original 160 gb's or so.  So I know that happened okay.  I guess what I'm asking is that if I have my external drive that is all one partition, if I asked Ubuntu to install itself on the 2nd partition on my internal, would it be possible for it to look at my external, and just 'grab' free space and create it's own partition out of a 1 partition disk and make 2?

I don't know if I made any sense there, I hope so.

Thanks so much!

---

### Post by jasdparker on 2007-07-12
Oh, and p.s.

I've been in computing for about 20 years now.  I set up a Win 95/ Red hat dual boot system years ago, so I am familiar with partitions, etc.  So, I guess, I said I was a Linux newbie because I haven't dealt with it for a while.  I have linspire running on a laptop just fine.  Not dual boot, but I get it, I guess that's the point I'm trying to make.

I guess my confusion is if something didn't happen the way I asked it to, I'm not sure why.

---

### Post by confused57 on 2007-07-12
> 1) Are fdisk, fstab, and menu.lst completely wrong?
No, I believe they are correct.

> I then launched the Ubuntu installer 7.04 (I think) 64 bit. I went through the guided setup and asked it to use the free space on hd0 or sda. I wanted to leave my external drive alone since it only holds data.
A guided install(the first option will automatically resize the one partition and install Ubuntu on the free space), see this howto:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
When I do an install I make sure to note the size of the hard drive I'm installing to, as well as the partition layout of the drive, to ensure I'm installing on the correct hard drive...I don't really use the /dev/sda or /dev/sdb designation, which are subject to change with different distro installers & kernels.

> So I know that happened okay. I guess what I'm asking is that if I have my external drive that is all one partition, if I asked Ubuntu to install itself on the 2nd partition on my internal, would it be possible for it to look at my external, and just 'grab' free space and create it's own partition out of a 1 partition disk and make 2?
Again, this could happen due to the process of the guided install(#1 option) as mentioned above.  I'm not aware of any bugs in the installer that would cause what happened to you, I'm not saying there isn't.

What I would suggest is to disconnect your external drive and reinstall Ubuntu to the free space on your internal hard drive.  Gparted should show your Dell Utility on the first partition(/dev/sda1),  Vista on the 2nd partition(/dev/sda2) and the rest as "unallocated" space(approx 100 Gb).  
Here are some excellent guides for planning partitions:
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

If there's anything you don't understand, feel free to ask questions...if I can't answer them, there are plenty of people in the forum who can.

---

### Post by jasdparker on 2007-07-12
You were exactly right.  I have no idea how it happened, but it did take up the free space on my external drive instead of what I thought I asked it to do and use the free space on my internal.

I did what you mentioned and unplugged the external and re-installed Ubuntu.  I plugged the drive in, and everything is working perfectly.

Now, what I'm wondering, is how can I recover that space I've lost on my external drive.

What I would like is to expand the partition to cover the entire disk, but I could live with 2 partitions if I have to.  Any thoughts there?

Thanks so much for your help! You Rock!

---

### Post by confused57 on 2007-07-12
> **jasdparker said:**
> You were exactly right.  I have no idea how it happened, but it did take up the free space on my external drive instead of what I thought I asked it to do and use the free space on my internal.

I did what you mentioned and unplugged the external and re-installed Ubuntu.  I plugged the drive in, and everything is working perfectly.

Now, what I'm wondering, is how can I recover that space I've lost on my external drive.

What I would like is to expand the partition to cover the entire disk, but I could live with 2 partitions if I have to.  Any thoughts there?

Thanks so much for your help! You Rock!
Great, I thought it would work.   You could probably use Gnome Partition Editor in the live cd to delete your Ubuntu partitions on your external hard drive, then just resize the FAT32 partition.

I always use the Gparted Live CD for partitioning:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)
it's only a 45-50 Mb download & has a later version of gparted than the Ubuntu live cd.

---

### Post by jasdparker on 2007-07-12
Hey there, I just downloaded gparted from the synaptic package manager and ran it locally.  The tool was really easy to use, and I was able to resize my data partition to the full size of the drive.

All of my problems were solved.  Thanks so much for all of your help!!

---

