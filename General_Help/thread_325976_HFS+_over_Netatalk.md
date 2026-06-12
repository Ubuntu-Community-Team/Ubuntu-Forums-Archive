---
title: "HFS+ over Netatalk"
date: 2006-12-26
forum: General Help
---

### Post by tburgund on 2006-12-26
Hey,
Merry Christmas All!
The problem is (sorry on my english):
I have headless ubuntu desktop PC acting as home server (mt-daapd, backup etc)
I had everything working (file sharing over netatalk to my iBook and MacBookPro) until i experienced power loss on ubuntu machine. 
Here are the facts:
Ubuntu desktop has 2 Hard drives: first (20Gb) is only system, second has two partitions (FAT32 and HFS+ not journaled). 
On my MBP i can remotely:
listen to my music over mt-daapd on HFS+ partition, 
ssh to headless ubuntu and browse FAT32 and HFS+ partitions
connect to server over afp: (i can see two partitions)
mount FAT32 partition
can&#8217;t mount HFS+ partition any more (I could before power loss?)
I would appreciate any kind of help here.

---

### Post by kidders on 2006-12-26
Hi there,

It's been a while since I've used netatalk, so I can't remember if it keeps independent log files, but either way, you should be able to use your system logs to diagnose your problem.

I would suggest finding a potentially useful log file (maybe /var/log/messages), and doing something like **tail -n 0 -f /var/log/whatever**. Then, try connecting to your fileshare again, and see what messages pop up. It's also possible (but not likely) that your MacBook's logs may have something useful in them.

With luck, your logs will spit out lots of bad things ... that means we can fix it! :-)

**Edit:** Incidentally, your English is perfect.

---

### Post by wgscott on 2006-12-26
I've sometimes had to reboot my OS X computers under similar circumstances in order to get them to "rediscover" NFS exports that I want them to mount.  The automounter in OS X is kind of buggy.  Also, try (temporarily) turning off your firewall (either in System Preferences or issue sudo ipfw flush ).

---

### Post by kidders on 2006-12-26
Hey again,

I figured I should add something I forgot to mention before...

Afaik Apple fileshares are announced via mDNS, so while you're poking around system logs on your Mac or your Linux box, you might want to keep an eye out for errors involving the various incarnations of multicast DNS (zeroconf, avahi, mDNSResponder, bonjour, etc.). mt-daapd includes an mDNS daemon ... I wonder what would happen if you switched it off temporarily ... maybe netatalk might be more cooperative. :-k 

Also, have you fsck'd your HFS filesystems since your little power accident? Since you disabled your HFS journals (presumably so Linux would be happier about writing), they will no doubt be more prone to corruption. :-(

If you *have* checked your filesystems for errors, may I suggest removing any Mac-related data forks anyway. It's possible (but not likely) that a corruption in one of them (that may have been written out completely), could be giving you problems. Something _like_ this would do ...

1. Tar them up, so you can put them back.
**tar cvf dotfiles.tar $(find /path/to/share -name ".DS_Store" -or -name "._*")**

2. Delete them all.
**find /path/to/share -name ".DS_Store" -or -name "._*" -exec rm {} \;**

3. Try to mount a share again.
**(CMD+K, etc. on your Mac)**

4. If the share still won't mount, put your dotfiles back, so your Finder preferences don't get lost.
**tar xvf dotfiles.tar**

---

### Post by tburgund on 2006-12-27
> **kidders said:**
> 
Also, have you fsck'd your HFS filesystems since your little power accident? Since you disabled your HFS journals (presumably so Linux would be happier about writing), they will no doubt be more prone to corruption. :-(

Hello again!
Here is output after fsck.hfsplus:

** /dev/hdc2
** Checking HFS Plus volume.
** Checking Extents Overflow file.
** Checking Catalog file.
** Checking Catalog hierarchy.
** Checking volume bitmap.
** Checking volume information.
   Volume Header needs minor repair
** Repairing volume.
** Rechecking volume.
** Checking HFS Plus volume.
** Checking Extents Overflow file.
** Checking Catalog file.
** Checking Catalog hierarchy.
** Checking volume bitmap.
** Checking volume information.
   Volume Header needs minor repair
** Repairing volume.
** The volume OSX could not be repaired.

How "minor" is this repair and how to do it?
While searching this forum I realized that the problem could be the mounting of the HFS+ partition on the Ubuntu machine. If I umount HFS+ partition on Ubuntu machine (automatically mounted from fstab) and mount it again manually with:
sudo mount -t /dev/hdc2 /mnt/osx
everything works fine so I guess the problem is my fstab.
Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc1       /mnt/win/    vfat iocharset=utf8,umask=000       0       0
/dev/hdc2       /mnt/osx/     hfsplus auto,rw,umask=000      0       0

Thank You for Your help so far.
What could be the problem with my fstab.

---

