---
title: "Troube using Luckybackup"
date: 2013-03-23
forum: General Help
---

### Post by unknown user on 2013-03-23
In the past I have been using luckybackup and I have found it great. It did what it said on the tin and I was more than happy with it.

I have a laptop with family pictures on it, a 1TB HDD that the pictures (and everything else) goes to and this is all backed up in my 2TB HDD.

The only thing that gets updates/changed really is the pics as new ones get added.

Yesterday, I backed up the pictures from the laptop to the 1TB HD all OK, sweet as a nut. So last night and tonight I tried to update the 1 TB to the 2TB. Remembering that only pictures have changed, it should of been a relatively quick process as normal. 

However when I tried it, it took well over 4 hours to only get to 38%. Not normal at all. It seems to be trying to back u every file and not delete any of the 2TB that have been deleted of the 1TB. Normally, it would delete old versions. I have not changed anything so cannot understand what is going on.

I just want my pics file of my laptop to be the master for the pics on the 1TB and for that to be the master for the 2TB. 

Does anyone know any good programs for this or why luckybackup may not be working now? I tried Grsync but this does not seem to be deleting old files from the 2TB

---

### Post by unknown user on 2013-03-23
It would appear that the 2 TB file is not allowing files/folders to be deleted for some reasons. I have checked the drive permissions and everything looks OK.

---

### Post by ibjsb4 on 2013-03-23
Like yourself, I been using lucky for a long time and its one of those packages that just work.  I was surprised to see your post so I did a little investigating.

LaunchPad has only 4 open bugs on lucky and 29 on rsync.  Nothing seems to apply to your situation.  You seem to have an isolated problem.  I think you have a good question for launchpad.

Good luck :)

---

### Post by unknown user on 2013-03-23
Hi there,
Thanks for the reply, like you I was shocked that it has started to go wrong :(
I have had a look and now old pics on the 1TB (being updated from the laptop) are not being deleted.
I have had a look at the backup from 1TB to the 2TB HDD are the following is shown. It appears to be an issues with the deleting of old files, it is not doing it :)
Also there seems to be a problem with the Trash files on the 1TB, so I tried deleting them and this did not make any difference:

[COLOR="#0000CD"]Removing old snapshots and logfiles of task: Westen Digital1 TB HDD Backup
=====================================
Removed all older snapshots data
Removing /home/unknownlaptop/.luckyBackup/snaps/default-Westen Digital1 TB HDD Backup-20130324135244.changes.log
Removing /home/unknownlaptop/.luckyBackup/logs/default-Westen Digital1 TB HDD Backup-20130324135244.log
=====================================
execution of task : Westen Digital1 TB HDD Backup, starting
Source : /media/Elements
Destination : /media/Expansion Drive/Westen Digital 1TB Hard Drive backup/Elements/
building file list ...
0 files...
rsync: readlink_stat("/media/Elements/.Trash-1000/expunged/213039232/amarok") failed: Input/output error (5)
rsync: readlink_stat("/media/Elements/.Trash-1000/expunged/213039232/RecentDocuments") failed: Input/output error (5)
rsync: readlink_stat("/media/Elements/.Trash-1000/expunged/688674988/.azureus") failed: Input/output error (5)
100 files... 
[/COLOR]

---

### Post by orb9220 on 2013-03-24
Just a shot in the dark and guessing here. And may not be the issue at all.
But possible as incremental relies on timestamp of files.
 
Recently there have been complaints on correct time and clock issues since the change to DST.
And file timestamps being generated incorrectly. Would create a text file and save then look at the timestamp of file.

---

### Post by unknown user on 2013-03-25
Thanks for the replies.

I think that I may of fixed the issue, or at the moment it looks like I have. On the 1TB HDD I moved all my folders/files into their own folder and left the .Trash one on its own. I then tried it again and it seemed to work. it did say that it had deleted some of the destination, which I checked were still on the source (which they were). So at first sight all looked OK and back to normal.

The thing that got me is many times before I had done a backup the same way as this time and all was OK. Just this time it decided it did not like it and wanted to throw an error message. How strange.

The one thing that I am finding is that now the file paths have changed, I need to change all reference to them, like in my iPod backup, oh well lol.

---

