---
title: "Moving home partition to a shared FAT32"
date: 2007-05-26
forum: General Help
---

### Post by Scruffynerf on 2007-05-26
Hi all,

I run a WinXP Hpome and Edgy Eft Dualboot. I also have 2 physical IDE HDD's, one 120Gb (Primary) partitioned into a NTFS / Ext3 / Linuxswap. This is all well and good. Windows can see and read to & from the linux partitions, and vice versa.

I also have a secondary 320 GB HDD, partitioned equally between NTFS & Ext3. This drive is my storage drive, and contains  my home partition.

 I set this up when I was a very new user. I'm now less new, and have decided that I'd like to mix things up a bit to make life easier.

 What I'm thinking is that I'd like to essentially reformat that drive to 300GB of FAT32, as both systems support it natively, and it is essentially a common resource. Id also probably keep 20Gb as ext3 in order to play around with other linux distro's just to test them out (Is this enough?)

I have access to a powerful drive management system (Acronis Disk Director) that I'm intending to use to do this (via windows (i'm more confident of this in windows))

Here's what I am thinking:

1) Boot into windows
2) Copy/zip existing files from NTFS partition to somewhere (i'll probably borrow an external HDD for this.)
3) Reformat NTFS to FAT32
4) Essentially reverse step 2 onto the fat32
5) Copy the files from the ext3 over to the new fat32 area (should fit.)
6) Delete the Ext3 partition
7) Extend the FAT32 to mostly cover where the Ext3 was, leaving about 20GB.
8) From my limited understanding, I think that I need to somehow edit the fstab file, wherever it lives, so it points back to the new large FAT32 partition.
9) Going back into Linux, format the 20GB back to ext3 for playing with linux distro's
now, some questions:

a) FAT32 filesystems frag horribly. If I defrag the drive in windows, will it corrupt the linux files?
b) Is 20GB buried at the back of a secondary hard drive enough for testing linux distro's on average?
c) Are there any common problems that I need to watch out for?
d) Editing the fstab - how exactly?

e) Estimated chance of fouling this up completely?

I do not want to install again. I've spend a lot of time customising my linux istall, and don't want to have to re-install again.

many thanks for your time and responses.

---

### Post by rillip on 2007-05-26
Editing fstab is easy.  It's in /etc/fstab.  

sudo nano /etc/fstab 

will put you in there. You can use vi or hell, Kate, whatever you like, you just have to run it as super user.  It's pretty obvious what you need to do there too.  Here's my fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda3 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid $
/dev/hdd /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda3 <mount\040point> swap defaults 0 0
/dev/sda1 /mnt/storage ext3 nouser,uid=1000,gid=1000,atime,auto,rw,dev,exec,sui$
/dev/sda2 /mnt/shared vfat uid=1000,gid=1000,auto,rw,nouser,quiet 0 0

You can see it's all of the form /device /location type uid= gid= and then some other items you can pretty much copy and paste from a similar parition.

Alternatively, there is a gui interface for this.  I don't know where it is in Gnome, but in KDE simply got to system settings -> disk and file systems and you can do it all from there with simple mouse clicks and menus.

The proposal you have makes sense, but I can't address your concerns about fragmentation.  Additionally, keep in mind there are limits on the max size of files in fat32.  Not sure what the limit is right off the top of my head, but it wasn't unconceivable, 4gig maybe?

Edit: I review my drive after this post for something else and found my / is less than 4 gigs.  If you're just going to be playing with one distro at a time, or maybe two at the most, 20 gb seems fine.  You'll likely want it to have its own home directory, so you don't mess up your settings, so keep that in mind.  The more you use the distro, the more space you'll need, but you'll have all that lovely 300 to put real data in, so it's just the app config files you'll acrew.  20gb seems fine for up two two, three at the most I would say.

I'm not aware of any specific issues you'll face, but it's always good to keep a backup, just in case.  It can be difficult to get your drives remounted, as sometimes the patition will change numbers and your old settings will cause conflicts with the new names/sizes/types, but this can all be sorted out by unmounting everything and getting it remounted, almost all of which can be done through the gui or manual fstab editing.

---

### Post by Scruffynerf on 2007-05-26
cheers.

Any other opinions out there?

Hmm.. FAT32 can't support files over 4GB? Wonder why that is... I've some 8+GB files sitting around. Backups and .iso files mainly

---