### Post by kidders on 2006-12-27
> **tburgund said:**
> How "minor" is this repair and how to do it?
There are probably some inconsistencies relating to unflushed buffers and incomplete I/O operations ... minor enough. You may, of course, also find that whatever you were doing with the filesystem at the time of the power loss may be incomplete, but there's not a whole lot you can do about that. HFS is quite a resilliant filesystem, so you shouldn't need to worry too much.

I wonder why the "volume OSX could not be repaired". Was it mounted when you did the check? (It shouldn't be ... repairing mounted filesystems can be disasterous.)

> **tburgund said:**
> sudo mount -t /dev/hdc2 /mnt/osxThat command shouldn't succeed, which is perhaps (in a way) the reason it appears to solve your problems. "/dev/hdc2" is not a valid filesystem type ("-t"), so the mount should fail, I think. :-k 

Your /etc/fstab seems fine, although setting a umask of 000 is an odd thing to do. It means that everything created on that filesystem, no matter by whom, is world-writable by default.

---

### Post by tburgund on 2006-12-28
> **kidders said:**
> There are probably some inconsistencies relating to unflushed buffers and incomplete I/O operations ... minor enough. You may, of course, also find that whatever you were doing with the filesystem at the time of the power loss may be incomplete, but there's not a whole lot you can do about that. HFS is quite a resilliant filesystem, so you shouldn't need to worry too much.

I wonder why the "volume OSX could not be repaired". Was it mounted when you did the check? (It shouldn't be ... repairing mounted filesystems can be disasterous.)

](*,) Oops. I umonted it and fscked it so the output is:
** Checking HFS Plus volume.
** Checking Extents Overflow file.
** Checking Catalog file.
** Checking Catalog hierarchy.
** Checking volume bitmap.
** Checking volume information.
   Invalid volume free block count
   (It should be 41002208 instead of 41001690)
   Invalid file clump size
   (It should be 1048576 instead of 0)
   Volume Header needs minor repair
(2, 0)
** Repairing volume.
** Rechecking volume.
** Checking HFS Plus volume.
** Checking Extents Overflow file.
** Checking Catalog file.
** Checking Catalog hierarchy.
** Checking volume bitmap.
** Checking volume information.
** The volume OSX was repaired successfully.
> **kidders said:**
> 
That command shouldn't succeed, which is perhaps (in a way) the reason it appears to solve your problems. "/dev/hdc2" is not a valid filesystem type ("-t"), so the mount should fail, I think. :-k 
Sorry about that, I forgot hfsplus (should be sudo mount -t hfsplus /dev/hdc2 /mnt/osx)](*,) :mrgreen: 
> **kidders said:**
> 
Your /etc/fstab seems fine, although setting a umask of 000 is an odd thing to do. It means that everything created on that filesystem, no matter by whom, is world-writable by default.
So should I remove umask=000?:confused: 
Thanks

---

### Post by kidders on 2006-12-28
Yay! So has that fix corrected your problems? (It almost looks *too* minor to me!)

> So should I remove umask=000?Emm... well... removing it would change the behaviour of your filesystem, so it depends on what you want. I only mentioned it out of curiosity, since it would be considered a security issue by some people, depending on their circumstances.

---

### Post by kidders on 2006-12-28
Sorry for replying to *myself*, but it strikes me that you might maybe find the following of interest:

Since you can't journalise your HFS+ partition for compatibility reasons, you might like to explore the "sync" and "dirsync" mount options. Using them would give you added (ie not foolproof) protection against certain kinds of filesystem corruptions, were you to experience further power interruptions. There would probably be a _very_ significant performance penalty, but it is unlikely to impact I/O speed over a LAN for a small number of users, since the data rates would always be far lower than the kernel can handle anyway.

Incidentally, is there a reason you've opted for HFS+ in the first place?

I hope your filesharing issue has been solved ... post back if you're still having problems!

---

### Post by tburgund on 2006-12-28
> **kidders said:**
> Sorry for replying to *myself*, but it strikes me that you might maybe find the following of interest:

Since you can't journalise your HFS+ partition for compatibility reasons, you might like to explore the "sync" and "dirsync" mount options. Using them would give you added (ie not foolproof) protection against certain kinds of filesystem corruptions, were you to experience further power interruptions. There would probably be a _very_ significant performance penalty, but it is unlikely to impact I/O speed over a LAN for a small number of users, since the data rates would always be far lower than the kernel can handle anyway.

I will look into that.
> **kidders said:**
> 
Incidentally, is there a reason you've opted for HFS+ in the first place?
Sometimes I have to take that HD out of the Ubuntu in order to take it to work, or to a friend etc.. (OSX everywhere:D , some WinXP:confused: )
I didn't give it much thought about filesystem, just went for the HFS+??
> **kidders said:**
> 
I hope your filesharing issue has been solved ... post back if you're still having problems!
Solved.

---

