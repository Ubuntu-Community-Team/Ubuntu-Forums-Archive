---
title: "Convert NTFS to FAT32 with Partiton Magic"
date: 2005-09-11
forum: General Help
---

### Post by BoomShake007 on 2005-09-11
Ok, i'm trying to convert two of my ntfs partitons to fat32 so both windows and linux can read/write.  My current setup is like this:

20GB NTFS - XP Pro installed here
10GB NTFS - Personal documents, etc
75GB NTFS - Media storage
512MB SWAP - ubuntu swap
100MB EXT3 - ubuntu boot files
13.4GB EXT3 - ubuntu files (/home directory, etc.)

Dual boot works fine, everything is dandy.  However, it's a real pain in the butt to have to reboot into each to modify files in the other.   I got something for windows that lets it see the EXT3 partitions, and supposedly write.  I can see the NTFS partitions in Ubuntu, no write.  I figure, making my Personal Docs and Media storage into FAT32, it would eliminate most of my problems and make things significantly easier.

I then fired up Partition Magic 8.0, selected the personal documents one to start.  Clicked "Convert"-->"FAT32".  It added it to the tasks, then I hit "apply".  It started to work a bit, then gave me an error.  Basically, it said I have a file over 4GB in directory 5 on that partition.  Confused, i looked around, searched with the search feature in windows for anything over even 1GB on that drive.  Nothing.  When it rebooted to do the media drive, it seemed to work, but when it finsihed, rebooted, adn went back to windows, it still was NTFS.  The biggest file on that is a little over 2GB.  I know for a fact that I have nothing even close to 4GB on either partition.

So, what should I do?  Is there any way that I can get around this?

---

### Post by nemin on 2005-09-11
[QUOTE=BoomShake007]Ok, i'm trying to convert two of my ntfs partitons to fat32 so both windows and linux can read/write.[/QUOTE] Correct me if I'm wrong, but I believe it isn't possible to convert from NTFS to FAT32 without losing all your data. I believe you should first remove your NTFS partition and then create a new FAT32 one.

---

### Post by floppy on 2005-09-11
Actually, you can do this conversion IF certain things are true.

Things that can cause problems:
1)   The Windows 2000/XP NTFS partition has compressed files, sparse files, reparse points, or encrypted files. In such case, you can uncompress and/or move (or delete) the sparse files, then repeat the conversion.

2)   The file system has errors, such as lost clusters and cross-linked files. You can fix these problems, then try the conversion again.

3)   There is not enough temporary space in the partition to do the conversion. The conversion will require the NTFS system and the FAT32 system files until the last step of the conversion. Also, there is data in NTFS File Replication Services that must be moved to external clusters and saved.

Those are quotes from the manual, I hope you don't mind my stating things you may have thought about.

I've done the conversion myself, but with very little data on a very large partition.

---

### Post by xequence on 2005-09-11
I dont think a fat32 partition can be over 32 GB.

---

### Post by El_Don_Casper on 2005-09-11
I tried this with my system and the problem is that windows when installed onto NTFS filesystem has files in it that are over 4gb. I changed my swap area to about 2 gb in windows and restarted and then tried again and it worked.  What i did on my laptop was zip my files to one partion and delete that partition and make a Fat32 partition there and then zip the files from the other partition over to the new  FAT32 PArtition  and make a new partition in the other space.  If you dont have enough space use norton ghost to back it  all up on cds.

---

### Post by BoomShake007 on 2005-09-11
nemin: Apparently with Partition Magic people have converted with zero data loss.
xequence: FAT32 partition can be over 32GB, but you can't create one with default Windows tools.

floppy: [quote=floppy]Actually, you can do this conversion IF certain things are true.

Things that can cause problems:
1) The Windows 2000/XP NTFS partition has compressed files, sparse files, reparse points, or encrypted files. In such case, you can uncompress and/or move (or delete) the sparse files, then repeat the conversion.

2) The file system has errors, such as lost clusters and cross-linked files. You can fix these problems, then try the conversion again.

3) There is not enough temporary space in the partition to do the conversion. The conversion will require the NTFS system and the FAT32 system files until the last step of the conversion. Also, there is data in NTFS File Replication Services that must be moved to external clusters and saved.

Those are quotes from the manual, I hope you don't mind my stating things you may have thought about.

I've done the conversion myself, but with very little data on a very large partition.[/quote]

#1: Does this mean like rar files?  I have a bunch I can get rid of or move temporarily to another partition before the conversion.  Will I be able to move them back or re-rar them after it's in FAT32?

#2: I don't believe there's any crosslinked or broken clusters.

#3: I'm using slightly over half of the 10GB partition and slightly over half of the 75GB one.  I would think that's enough space left.

I'm going to try moving hte rar files off the personal partition and run the conversion adn see where I get.

---

### Post by Parkaboy on 2005-09-11
I had a lot of problems trying to do the same some time ago, defragment your partition and see if you do not have any file compressed or encrypted with the NTFS options. Now If what you want is to write on NTFS I think you can compile a kernel with NTFS write support

---

### Post by BoomShake007 on 2005-09-11
[QUOTE=Parkaboy]I had a lot of problems trying to do the same some time ago, defragment your partition and see if you do not have any file compressed or encrypted with the NTFS options. Now If what you want is to write on NTFS I think you can compile a kernel with NTFS write support[/QUOTE]
 what do you mean by "compressed or encrypted with the NTFS options"?  What options are these?

and NTFS writing is dangerous still.

---

### Post by Fragdaddy Nukem on 2005-10-11
[QUOTE=xequence]I dont think a fat32 partition can be over 32 GB.[/QUOTE]

According to Dr. Brian K. Lewis, FAT32 can handle up to 2 terabytes: [http://www.spcug.org/reviews/bl0107.htm](http://www.spcug.org/reviews/bl0107.htm)

I'll be trying 160 gigs tonight (I got a V-Gear LANdisk in today's FedEx truck and I plan to make a NAS box for all of our family MP3 files with it).

---

### Post by Hobgoblin on 2005-10-11
[QUOTE=xequence]I dont think a fat32 partition can be over 32 GB.[/QUOTE]

Actually, it is Windows XP which won't let you create a FAT32 partition over 32GB.  It's not a FAT32 limitation.

I imagine the 4Gig file limit on FAT32 could be a problem, that's the reason I switched to NTFS in the first place.

---

### Post by theToolman on 2005-10-13
Toolmans 2 cents:

*Yes FAT32 can be as large as you can buy, but XP wont format > 32Gb; yet to hear a good reason for this, so you have to make it in linux / or DOS (win95 boot disc time...)

*I spent ages looking for a NTFS -> FAT32 conversion tool and none seemed reliable - it seems the translation this way is generally known to be iffy at best.  I recommend not using any conversion tools on any data you dont want to loose.  As i have an affinity with my data, I recommend getting a temporary drive from somewhere, copying data off, formating as FAT32 ten copying back - yes its a pain but its the safesst way!

If you just want your personal docs FAT'ed then make 10G of space on your media drive, copy it off, format, then copy on...

---

