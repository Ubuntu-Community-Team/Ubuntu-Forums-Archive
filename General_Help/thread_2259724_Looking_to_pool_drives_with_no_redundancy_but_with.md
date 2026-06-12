---
title: "Looking to pool drives with no redundancy but with portability of individual drives"
date: 2015-01-06
forum: General Help
---

### Post by duelistjp on 2015-01-06
[COLOR=#2A2A2A][FONT=Segoe UI]I'm currently building a new file server to replace my old one.  I am looking for a way to pool drives that has the following properties.[/FONT][/COLOR]
[COLOR=#2A2A2A][FONT=Segoe UI]1.  I do not want to have data redundancy,  I just can't afford extra drives and my offsite backup is good enough for me.[/FONT][/COLOR]
[COLOR=#2A2A2A][FONT=Segoe UI]2.  Files should not be split across multiple drives.  When I put a file on there it should be on a single drive.[/FONT][/COLOR]
[COLOR=#2A2A2A][FONT=Segoe UI]3.  Each hdd should be able to taken out individually to another comp and the data on it be readable without the other drives[/FONT][/COLOR]
[COLOR=#2A2A2A][FONT=Segoe UI]4.  When a drive fails the files on the nonfailed drives should be able to be read normally.[/FONT][/COLOR]
[COLOR=#2A2A2A][FONT=Segoe UI]I think 3 and 4 are somewhat related in that if a system solves one the other should be solved to.  I imagine by having the directory structure be duplicated on all drives in the pool and the drives be displayed in a merged fashion.  Ideally I would like it to fill the drives fairly evenly where it chooses which drive to place a new file on based on which drive has the greatest % of free space.[/FONT][/COLOR]
[COLOR=#2A2A2A][FONT=Segoe UI]The reason for this is that this drive has a partition for files of a certain type.  Namely media files.  Now it is inconvenient to have to go searching multiple folders to find a given series or movie so i would like to have them appear together.  This also makes things simpler for the program that automatically renames and moves new files as I can just tell it to put it in this folder and not have to worry about which drive has space.  There are a number of solutions to this problem I have found but they all fail the other criteria.  namely that the entire group of drives becomes unreadable if one fails and they are not individually readable when taken to other machines.  As I can't afford to provide redundancy in the pools and it is a significant bother to restore from my offsite backup this is a significant problem.  Is there a solution you know of that can do this.  My old server was linux using lvm but I just can't stand the thought of losing several drives worth of data if one were to fail so I want to rectify this on my new server[/FONT][/COLOR]

---

### Post by TheFu on 2015-01-06
You can create this easily by using symbolic links. That is standard for all Linux/Unix file systems. It doesn't work on NTFS or FAT or HFS. Just make a link to the other drive's top directory from where ever you like on the 1st drive.

Or if you want to be more complex, use something like aufs, unionfs, or  MHDDFS. I've never used any of these.

---

### Post by duelistjp on 2015-01-06
so if I had 2 drives with movies that would still require it to be 2 separate folders though wouldn't it?

---

### Post by TheFu on 2015-01-06
> **duelistjp said:**
> so if I had 2 drives with movies that would still require it to be 2 separate folders though wouldn't it?

The limitation is just your imagination.  I do it with m1/ and m2/ links. Hardly any hardship and popular media software like Plex handles it fine.  You could create a link for every file, if you wanted, but that would be a maintenance nightmare.

Play with some symbol links to see how they work. Try files, directories, and different levels ... you'll see.

---

### Post by duelistjp on 2015-01-06
that would require me to choose where each is put. currently with lvm it puts it in one drive than when it needs puts it in the other without me thinking of which.  your way would require me to make sure when one got full i started putting stuff in the other which would mean i'd be getting errors when the disk is too full then needing to change my settings.  i don't normally check this server but once a month. i guess it's not too much of a hassle as i can just put stuff in one and copy stuff over to the other once a month till it is filled then let it start accumulating in the other.  that might be the solution for me as 99% of the time I'm using plex.  it'll be inconvenient when i do need to manually navigate as i won't know which folder a movie is in but i guess that is what search is for.  thank you for your input

---

### Post by TheFu on 2015-01-07
Don't know where media is?  Ever heard of '**locate**'?

Or Plex/XBMC requires that media be split by types - movies, TV, music, photos ... put 1 type on one disk.
Or by the first letter of the title ... A-M on Disk-1.. N-Z on Disk-2.

Plex doesn't care if there are 2, 10, 20, HDDs involved and it really doesn't matter to us humans either ... well, except for backups and for alarming. You did say server, right? All servers need alarming to warn the admin about issues (like a full disk).  Have the computer work for you, not the other way around.  This stuff has been solved usually in a fairly elegant way over the 40+ yrs of UNIX.  The hard part is for us to learn about it.

---

### Post by Impavidus on 2015-01-07
Or write some scripts to do the hard work for you and run them as cron jobs. Balancing usage over both drives, creating the symlinks. A script can easily handle the symlinks even at file level.

---

