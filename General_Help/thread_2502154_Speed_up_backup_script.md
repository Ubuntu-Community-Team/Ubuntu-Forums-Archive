---
title: "Speed up backup script"
date: 2024-11-03
forum: General Help
---

### Post by raleigh3 on 2024-11-03
This is running slower than I like.

I want it to compress files only with newer files and then go on to the next item.

I will get rid of anything that is slowing it down.

How can I speed it up?



```
#!/bin/bash
# 
#  BACKUP IMPORTANT FILES TO MAXTOR DRIVE 
#
# Don't use ALLCAPS for variable names or begin them with a number.
#

DOG_ATTACKS="home/andy/Dog_Attack/"
Backup_Directory="/media/andy/Maxtor/Backup/Ubuntu_Mate_24.04/"
DOCS="/home/andy/Documents/" # shell variable
SCRIPTS="/home/andy/bin/"
HOME="/home/andy/"
ICONS="/home/andy/Icons"
MY_Sounds="/usr/share/sounds/My_Sounds/"
THUNAR="/home/andy/.config/Thunar/"
Music="/home/andy/Music/"
FedEx="/home/andy/FedEx/"

#
cd $THUNAR
tar -cf Thunar_Custom_Actions.tar uca.xml
/usr/bin/rsync --progress -r -u Thunar_Custom_Actions.tar $Backup_Directory
#--------------------------------
cd /home/andy/Dog_Attack/
tar -cf Dog_Attack_Documentation.tar *.png *.pdf *.odt *.jpg *.mp4
/usr/bin/rsync --progress -r -u Dog_Attack_Documentation.tar $Backup_Directory

#-----------------------------------------------
#
cd $DOCS
tar -cf Ubuntu_Documents.tar *.txt *.doc *.rtf *.html *.png *.pdf *.odt *.ods *.odg *.csv *.xls *.jpg *.PDF *.docx *.otg 
## ONLY copy file if it's newer than destination file
##
/usr/bin/rsync --progress -r -u Ubuntu_Documents.tar $Backup_Directory

#-----------------------------------------------
cd $SCRIPTS
tar -cvf UM_24_04_Ubuntu_Scripts.tar *.sh *.txt 
/usr/bin/rsync --progress -r -u UM_24_04_Ubuntu_Scripts.tar $Backup_Directory
#
# Backup Firefox bookmarks.
# 
# Backup my music
/usr/bin/rsync --progress -r -u /home/andy/.mozilla/firefox/t0kduppg.default-release/bookmarks.html $Backup_Directory
#
cd $Music
tar -cvf My_Music.tar *.mp3
/usr/bin/rsync --progress -r -u My_Music.tar $Backup_Directory
#
cd $FedEx
tar -cvf FedEx_Documentation.tar *.png $Backup_Directory
/usr/bin/rsync --progress -r -u FedEx_Documentation.tar $Backup_Directory
#
#date +'%m/%d/%Y %I:%M:%S %p' > /home/andy/Downloads/Computer_Backup.txt
gxmessage -fg blue -font  'sans 20' -timeout 2 'Computer has been backed up' 

touch /home/andy/bin/Backup_24_04.sh

touch /home/andy/Documents/blank.odt

/usr/bin/geany /home/andy/Documents/Stuff_To_Paste.txt

```

---

### Post by TheFu on 2024-11-03
a) don't use tar.  Tar was designed for the 1990s with tape for backups. It is a terrible backup tool for today.

b) don't use rsync.  **rsync** is for mirroring directories, not backups.

If you want fast backups that are very similar to what **rsync** provides, use **rdiff-backup**.  The commands are very similar.  For most of my systems, the rdiff-backup after the first one is under 2 minutes if more than 10 seconds.  For 1 computer that has hundreds of thousands of tiny files, the backup takes about 20 minutes just due to the number of files that need to be compared.  rdiff-backup is faster than rsync because the checksums are retained between backups, so that work isn't needed AFTER the first mirror is created.  The most recent rdiff-backup looks like an rsync mirror.

BTW, for large files that don't change (music and videos), don't use rdiff-backup.  Use rsync with options that don't check block-by-block for differences.

I've posted some simple rdiff-backup command examples in these forums. Look for the most recent on (perhaps a year ago) that shows local, "push" and "pull" examples.   Found it: [Https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329](Https://ubuntuforums.org/showthread.php?t=2482517&p=14125329#post14125329)

Lastly, if you still have a Maxtor drive, it is passed time to replace it.  A 2TB USB drive can be found for less than $50.

---

### Post by raleigh3 on 2024-11-04
```
Lastly, if you still have a Maxtor drive, it is passed time to replace it.  A 2TB USB drive can be found for less than $50.[/QUOTE]

```

My main drive is a 2 Tb drive.

Why would I replace a drive that is working very excellently?

I also backup to a pendrive and DVD.

---

### Post by TheFu on 2024-11-04
The last time I saw a Maxtor drive on sale was around 2005, so it would be 20 yrs old.  All HDDs fail and 20 yr old HDDs are well passed their time of failure.

However, I did a little research and it seems that for about a year - around 2017 - the Maxtor HDD name was resurrected in China, so if that was about the time THIS drive was made, then it is only getting old, but I completely agree that you don't need to replace it provided the SMART data for the drive is all fine.  I have a few 10 yr old HDDs that have excellent SMART data still in use.  Of course, most HDDs die well before 10 yrs.

Anyway, did the examples in the linked post help with your backups?

---

