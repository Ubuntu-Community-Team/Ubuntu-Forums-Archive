---
title: "[SOLVED] Changed mount point - now cannot mount volume"
date: 2008-04-27
forum: General Help
---

### Post by dorkdork777 on 2008-04-27
I decided to change the mount point of one of my partitions, to something relating to the files on it. I right-clicked on the drive on the desktop, went to "Volume", and changed the mount point to /media/Storage. Then, I unmounted it, and tried to mount it again:

[IMG]http://i71.photobucket.com/albums/i154/dorkdork777/nomount.png[/IMG]

So now I can't access the option to change the mount point, as that option only comes up when it's mounted. How do I change the mount point via the Terminal, or otherwise?

(BTW - I changed another one to just "Windows" and it worked, so I know it shouldn't have been "/media/Storage", it should have been just "Storage". D'oh.)

Many thanks in advance! :)

---

### Post by pietjanjaap on 2008-04-27
Install this "pysdm"
This is a grafical mounter, after install see, system,administration,storage device manager

---

### Post by dorkdork777 on 2008-04-27
Strange... I can't see it there, so I can't mount it. I'm going to reboot into Kubuntu, and see if that gets a different result...

EDIT: Just tried it in Kubuntu, and it works fine, so the data isn't corrupt. I just can't mount it in Ubuntu.

---

### Post by dorkdork777 on 2008-04-28
bump

---

### Post by darco on 2008-04-28
> **pietjanjaap said:**
> Install this "pysdm"
This is a grafical mounter, after install see, system,administration,storage device manager

Sweet...I had this exact problem...installing pysdm did the trick. I changed the options to "default", all is good!!

thxs
darco

---

### Post by dorkdork777 on 2008-04-28
I've still got the same problem - it doesn't even show up in pysdm. I think I just need the Terminal command to set the default mount point for an NTFS drive - "sda3".

---

### Post by Zimmer on 2008-04-28
Have a look in etc/fstab  and see what the system is trying to mount at boot.
Could be you need to edit the line in there (if right clicking on your partition has changed fstab with invalid characters in the mount string )

---

### Post by Zimmer on 2008-04-28
Have a look in etc/fstab  and see what the system is trying to mount at boot.
Could be you need to edit the line in there (if right clicking on your partition has changed fstab with invalid characters in the mount string )

---

### Post by dorkdork777 on 2008-04-28
It doesn't get mounted at boot; only the swap, home and Ubuntu partitions do. Here's my fstab.
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=c5bd54bb-8580-4001-a5d2-bb77174c0522 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=246b1051-1eac-45b0-8007-51e5aab5c440 /home           ext3    relatime        0       2
# /dev/sda2
UUID=690ebf12-ea40-55a5-de64-447a78c63e30 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


Thanks a lot, BTW!

---

### Post by amorangi on 2008-04-29
Thanks, sudo pysdm works. However that original dialogue is a very bad one - there's nothing that says the mount point shouldn't have a / and once you've made this mistake the error message gives no indication how to fix the problem. This is exactly the type of thing that make linux unfriendly.

---

### Post by toolchest on 2008-05-03
Had this issue with gutsy and tried a lot of different suggestions but nothing worked so I upgraded to hardy.  Unfortunately the problem persisted until I installed pysdm.  Thanks for the tip.

---

### Post by dorkdork777 on 2008-05-03
Please, it's not showing up! The one I want to change the mount point of is sda3 - and it's not showing up.

[IMG]http://i71.photobucket.com/albums/i154/dorkdork777/nosda3.png[/IMG]

Please - any suggestions? :(

---

### Post by Zimmer on 2008-05-03
So, it doesn't get mounted a t boot. How did you mount it in the first place? 

I reason that as it is one of your partitions it 'could' have originally been mounted at boot, until you right clicked and adjusted it!   I (a Dapper User) have tried right clicking on partitions but can find no way of altering the mount point from there.. so how did you manage that? I am curious as to 'where' you right clicked....

Anyhow, if you did not mount the drive manually when starting Ubuntu then it should have had an entry in fstab...... which may now be missing. So, a potential solution is to create a correct entry for it there. That will involve, I believe, hunting down the UUID  for it (something I have never done as DApper does not use that feature) but I have seen posts/articles somewhere that do it.  And in Kubuntu you may have a way of getting that info easily.....  hope that helps.
type the following in a terminal.
 ls -l /dev/disk/by-uuid

---

### Post by dorkdork777 on 2008-05-03
Hi, thanks for your reply!

Gutsy mounted it at boot, but when I wiped my Gutsy partition and installed Hardy (I prefer a fresh start) it was no longer mounted at boot, but it still showed up in the Places menu, and I mounted it when I needed it from there. That was how I mounted it to change the mount point.

I've also installed the 'kde4' package on my Ubuntu partition - and I can mount it perfectly fine from that, as well as my dedicated Kubuntu partition. I just can't mount it from GNOME.

I think editing my fstab might work (I have a backup should I need it). Here's my fdisk -l:
> 
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x493936ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9891    79449426    7  HPFS/NTFS
/dev/sda2           30275       30401     1020127+  82  Linux swap / Solaris
/dev/sda3            9892       23659   110591460    7  HPFS/NTFS
/dev/sda4           23660       28627    39905460    5  Extended
/dev/sda5           23660       25300    13181301   83  Linux
/dev/sda6           25301       27290    15984643+  83  Linux
/dev/sda7           27291       28627    10739421   83  Linux

Partition table entries are not in disk order


And my current fstab:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=c5bd54bb-8580-4001-a5d2-bb77174c0522 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=246b1051-1eac-45b0-8007-51e5aab5c440 /home           ext3    relatime        0       2
# /dev/sda2
UUID=690ebf12-ea40-55a5-de64-447a78c63e30 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Note that all partitions without an important mount point (like / or /home) don't show up.

I'm guessing I'll need the UUIDs, though...

EDIT: Just found a post saying they're not too important, and they can be left out. I tried changing the fstab myself, but with no result. So how should I change it to mount sda3 as... well, anything?

Or is editing fstab not the answer at all?

---

### Post by dorkdork777 on 2008-05-04
It's OK, thanks to everyone for their help! I found and followed a guide dating back to 5.10 [here]("https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html"). I ran -
 
> 
sudo mkdir /media/windows
sudo mount /dev/sda3 /media/windows/ -t ntfs -o umask=0222


That mounted it fine, and I was then able to change the mount point. Afterwards, I was unable to unmount it from Nautilus, so I ran - 
> 
sudo umount /media/windows

Then, I mounted it from Places, and it worked! Thanks again to everyone! :)

---

### Post by Zimmer on 2008-05-04
Well Done. 
Don't forget to use the thread tools to mark it SOLVED.. helps others looking for similar answers when searching the forums..

---

### Post by dorkdork777 on 2008-05-04
I can't see it, amd by the looks of [this thread]("http://ubuntuforums.org/showthread.php?t=766298") it still needs to be re-implemented. I'll mark it when the option is there.

---

### Post by DaddyX3 on 2008-05-04
SO does it mount automatically everytime you boot now? or do you still need some assistance with your fstab to get it to boot everytime?

---

### Post by dorkdork777 on 2008-05-04
It's no hassle to click on it in Places to mount it, so I'm fine, but thanks for the offer. :) Never before on forums have I been offered more help once the case is solved; the amazing community is half of what made me switch to Ubuntu rather than any other Linux distro. :D

---

