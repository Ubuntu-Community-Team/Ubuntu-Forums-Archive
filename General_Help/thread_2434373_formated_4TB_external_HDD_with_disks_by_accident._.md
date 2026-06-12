---
title: "formated 4TB external HDD with disks by accident. Possible to recover?"
date: 2020-01-04
forum: General Help
---

### Post by stupidman on 2020-01-04
Stupid sleepy mistake of mine, formatted by accident a 4TBdrive containing important files to me.
Now I have a ready to use, empty, 4TB drive...
I'm new to Linux but fro searches testdisk seems to be the way to go for this. A quick partition search returned only the current empty one. Doing a Deep Search as I type this, but not too hopeful...

I could go out and byy another 4 TB drive and try to do file recovery instead of partition.

Any suggestions?

Thanks. So mad... at me...

The format was done in POP_OS! Gnome Disk Utility name Disks.

---

### Post by TheFu on 2020-01-04
Can you just restore from backups?

---

### Post by stupidman on 2020-01-04
No, I immigrated and this is a backup of my files back home, so while most exist somewhere else I won't have access to them for a long time.
There are also a few new files I backed up into the drive from the past months.

I'm in the middle of trying distros and get my laptop up and running and instead of formatting a pen drive I did it on the archive drive.

---

### Post by dragonfly41 on 2020-01-04
> [COLOR=#000000]I could go out and by another 4 TB drive and try to do file recovery instead of partition.[/COLOR]

I fear that you will need to do this anyway since you need another similar size device into which you can save any recovered files.
Otherwise recovered files just overwrite the drive you hope to recover!

I would use Gparted on a LiveUSB to select any drive and then create partitions and format.  Hopefully less chance of errors.
Also in GParted under toolbar > Device there is an option Attempt Data Rescue.

Another tool associated with TestDisk is Photorec.  But as I explained you must get some device to receive your hopefully recovered files. This second device can always be used as your future backup device so it is a necessary purchase. I have recently invested in buying a StarTech dual docking station for external docking of dual SSD's or drives. This docking station would be handy for a laptop but requires USB 3.0 port for fast data exchange. See post#5 [here ]("https://ubuntuforums.org/showthread.php?t=2433815&highlight=startech")where I give links to the device specs.

---

### Post by oldfred on 2020-01-04
If testdisk deeper search finds files, copy them to new 4TB drive, before anything else.
Do not format or do anything to 4TB drive until testdisk shows nothing. And then photorec may find files.
What format was partition? Was it all one very large partition.

Does this show anything as 4TB drive should be gpt partitioned, although some external drives use proprietary configuration for compatibility with XP which did not support gpt. I would expect disks to also have erased backup partition table.

sudo gdisk -l /dev/sdX where sdX is sdb or whatever 4TB drive is.

---

### Post by stupidman on 2020-01-04
Thanks guys.
Going to buy a 5TB Seagate while R-Studio scans the drive.
Will report after the task is done.

---

### Post by TheFu on 2020-01-04
I wouldn't buy a Seagate less than 8TB in size.  Their smaller drives have a history of quality issues, especially the odd-sized ones, like 3TB and 5TB, though the 2, 4, 6TB versions also had quality issues.  Check out the reliability reports from backblaze for the statistics.

Can't you have someone snailmail the original disk?  That would be faster, less hassle and you could replace theirs with a new disk.  I've mailed HDDs halfway across the planet overnight using DHL/FedEx and usually arrive within 30 hrs or so.  If the data isn't encrypted, expect customs to take a look. kurt18947 has the right idea below, though cloning 4TB will usually take about 26 hrs for me.  I would definitely use LUKS encryption if given the choice, regardless of the data.

---

### Post by kurt18947 on 2020-01-04
> **TheFu said:**
> I wouldn't buy a Seagate less than 8TB in size.  Their smaller drives have a history of quality issues, especially the odd-sized ones, like 3TB and 5TB, though the 2, 4, 6TB versions also had quality issues.  Check out the reliability reports from backblaze for the statistics.

Can't you have someone snailmail the original disk?  That would be faster, less hassle and you could replace theirs with a new disk.  I've mailed HDDs halfway across the planet overnight.

Or an encrypted copy of the original files?

---

### Post by stupidman on 2020-01-05
Restored the recent months files with R-Studio and they are in working condition. Haven't noticed any work corrupted so far!:guitar:

Proceeding to recover the big old archives.


> **TheFu said:**
> I wouldn't buy a Seagate less than 8TB in size.  Their smaller drives have a history of quality issues, especially the odd-sized ones, like 3TB and 5TB, though the 2, 4, 6TB versions also had quality issues.  Check out the reliability reports from backblaze for the statistics..
I see. Well at most it means I have to immediately copy the files back to my original 4TB Western Digital once the salvage is done.

> **TheFu said:**
> 
Can't you have someone snailmail the original disk?  That would be faster, less hassle and you could replace theirs with a new disk.  I've mailed HDDs halfway across the planet overnight using DHL/FedEx and usually arrive within 30 hrs or so.  If the data isn't encrypted, expect customs to take a look. kurt18947 has the right idea below, though cloning 4TB will usually take about 26 hrs for me.  I would definitely use LUKS encryption if given the choice, regardless of the data

I could but that would also be a gamble for me in case something happened in the transportation. Also, I prefer that those to stay in another place. Plus still need recent months files recovered.

Why LUKS for encryption? Also since we are talking of file recovery is there any advantage with any encryption methods when in comes to salvage data? Would I be able to scan and recover files from a LUKS drive as long as I know the passcode? 


Also since we're talking archive drives is there any file system that will offer capabilities over the other when it comes to fast searching? I'm using NTFS because my stuff originally came from Windows and "Search Everything" from voidtools worked wonderfully to fast search files. Angry Search in Linux seems to work in similar way maybe better than FSearch, but I still wonder if for archive NTFS is the safest option especially if one might go back and forward Linux and Windows.

---

### Post by TheFu on 2020-01-05
Why LUKS?  It is built-in and very strong.  No known way to hack it, assuming you don't use trivial locking or passphrases.  The data is secure.  Using encryption means having perfect backups.  If you can't do that, then don't use encryption.  OTOH, there are many well-documented reasons FOR using encryption.  Chiefly to me is being able to get HDD warranty service without worrying that the vendor will ever have access to the data.  All portable devices, including USB storage must be encrypted, period.  Phones, tablets, laptops, and any storage that a single human can grab with 1 hand.

Yes, that "1-hand" rule is contrived.  

The main problem with NTFS is that it doesn't support Linux permissions which is critical.  It lacks advanced file system capabilities without add-on products that cause issues for Linux+Windows+OSX access.  Just because Windows needs access, that doesn't mean NTFS is required.  NTFS is only required if the drive will be physically connected to a Windows machine. Network access to the storage does not need NTFS.  Samba works best with native Linux file systems.

As for searching, that is just you being new.  There are plenty of excellent search options on Unix.  Google runs on Linux.  Is that good enough?  You can make your own google-like search tool.  Find, locate, recoll, beagle, and probably 10 others.  These forums have some information about each.  The Linux Journal had a few articles on how to index anything which is used for searches.  You can build your own putting together a few small tools.  This is the Unix way.  If you don't want that customization, recoll works well.

---

### Post by dragonfly41 on 2020-01-05
[COLOR=#000000]> Restored the recent months files with R-Studio

Do you mean R-Linux and not R-Studio?   R-Linux I have used for data recovery.[/COLOR]

---

