---
title: "Home User Backup &amp; Simple Backup not up to the job"
date: 2008-02-03
forum: General Help
---

### Post by Roger D on 2008-02-03
Can anyone point me in the direction of a GUI-based backup program that is easy to use and where the user can have total confidence that everything is working correctly?

I've tried Home User Backup (which doesn't recongnise my external hard disk, where I want to store my files) and Simple Backup (where I can manage to create a file with an .fil extension on my external hard disk, but this file isn't found when I try and do a restore. A reliable backup system is absolutely critical to any computer system, and I just don't have any confidence in these two programs. For the present, my backup strategy is based on copying and pasting key directories - it's crude, it's slow, but I know it works.

I know I can use the command line to create just about any backup options I might want, which is fine for serious systems administrators, but isn't apppropriate for the typical SoHo user - i.e. someone like me. I'd be perfectly happy to pay for a suitable commercial product, and understand that Handy Backup are planning a Linux-compatible product, but I don't know when this will be available.

All help and advice much appreciated.

Roger D

---

### Post by goodfella on 2008-02-04
To tell you the truth you should consider using a terminal based backup command like resync.  I use it combined with cron and I run nightly backups on my home directory.  Resync is nice because it only backs up what is new so it is faster then just copying and pasting things over.  Also, with cron you can schedule the backup at any kind of interval you want.  I backup my stuff both to another hard drive and an external drive connected to my computer through usb.  It works flawlessly.  Another option is to tar and gzip directories to back them up.  I do this also and I append a date at the end of the file name so I know when the backup was performed.  My backups are flawless and require absolutely no user intervention. They are done everyday without me having to do anything.  Think about it.  I would be glad to help you.

---

### Post by Roger D on 2008-02-08
Many thanks for the offer of help. I really do need a reliable, understood, backup system, and I'm quite happy to give rsysnc a try.

Here's the background to what I'm trying to do. I'm running 6.10, and there are two users on my PC, myself, roger, and my wife, sarah. I'm the principal user, and the one with administration rights. I work as a part-time technical editor, and it's absolutely essential that I'm not without a working computer for more than a few days at a time. To protect myself against a hard disk failure, at the end of each work session I copy the folder containing all my editing work onto an external hard disk (/media/"My Book"). I just do a simple copy and paste. My work folder holds over 2000 files and is over 900 MB, but the copy and paste is pretty quick. I know it's crude, but I'm also confident it works.

I also have a spare PC, also running 6.10, and, in the event of my regular PC failing for any reason, I would simply copy my work folder into /home/roger on my spare PC, and carry on. Evolution is a bit of a problem, but, now and again I copy my inbox and contacts list onto the external hard disk.

I'd like to be able to do a bit better than this. Some sort of incremental back up scheme would be nice; I'd like to be able to save all my Evolution files, and my desktop settings, and I'd like to be able to backup my wife's files as well. She tends to get a bit upset when my mishaps result in a loss of her data.

All advice and help would be much appreciated.

Best regards

Roger D

---

### Post by Irihapeti on 2008-02-08
rsync has a graphical front-end, grsync, which is in the repositories. It might help get you started.

---

### Post by goodfella on 2008-02-09
Here is the way I do my backups.  First you will need to understand crontab.  Here is a good link:

[http://www.adminschoice.com/docs/crontab.htm]("http://www.adminschoice.com/docs/crontab.htm")

You can edit your crontab file like so:
```

crontab -e

```

my crontab file consists of the following:
> 
30 22 * * * /home/nick/backup-scripts/backup-home
30 22 * * * /home/nick/backup-scripts/backup-win
30 22 15 * * /home/nick/backup-scripts/backup-media
30 22 * * * /home/nick/backup-scripts/backup-school


So according to the crontab I run 3 backups every night a 22:30 (10:30 pm), and 1 backup every 15th of the month also at 22:30 (10:30 pm).  I basically run a script at the specified times.  The scripts you probably would be interested in are backup-home and backup-school.

Here is backup-home:
> 
#!/bin/sh
/usr/bin/rsync -avx --exclude=.aptitude --exclude=.rnd --exclude=.qt /home/nick /media/backup

/usr/bin/rsync -avx --exclude=.aptitude --exclude=.rnd --exclude=.qt /home/nick /media/ext-backup


One note about crontab files is to only use absolute paths.  Also always place an extra newline at the end of the crontab.  The first command says to backup my home directory on /media/backup.  The second command says to backup my home directory on /media/ext-backup.

Here is backup-school:
> 
#!/bin/sh
/bin/rm -f /media/backup/school-backup-*
/bin/rm -f /media/ext-backup/school-backup-*
/bin/tar cvpzf /media/backup/school-backup-`/bin/date +'%m-%d-%y'`.tar.gz /home/nick/school
/bin/cp /media/backup/school-backup-* /media/ext-backup


This script removes the previous nights backups and then tar and gzips my directory with my school work.  The date is appended to the end of the file name so I know when the backup was created.

You don't have to use rsync for your home directories.  You can choose to tar those up as well.  I just did that because I wanted an uncompressed backup of my home directory at all times.  But you may not care.  Remember the nice thing about this is it is completely automatic once you get it setup.  I hope this helps.

---

### Post by Roger D on 2008-02-09
Hmm... that sounded like a good idea.

I installed grsynce, and found a tutorial at [http://pclosmag.com/html/Issues/200708/page04.html](http://pclosmag.com/html/Issues/200708/page04.html). Followed all the instructions, setting the various option boxes as suggested; then clicked on 'execute'.

Things seem to go pretty well for a while, but soon everything stopped, and I got a couple of messages saying the likes of 'rsync: connection unexpectedly closed' and 'rsync error: error in rsync protocol data sream'.

I checked the destination folder' /media/"My Book"/backups/roger_backup, and found a couple of text files, which had certainly come from my home folder. Progress - but still a long way to go.

Any ideas, anyone?

Roger D

---

### Post by geo909 on 2008-02-09
I had a similar question recently.
Just wanted to mention that for image Harddrive or partition backups, 
clonezilla is a fine tool. Google it if you want more info.

---

### Post by Roger D on 2008-02-09
Just can't get rsync to work. Tried it from the command line and got:

roger@roger-desktop:~$ rsync -av /home/roger /media/"My Book"/backups/roger_backup building file list ... done
roger/
roger/.ICEauthority
roger/.Maelstrom-data
roger/.Xauthority
roger/.Xscrc
roger/.aspell.en.prepl
roger/.aspell.en.pws
roger/.barrage.hscr
roger/.bash_history
roger/.chromium
roger/.chromium-score
roger/.dmrc
roger/.esd_auth
roger/.fonts.cache-1
roger/.gksu.lock
roger/.gtk-bookmarks
roger/.gtkrc-1.2-gnome2
roger/.lesshst
roger/.mailcap
roger/.mime.types
roger/.nvidia-settings-rc
roger/.plan
roger/.realplayerrc
roger/.recently-used
roger/.slune
roger/.sudo_as_admin_successful
rsync: send_files failed to open "/home/roger/.viminfo": Permission denied (13)
roger/.xsession-errors
roger/19_11_07_clive
roger/1_to_s_malindine
roger/DARCEYBUSSELL_PILATESFORLIFE.iso
rsync: writefd_unbuffered failed to write 4 bytes: phase "unknown" [sender]: Broken pipe (32)
rsync: symlink "/media/My Book/backups/roger_backup/roger/Examples" -> "/usr/share/example-content" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/googleearth" -> "/home/roger/google-earth//googleearth" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.adobe/Acrobat/7.0/Cert/curl-ca-bundle.crt" -> "/usr/lib/Adobe/Acrobat7.0/Reader/Cert/curl-ca-bundle.crt" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/default" -> "win98" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_hta.xpm" -> "/opt/cxoffice/share/icons/crossover.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_pics-rules.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/prffile.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_pkix-cert.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/cerfile.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_pkix-crl.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/crlfile.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_rat-file.xpm" -> "/opt/cxoffice/share/icons/crossover.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_vnd.ms-pki.seccat.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/catfile.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_vnd.ms-pki.stl.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/stlfile.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-cdf.xpm" -> "/opt/cxoffice/share/icons/crossover.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-art.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/artfile.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-cat.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/catfile.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-chm.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/chm.file.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-crl.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/crlfile.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-eml.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/microsoft+internet+mail+message.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-grp.xpm" -> "/opt/cxoffice/share/icons/crossover.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-hta.xpm" -> "/opt/cxoffice/share/icons/crossover.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-ini.xpm" -> "/opt/cxoffice/share/icons/crossover.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-ins.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/x-internet-signup.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-isp.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/x-internet-signup.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-its.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/its+file.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-jfif.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/pjpegfile.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-js.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/jsfile.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-jse.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/jsefile.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-m1v.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/mpegfile.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-mht.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/mhtmlfile.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-mhtml.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/mhtmlfile.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-mp2v.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/mpegfile.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-mpa.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/mpegfile.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-mpv2.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/mpegfile.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-msi.xpm" -> "/opt/cxoffice/share/icons/crossover.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-nws.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/microsoft+internet+news+message.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-p7b.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/spcfile.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-p7c.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/certificate^5Fwab^5Fauto^5Ffile.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-p7r.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/p7rfile.xpm" failed: Operation not permitted (1)
rsync: symlink "/media/My Book/backups/roger_backup/roger/.cxoffice/newbottle/desktopdata/cxassoc/tagged_icons/cxoffice-7e3ec374-9084-46dc-876f-1384be4b178d.application_x-crossover-prf.xpm" -> "/home/roger/.cxoffice/newbottle/windata/Associations/prffile.xpm" failed: Operation not permitted (1)
rsync: connection unexpectedly closed (488427 bytes received so far) [generator]
rsync error: error in rsync protocol data stream (code 12) at io.c(434)
rsync: connection unexpectedly closed (674 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(434)
roger@roger-desktop:~$

Any ideas

---

### Post by brucewagner on 2008-02-11
I found a pretty cool looking program you might want to check out...   It seems to do what you're looking for...  in a nice GUI.

It's called Unison.

It is under Applications-->Add/Remove...

---

### Post by Roger D on 2008-02-11
Hmm... Had a look at Unison - it's amazing  the tools that are out there. But I'm not at all sure if Unison is what I'm looking for. All I really want is a simple reliable means of backing up and restoring home directories - Unison seems to be focused on synchronising files across networks, and I don't even know what synchronising files means, and whether it has anything to do with backup and restore. Simple Backup seems to be the application within Ubuntu designed expressly for a GUI-based backup and restore, and I'm trying to focus - see my post 'Can Simple Backup' be made to work' on trying to establish whether it works or not.


Roger D

---

### Post by undecidable on 2008-02-11
My needs are similar to yours,
though I like very fine control and detailed reporting.
I am new to Linux.
Under Wz I used Veritas Backup Exec Desktop.

I considered areca, afbackup, bacula, cedar backup, BackupPC & BRU.
and tested in detail
. keep
. simple backup / sbackup
. backup2l  (cmd line)
	
Keep:
. Cant avoid auto backup.  
. Cant select subdirs or files within subdirs.
. Cant seem to control diff backups.  
. Can do manual.

sbackup:
. Can avoid auto backup.  
. Cant select subdirs or files within subdirs.
. No diff, only full & incr backup.  
. Cant control which is done.
. Can do manl backup, but prog decides full or incr!
. Files in .tgz and can be browsed, extracted.

I finally selected backup2l:
	[http://sourceforge.net/projects/backup2l/](http://sourceforge.net/projects/backup2l/)
	[http://backup2l.sourceforge.net/](http://backup2l.sourceforge.net/)
man page on
	[http://www.penguin-soft.com/penguin/man/8/backup2l.html](http://www.penguin-soft.com/penguin/man/8/backup2l.html)
and one guys experience on:
	[http://www.debianhelp.co.uk/backup2l.htm](http://www.debianhelp.co.uk/backup2l.htm)

I did not originally want to consider a cmd line tool
and was looking for a gui tool,
but in fact backup2l is easy to use
and am very happy with it.  

Like many command line tools
I had to read the man page 3 or 4 times to fully grasp it.

You specify most of your options in a config file.  
In fact I use two config files to backup 2 different parts of my files system that I want treated separately.
The reporting is very nice,
and you can easily browse the backup.
If you would find it helpful I can post my own summary of how I use the command.

Hope this is helpful.

---

### Post by Krydahl on 2008-02-11
Unison does do synchronization - but all that means is that it checks to see if anything has changed in both directories. So, if you had a laptop and a desktop, both with a copy of your book on it, you could edit files on either machine and then Unison would copy changes both ways. It works well until you edit the same file on both machines between syncs.

Given you'll only ever be changing stuff on one machine, you should have no problems with this. Unison is doing some extra work it doesn't need to, but that's not a problem.

You may well be having trouble with permissions on the external disc. You don't say what it is, but if its formatted using FAT32, say, then it doesn't support permissions. Rsync tries to get permissions to match as well as file content, so fails if you don't get your options set right.

Unison uses rsync too, so you may find that's still a problem.

When you first create a backup profile in Unison, it creates a directory ~/.unison. In there it puts .prf files which specify which directories you want backing up. If you have problems with permissions, try setting the option perms = 0. You'll end up with a file that looks something like:
```
# Unison preferences file
root = /home/username/documents
root = /nas/documents
perms = 0
```

One final note, with backups its nice to have them run automatically. Once you've created a unison profile you can run it from the command line. That means you can put it in your crontab. You want to use unison -batch profilename

---

### Post by Roger D on 2008-02-11
My external disk if FAT32. Could this be the root of my problems?

---

### Post by Krydahl on 2008-02-11
As I say, FAT32 doesn't handle permissions which gives rsync some problems. Most of the backup/sync tools I looked at used rsync even if they put a nicer front end on it.

If you're only accessing the disk from linux machines I guess you could reformat to ext3 or something. If you want a windows machine to be able to read it that isn't an option.

The perms = 0 option seemed to sort it with Unison for me. I found that rsync - r --delete worked in a simple backup script, though it seems erratic about deleting files that have been deleted in the original directory (which was what I wanted). I have to say that my backup to my external FAT32 isn't totally satisfactory but it will do for my needs.

---

### Post by Roger D on 2008-02-11
The implication seems to be that you can't expect to backup any part of a Linux system onto a FAT32 drive. If this is the case,  I wish this information was included in the description of all backup programs, including Simple Backup.

Roger D

---

### Post by dark_phantom on 2008-02-11
If you only backup a couple of folders and always store your data there, running a simple tar command is all you need.  Or you could create a script to do it for you.

For example:

To backup a work folder under your home directory, you can do this command.

sudo tar cvpzf /media/"My Book"/mybackup_`date +%m_%d`.tar.gz /home/"username"/work

To restore, simply you would do.

cd /home/"username"/
sudo tar xvpzf /media/"My Book"/mybackup_"whatever date".tar.gz

If you like to backup multiple folder then follow them at the end of your tar cvpf command.

sudo tar cvpzf /media/"My Book"/mybackup_`date +%m_%d`.tar.gz /home/"username"/work /home/"username"/folder1 ... /home/"username"/folder2 ... etc

This probably the simplest backup with a command.  You can get fancier with cron and scripts, but this would work for you.  Send me a PM if you like extra help with this.  I hope this helps you out.

---

### Post by Roger D on 2008-02-11
Thanks

This seems fairly straightforward, but I've a couple of questions:

1 Currently I back up my 'work' folder by a copy and paste operation to my external hard disk. Apart from the opportunity to apply a bit of compression, what's the advantage of using tar?

2 Will tar work with complete home directoires? i.e. I won't run into any problems with permission when I try and untar 'roger' or the home directories of any other users on my system, and will all the hidden folders, especially those related to Evolution, will also untar successfully?

Roger D

---

### Post by chadeldridge on 2008-02-11
Have you tried doing something as simple as using Tar to compress the files and using cron to schedule the backups?

sudo tar cvpzf /media/disk/Backup/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/media /

Something like this is what i use.

---

### Post by Irihapeti on 2008-02-11
I seem to recall reading that tar retains file permissions within archives, but it's been a while since I looked at that.

I use a script to backup my system using tar. It's one I wrote myself becauseI have only DVDs as an external medium; all of the readily available Linux backup options assume something instantly rewritable such as a hard drive or usb stick.

Once the script is written, it's very easy to run. You can set it up as a choice in your main menu, if you wish. In fact, I'm much more regular and organised now with my Ubuntu backups, than I was when using Windows when I had plenty of gui backup programs to choose from.

---

### Post by brucewagner on 2008-02-11
> **Roger D said:**
> Hmm... Had a look at Unison - it's amazing  the tools that are out there. But I'm not at all sure if Unison is what I'm looking for. All I really want is a simple reliable means of backing up and restoring home directories - Unison seems to be focused on synchronising files across networks, and I don't even know what synchronising files means, and whether it has anything to do with backup and restore. Simple Backup seems to be the application within Ubuntu designed expressly for a GUI-based backup and restore, and I'm trying to focus - see my post 'Can Simple Backup' be made to work' on trying to establish whether it works or not.

Synchronizing files means that all the changes made to files in location A would be also applied to location B.   And all the changes made to files in location B would also be applied to those in location A.

But Anyway....  Now that I understand more about what you're looking for...

I think you should try THIS one:  Called, " QuickStart: Back-up, Restore, & Set-up (Flash/Codecs/Java) Ubuntu Quickly and Easily"  see [http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

It was designed SPECIFICALLY to back up your Home folder, etc.... with a simple GUI interface.

---

### Post by dark_phantom on 2008-02-11
> **Roger D said:**
> Thanks

This seems fairly straightforward, but I've a couple of questions:

1 Currently I back up my 'work' folder by a copy and paste operation to my external hard disk. Apart from the opportunity to apply a bit of compression, what's the advantage of using tar?

2 Will tar work with complete home directoires? i.e. I won't run into any problems with permission when I try and untar 'roger' or the home directories of any other users on my system, and will all the hidden folders, especially those related to Evolution, will also untar successfully?

Roger D

1.  To me it's just a better thing to have a compress file, you can see what you have on it by double clicking it and also by tar tvpzf 'file'.  I guess if you don't like that and would like to keep the same structure you can do a find command that will practically do the same thing as a copy and paste action.

2.  Yes, you just gotta be careful what you want to archive.  As long as you have the p option in tar the permissions should be the same.  In evolution, you can archive all or parts of what you need.  But essentially yes, all of your hidden files will be archived.

---

### Post by brucewagner on 2008-02-11
> **Roger D said:**
> 1 Currently I back up my 'work' folder by a copy and paste operation to my external hard disk. Apart from the opportunity to apply a bit of compression, what's the advantage of using tar?

2 Will tar work with complete home directoires? i.e. I won't run into any problems with permission when I try and untar 'roger' or the home directories of any other users on my system, and will all the hidden folders, especially those related to Evolution, will also untar successfully?

You can do your backups of your Home folder to CDs or DVDs.  The data will be compressed and "sliced" into pieces that fit onto a series of CDs or DVDs.   This will allow you to use fewer CDs or DVDs.

Yes,  QuickStart is a simple GUI interface which automates the backup and restore of your /home directory (as well as several other features).  It is my understanding that it uses tar as the underlying tool, but it saves you the hassle of getting all the tar commands perfectly right.

Yes, tar can back up complete folder structures, including sub-folders.

It is also my understanding that tar DOES preserve all Permissions.

(This is my understanding,  Check with the author, mdpalow, on the other thread to be sure, at [http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462) ), 

I have used Quickstart myself, and nothing could be easier and simpler.

A total newbie can use it easily.

---

