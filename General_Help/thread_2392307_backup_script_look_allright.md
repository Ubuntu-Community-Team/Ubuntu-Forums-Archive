---
title: "backup script look allright?"
date: 2018-05-19
forum: General Help
---

### Post by derekcentrico on 2018-05-19
I think this is just fine, but I don't want to run it and botch anything as I'm not totally create with the scripts lately.  Borked some stuff during a system upgrade that made life suuuuuck.  Anyway, any comments would be awesome especially if there's a more efficient way.

Basically, I have a USB drive slapped on and I'm trying to have a script do bi-monthly tarballs.  The drive will fill up after about 4 months of tarballs, but I figure I only need 1.5-2 months worth as a problem will be quite evident before that time.  So this is what I slapped together after comparing an old crappy script I had from years ago and some Googling:

```
[COLOR=#212121][FONT=Arial]#!/bin/sh[/FONT][/COLOR]
[COLOR=#212121][FONT=Arial]DATE=`date +%m_%d_%Y`[/FONT][/COLOR]

[COLOR=#212121][FONT=Arial]tar -cpzf /media/storage5/18.04/tarballs/18.04.system.operational.backup.$DATE.tgz --exclude=/dev --exclude=/tmp  --exclude=/initrd.img.old --exclude=/lost+found --exclude=/srv --exclude=/cdrom --exclude=/media --exclude=/proc --exclude=/sys --exclude=/run --exclude=/var/lib/samba/private/msg.sock/ --exclude=/var/lib/samba/private/winbindd_privileged/ --exclude=/var/snap/canonical-livepatch/ /[/FONT][/COLOR]

[COLOR=#212121][FONT=Arial]#Remove tarballs older than 60 days[/FONT][/COLOR]
[COLOR=#212121][FONT=Arial]cd /media/storage5/18.04/tarballs[/FONT][/COLOR][COLOR=#212121][FONT=Arial]
[/FONT][/COLOR][COLOR=#212121][FONT=Arial]find . -mtime +60 | grep tgz > temp.txt[/FONT][/COLOR][COLOR=#212121][FONT=Arial]
[/FONT][/COLOR][COLOR=#212121][FONT=Arial]for i in `cat temp.txt`[/FONT][/COLOR][COLOR=#212121][FONT=Arial]
[/FONT][/COLOR][COLOR=#212121][FONT=Arial]do[/FONT][/COLOR][COLOR=#212121][FONT=Arial]
[/FONT][/COLOR][COLOR=#212121][FONT=Arial]rm -f $i[/FONT][/COLOR][COLOR=#212121][FONT=Arial]
[/FONT][/COLOR][COLOR=#212121][FONT=Arial]done[/FONT][/COLOR][COLOR=#212121][FONT=Arial]
[/FONT][/COLOR][COLOR=#212121][FONT=Arial]rm -f temp.txt
[/FONT][/COLOR]
```

Thanks for any comments to come.  Cheers.

---

### Post by TheFu on 2018-05-19
Tar isn't a good backup choice when you have more than 500MB (not GB) of data. 

There is lots and lots of discussions here about different backup techniques that would be worth your time to review.  Just remember that tar was created when 250MB tapes were considered huge.  I haven't seen tar used in any professional environments since around 1995.  tar is like ZIP - would you backup an entire OS with ZIP?   The amount of time needed to create a tgz file will be non-trivial, so you'll need to take steps to prevent modification of any open files during the process.  This is most important for DBMS files.  

There are better choices that work easier. duplicity or rdiff-backup come to mind, but there are 20 others.  I use rdiff-backup.  Takes 2-4 minutes daily and I keep between 60 days and 120 days based on the risks for the system. Both tools are highly efficient with bandwidth and storage.

Generic scripting comments:
* use yyyymmdd for filenames - helps with sorting and there is an ISO standard around it. Put '-' if you like. **+ %F** does it.
* use variables to make long text/paths compact and easily modified in 1 place. If possible, use 1 BASE, then relative off that.... JAVA_HOME, JAVA_BIN=$JAVA_HOME/bin ... make sense?
* always specify the absolute path to all programs and output files when scripting. Don't trust the environment, since environment setup is different depending on how a script is run.
* Indentation is important for readability.
* really long and descriptive filenames seem like a good idea, until they aren't. Shorten where it makes sense. 18.04.system.operational.backup.$DATE.tgz  would be better with $HOSTNAME-prod-$DATE.tgz, IMHO, assuming you keep using tar (please don't).  ;)

So .... 
```
/usr/bin/rdiff-backup --exclude-special-files $EXCLUDES $INCLUDES $BACKUP_TGT
```
is what I'd do.  Then I'd run rdiff-backup again to --remove-older-than versions ... say "90D".  It is very efficient on storage and backup times.  Test it out on /etc/ a few times to see what gets written with each change to files. I think you'll like it.

You might not want to backup all the OS programs and logs either. That's usually about 4G which is easily replaced from an ISO (fresh install). Just capture the list of manually installed packages using apt-mark and back that up. Then you can just import that list and reinstall from your local apt-cache or over the internet.  If anything other than a disk failure happens, you won't want the backup files anyways, since they may be compromised.  A fresh install with fresh patches is where I begin my restore process.   My restore process is about 45 minutes:
* fresh OS install - about 15 min - only ssh-server included with base OS.
* restore app settings, DBMS files, websites, and /home/ - usually 15 minutes (25G max)
* import list of manually installed apps and reinstall those usually 15min
The system is mostly useable at this point. Lastly, 
* restore huge data areas that take what they take to restore.  10 min - 4 days.

This method works for both physical systems and virtual machines.  I treat VMs the same as physical machines.
 
There are different backups methods
* images
* partition
* file system
* hardlinking
* differencing / reverse differencing
each method has pros/cons.  At 3am, I'd love to have an image-based backup that needs 1 command to do a full restore, assuming I always need a full restore.  But I don't.  And I don't like that images require the system be down during the backup creation or that huge amounts of bandwidth and storage are required for images.  Trade-offs.

Anyways, hope this is helpful.  Whatever backup method you do end up with, be certain to test it BEFORE you need it.


Oh ... find . -mtime +60 | grep tgz > temp.txt .... 
Make that **/usr/bin/find $BACKUP_TGT -mtime +60 -a -iname \*tgz -delete** and everything is handled much more efficiently.

---

