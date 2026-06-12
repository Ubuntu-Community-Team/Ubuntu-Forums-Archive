---
title: "[SOLVED] Access 2nd hard drive after reinstall"
date: 2007-06-28
forum: General Help
---

### Post by Derspankster on 2007-06-28
For a variety of reasons, I recently did a fresh reinstall of Feisty.  My system disk is 80 GB and I have a second disk that is 160 GB and is partitioned in two 80 GB partitions.  I have been using this machine as a music server among other things. However, now I can only manually mount my second hard drive and nothing is accessible from this machine on my network.  The 2 partitions on the 160 GB disk manually mount as disk and disk-1.  I know that I need to create some mount points for the 2nd drive again and probably permissions need to be changed and my fstab file modified.  Not to mention the need for configuring Samba.  I'm not sure where to start to tell you the truth. I kind of wish I'd never done the reinstall. Ubuntu is light years behind Windows when it comes to handling hard drives. But, I still like Ubuntu a lot.  What I'm looking for is a little direction here - where to start. Below is my fstab.   


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=62fc2d7a-3894-4328-8619-e1a2899064f7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=b5cdad0a-58bd-45e8-9e72-e3712745dea5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by 1ballistic1 on 2007-06-28
If you've already partitioned, you should already have another partition ready that Ubuntu can mount.  You need to add another line in fstab, something like this:
/dev/hdb  /media/hdb    vfat      auto   0 0


Some of it is going to change a bit: 
If the drive is an IDE drive, it will be something like /dev/hdb , depending if it was detected before or after the CD drive.  If it's a SCSI/USB/SATA drive, it's more likely to look like /dev/sdb

If it's formatted using a FAT variant( FAT,FAT32), vfat will be the option to choose.  If it's NTFS, you would use ntfs-3g  (note that you will also need to install ntfs-3g (in Terminal, type: sudo apt-get install ntfs-3g)

If  you still have questions, post back with more details.

---

### Post by Derspankster on 2007-06-28
> **1ballistic1 said:**
> If you've already partitioned, you should already have another partition ready that Ubuntu can mount.  You need to add another line in fstab, something like this:
/dev/hdb  /media/hdb    vfat      auto   0 0


Some of it is going to change a bit: 
If the drive is an IDE drive, it will be something like /dev/hdb , depending if it was detected before or after the CD drive.  If it's a SCSI/USB/SATA drive, it's more likely to look like /dev/sdb

If it's formatted using a FAT variant( FAT,FAT32), vfat will be the option to choose.  If it's NTFS, you would use ntfs-3g  (note that you will also need to install ntfs-3g (in Terminal, type: sudo apt-get install ntfs-3g)

If  you still have questions, post back with more details.

Thanks for replying!  Yes, it's already formatted into two partitions.  It's ext3.  The two partitions show up as disk and disk-1 respectively and I can mount them manually. I want to be able to mount them automatically as Music and Photos.  The old mount point was Music mp3 and there's a folder on disk with that name. Likewise, there's a folder on disk-1 with the name Photo.  As you can probably tell, I'm somewhat of a noob as I bounce around through Linux, Windows and my Mac. Almost all my experience has been with Windows. I had all of this working before the reinstall.  When I tried to add a line to my fstab to mount disk the drive disappeared totally.  I'm afraid I'm so caught up my underwear I don't know what to do next.  Should I try adding a line to fstab like this?

/dev/hdb  /media/hdb    ext3      auto   0 0

---

### Post by Derspankster on 2007-06-28
I went ahead and added the line:  [COLOR="Red"]/dev/hdb /media/hdb ext3 auto 0 0[/COLOR]   to my fstab and it made no difference. I still have to mount the drives manually. I can access all the files on the two partitions that way but I want to be able to mount them automatically and then be able to join my home network and have them accessible to all computers on the network. Of course, that's the second part of my problem, reconfiguring Samba.

---

### Post by confused57 on 2007-06-28
Here's an excellent guide for mounting various filesystems, including ext3:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by Derspankster on 2007-06-29
Well, it's nice tutorial and I was able to create a mount point but it points to nothing. I still can only manually mount the partitions of my second drive  using my system password.  Any attempt to add the partitions to fstab results to the partitions being invisible upon reboot.  I'm looking at the new Windows Home Server, sorry to say.

---

### Post by 1ballistic1 on 2007-06-29
I was having the same issues recently....I ended up having to add the same line to /etc/mtab manually because it was doing the same thing...it worked for me...

---

### Post by Derspankster on 2007-06-29
> **1ballistic1 said:**
> I was having the same issues recently....I ended up having to add the same line to /etc/mtab manually because it was doing the same thing...it worked for me...


Really?  Never even heard of mtab.  No reason for me not to try it. Thanks!

---

### Post by Derspankster on 2007-06-29
> **1ballistic1 said:**
> I was having the same issues recently....I ended up having to add the same line to /etc/mtab manually because it was doing the same thing...it worked for me...


Well, it didn't work - drives are gone again.

---

### Post by Derspankster on 2007-06-29
You know, the real problem with Linux is that there's just about 3 people in the whole world who really know what's going on  - and they're not talking!   I mean no offense to you 1ballistic1, you have been doing your best to help.

---

### Post by Derspankster on 2007-07-01
OK, all kidding aside, and thanks to 1ballistic1 for his guidance and confused57 for his excellent link. I have successfully mounted both partitions of my second hard drive. Even though I went through that once, apparently being somewhat of senior citizen the methodology had completely escaped me. Believe me, I've saved the links this time around.  I do have another question though, before I move on to reconfiguring Samba for network accessibility. 

Both partitions that I recently mounted now show up on my desktop as well in my Computer folder.  I've not seen that before. The desktop links, that is.  What gives with that?

---

### Post by 1ballistic1 on 2007-07-01
Noticed that start with 6.10....no Home shortcut anymore though...

---

### Post by Derspankster on 2007-07-01
> **1ballistic1 said:**
> Noticed that start with 6.10....no Home shortcut anymore though...

Must not have seen that since I did upgrades from Dapper to Edgy and then Feisty before I did the complete fresh reinstall of Feisty.

---

### Post by Derspankster on 2007-07-03
Wanted to mention that this is resolved. Thanks to all. Not sure why the mounted partitions are on my desktop but I guess that's OK.

---

