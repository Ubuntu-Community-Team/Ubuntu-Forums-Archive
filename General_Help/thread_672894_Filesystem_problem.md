---
title: "Filesystem problem"
date: 2008-01-20
forum: General Help
---

### Post by SteveLaw on 2008-01-20
Hi,

I'm new to Ubuntu/Linux so please bear with me if I can't explain this very well (or if it has already been answered somewhere, I didn't even know what to search for).

I set up a dual boot with my XP.  I orginally had the HDD partitioned roughly like:

Dell Utilities (Yes, it's a Dell PC) (fat16) - 40MB
XP (ntfs) - 60GB
Swap - 4GB
Ubuntu Filesystem (ext3) - 9GB
unallocated - 30GB
Media (ntfs) - 40GB
Dell Restore (fat32) - 4GB

Dell Utilities, XP and Dell Restore all primary partitions, 
Swap, Ubuntu, unallocated and media all logical partitions as part of the 3rd primary partition. 

I tried Ubuntu felt I could commit a little further so I thought I should expand it into the rest of the unallocated (in hind sight, perhaps a little hasty).

I looked through a few articles and then burned a copy of Parted Magic as one suggested (I may have picked the wrong one!) - resized the Ubuntu partition to fill the unallocated and rebooted.

I then got an error - can't remember the details but it told me to run fsck which I did, said yes to all fixes and everything booted fine.

However, when I now look at the filesystem partition I find that it says it is still 9GB.  If I look in GParted in Ubuntu it says the partition is around the 40 GB expected, but that it is almost full.  Looking further I find a folder called media in the root of the Filesystem partition that appears to contain every partition of the disk (including CDROMS), thus:

cdrom
cdrom0
cdrom1
sda1
sda2
sda4
sda5
sdb1
sdb2
sdb3

if I go into sdb2, for example, if takes me to the Media partition. sda2 - the XP partition, etc.

Help!  What's going on?  Can I (*ahem* you...) fix this?  Have I broken it completely? Do I have to start again?

Thanks!

---

### Post by jnorthr on 2008-01-20
Steve - how many hard drives are in your system ?  my understanding is that sda... would be one drive and sdb... would be another drive.  My approach would be to burn a copy of gparted to cd and use it stand-alone to play with partitions as it has been suggested elsewhere that using gparted WITHIN ubuntu may have issues with permissions/authorities. I would take a backup of your important stuff first - just in case - cos you never know, then delete the media, swap and ubuntu partitions. Reboot and confirm xp still boots ok  or not.
 
If not then your backups will become critical - you do have them don't you ?

If xp does boot then i'd try to use the stand-alone gparted again to do your /swap and / root and /home partitions from the room available. Maybe leave a little room for a fat or fat32 partition cos both xp and ubuntu can read/write to them. for what it's worth ... =;

---

### Post by SteveLaw on 2008-01-20
Hi jnorthr,

Two disks.

(Correction to original post)

sda are on the the first disk, sdb the second. (only the ntfs partitions)

Media is not on the first disk as in my original post, but the second, where it says media it should be Virtual - not that it matters hugely, but I may have caused extra confusion.

(end of correction)

XP and Ubuntu both work fine, the only issue is the disk space/weird mounting problem (if that's what it is).

I did run Gparted as a live CD (Parted Magic) not within Ubuntu, I only installed and ran Gparted within Ubuntu to see what was going on without having to reboot (all partitions are locked so I couldn't change them within Ubuntu even if I wanted to).

I'm currently using the NTFS partitions for sharing between the two as Ubuntu seems to handle them with no problems, so I don't really see any need for a fat partition (but that's a different discussion :) ).

Backups not a worry either I have a recent backup of XP, and I have no data to speak of in Ubuntu yet.  However, I've spent some time faffing on with installations (including a minor nightmare when I fitted an ATI card I ordered before I went Ubuntu and learned it wasn't too keen on it) so I'm trying to avoid a wipe/reinstall, but if I have to, I have to - puts you off a bit committing to Linux though...).

---

### Post by heatblazer on 2008-01-20
Why don`t you try to install the NTFS onfiguration Tools? It may do something :)

---

### Post by SteveLaw on 2008-01-20
They were already installed.

---

### Post by SteveLaw on 2008-01-20
I can umount them all from "init 1" so the mounted partitions are not displayed but the media folder still exists with them all inside - if I go into each folder (e.g. sda1) then nothing is listed, even though Gparted still says it is still 90% used (about 37GB), but the properties of the file system partition says 5.7GB used.

Then, when I reboot they are back again (I actually want them mounted of course, just not linked to my File System partition via this media folder however that is happening).

---

### Post by SteveLaw on 2008-01-20
I've done a little searching and the mountpoint thing (/media/) may not be unsual so it may be something of a red herring.  (Although is it normal for /media to think it is 100GB in size (if that is how big the contents of the mounted partitions are?) - this mounting thing just isn't making sense to me yet...


The REAL problem I want to solve (I think) is why the File System partition still thinks it is 9GB when it should be 40GB.

---

### Post by SteveLaw on 2008-01-22
Okay, never mind, it was obviously one of those weird ones - I flattened it and started again.  Triple check my sources from now on...

Thanks anyway for those who tried to help.

---

