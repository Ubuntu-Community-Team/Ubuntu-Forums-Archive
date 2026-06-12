---
title: "NTFS-3G, FUSE, &amp; NTFS Config installed but not working (7.04)"
date: 2007-04-16
forum: General Help
---

### Post by teastman on 2007-04-16
Hi folks.

I originally posted this to the Kubuntu Feisty forum but It's not necessarily a Kubuntu issue and I need an answer relatively soon.  Hope this is ok in the General area.

I'm still having problems getting to where I can read and write to my ntfs partitions (and external ntfs formatted disks).

Checking in my Adept- Manager NTFS-3G and FASE are installed as well as the NTFS-Configuration tool.



FSTAB looks like this - notice no mention of ntfs;
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=60e0cd3f-d84c-4c9f-8e60-9224aeda1464 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=63858b37-3c50-42b2-bd07-f243ddca2fbb /boot           ext3    defaults        0       2
# /dev/hda5
UUID=b8269c38-21be-4f9e-9e27-4b73ad708242 /home           ext3    defaults        0       2
# /dev/hda6
UUID=07578e17-0c27-4513-879b-0f3a0df4b6f4 /media/hda6     ext3    defaults        0       2
# /dev/hda2
UUID=02db224f-bb0d-497c-8e87-3635d0966587 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

#end of file [my edit]

You might notice my hda4 partition is missing. My dev/hda4 partition is actually an extended partition with hda5&6 as logical partitions in it.  Reason being my GParted-Clonezilla (1.7) can't handle more than 4 primary partitions.

Going to my KMenu>System>NTFS Configuration Tool has no icon next to it (which indicates it's not installed?).  Clicking that "NTFS Configuration Tool" does absolutely nothing - no panel , no banner - no spinning hourglass - nothing.

My confusion in all this - The very first time I installed 7.04 last week Tues(?) I also installed ntfs-3g through the Add/Remove programs and it took right off after I ran the "NTFS Configuration Tool" reading and writing to my ntfs partitions and USB devices.

Now the system tells me those three packages are installed but nothing takes off. No NTFS drives or external disks are available in the "Storage Media".

Just as a BTW I have had to re-install but for other reasons - when I have reinstalled my system this week (7.04) I have formatted my ext3 partitions during installation to ensure no "leftover" files which were earlier "broken" (by me) would be laying about so it was a clean re-install.

I am not real proficient at Linux yet. I'm a bit of a greenhorn with this.

Should I go through Adept Manager and uninstall those three programs and then re-install them through a konsole?

Is there another file you guys would need me to post as a troubleshoot?

Thanks
Tim

---

### Post by lotacus on 2007-04-16
try issuing the command **sudo fdisk -l** and note where your NTFS partition is located.
For example, mine looks like this:

[SIZE="1"]   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3627    29133846   83  Linux
/dev/sda2            3628       12160    68541322+   f  W95 Ext'd (LBA)
/dev/sda5            3786       12160    67270656    7  HPFS/NTFS
/dev/sda6            3628        3785     1269072   82  Linux swap / Solaris
[/SIZE]

In my case, my NTFS partition is /dev/sda5.

In your fstab file, it should be safe to replace the guid with /dev/sda* or hda* depending how your installation recognizes the drives. (sata or pata). Always make a backup before modifying though. **sudo cp /etc/fstab /etc/fstab.bak**

Find your ntfs partition(s) and add them into you fstab file. so it looks similar to this:

[SIZE="1"]proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=af993e1a-db8c-4d02-9424-8da74bf5247a / ext3 defaults,errors=remount-ro,data=writeback,noatime 0 1
/dev/sda6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
**/dev/sda5 /media/sda5 ntfs nls=utf8,rw,umask=000 0 0**[/SIZE]

You will have to replace the word ntfs with ntfs-3g. umask=000 basically means all users have access to the partition, and the rw which I got from a guide allows read/write. However, I must tell you that I have NEVER been able to write to my ntfs drive using the kernel's ntfs driver or using ntfs-3G, excluding the very first time I installed Edgy. I always get a permission denied because I don't have writes to view the contents. (that's when it's mounted -rw)

Anyways, I suspect your NTFS-3G package is broken. You may want to recompile the kernel (if it's necessary) or completely remove ntfs-3g and try reinstalling it from it's home CVS location and NOT the repositories, since most of the repo's can be well dated.

---

### Post by teastman on 2007-04-16
Thanks Lotacus - I'll try that tonight.

Tim

---

### Post by thesphine on 2007-04-17
I've got ntfs-3g working like a charm and have done since dapper.

The line in my fstab under feisty looks like this:

UUID=AAB80529B804F61B /NTFS/CDrive ntfs-3g defaults,locale=en_US.utf8 0 0

The format changed going from Dapper to Edgy (which I've just noticed :) 

Make sure you've got version 1.328 of ntfs-3g if you're planning on writing large files to fairly full/fragmented disks.

---

### Post by chakkaradeep on 2007-04-17
Well, People ignore [Automatix2]("http://getautomatix.com") a lot !

I installed ntfs support via Automatix2 and it just worked out of the box in Feisty :guitar:

---

### Post by lotacus on 2007-04-18
heh. not for me. I dont' know what went wrong, but I got the filesystem is dirty message and there was no work around for me even though there ARE work arounds, neither did the trick. I still don't have write support after "cleaning" with ntfstools and forcing -rw as what is in my fstab. Don't even have write support when using root. I suppose my only option is to completely destry the NTFS partition after backing up the files I need.

---

