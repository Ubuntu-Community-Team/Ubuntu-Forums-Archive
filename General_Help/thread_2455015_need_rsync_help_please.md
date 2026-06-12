---
title: "need rsync help please"
date: 2020-12-10
forum: General Help
---

### Post by coley9225 on 2020-12-10
I'm  trying to figure out how to make rsync make a copy of any files marked for deletion. My current back-up scheme is,
Timeshift --- daily back-up of / and /home partitions. I retain the last 10 days. This seems to be working fine.
I have a separate partition for most of my important files, documents, photos, etc. To back-up that partition,
bash script with basic cp command --- cp -ruv /media/source dir /home/.Backups -- each dir in the partition is copied separately.
rsync -avh /media/source/dir /rsync_day --delete-after ---delete-excluded   (runs daily)
rysnc -avh /media/source/dir /home/rsync_month   (runs on the first day of month)

I originally had it NOT delete anything, that way if I deleted a file and realized later I needed it it I could restore that file. I went through and renamed a large number of photo and movie files and quickly out grew the partition, so I added --delete-before to the command. This configuration eliminates the ability to recover any files after the monthly back up has run. I would like to split thee difference. I want to delete files that are not in the source, but rather than delete them entirely, move them to another partition
so they are available, and I can thin the files out as I have time. I hope I worded everything so that you understand my goal, if not ask whatever you need and I will clarify. 2 things to note. First, before it comes up, I understand that rdiff-backup is a more efficient method for this type of backup. I am reading up on it and when I figure it out a little more, I may rewrite my backup scheme. Second, just for the curious, yes backups are to external drive, and the verbose part of the backup commands are there for when I run them from terminal.
 Any helpful tips are always appreciated.
      Thanks

---

### Post by TheFu on 2020-12-10
You need versioned backups. 

For everything except video and audio files that basically never change, duplicity, back-in-time, rdiff-backup, rsnapshot can all handle that fine.
For large media files where versioning can eat hge amonts of storage, I have 2 ideas.
[LIST=1]
[*]Use any of the above tools, but only keep 2 days  i.e. 2 backup versions).  unfortunately, many of those tools se hardlinks to minimize storage used, bt that doesn't work across fle systems.
[*]Use the  rsync --dry-run option to get a list of files to be deleted, then copy that list off to the other storage, before removing the --dry-run and doing the sync.
[/LIST]

I think complicated solutions lead to failures. Simplify as much as possible. Limit the special situations wen possible.

---

### Post by HermanAB on 2020-12-11
Maybe see this:
[https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html?m=1](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html?m=1)

---

