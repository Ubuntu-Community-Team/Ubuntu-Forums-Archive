---
title: "backup question"
date: 2008-01-23
forum: General Help
---

### Post by ThunderRd on 2008-01-23
Using Simple Backup, is there a way to make hourly full backups which append to the previous backup?

I see only how to make a full backup followed by incrementals, and that doesn't suit my specific purpose.

If that is not possible, what backup program is available that has more flexibility?

---

### Post by HermanAB on 2008-01-23
Rsync is your friend.

Cheers,

Herman

---

### Post by ThunderRd on 2008-01-23
OK, can rsynch back up files that are in use at the time, a la Volume Shadow Copy in Windows?

I have a fairly simple need(for someone who knows how to do it).  I run folding@home, and I want the f@h directory backed up hourly; some of the files will be in use at any given time, and they are the most critical to back up.

How can I run a scheduled backup of one directory and its subdirectory, and include all the files that are in use?  The backup needs to be full, not incremental, and cannot overwrite the others.  I would manually delete the old backups periodically, (unless there's a way to automate that as well).  Simple Backup looked good, but it can't make multiple full backups, AFAICT.

If rsynch can do that, can someone help me with the command; I am a new Linux user and although I do my homework, I still need help. ;)

---

### Post by vanadium on 2008-01-23
You can certainly setup an easy powerfull system that creates hourly "snapshots" of your directory tree in a highly space efficient matter using rsync. Here is the full story: [http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

I am having this script to create "incremental" backups: study it, it is not as difficult as it looks. I included extra comments in the file. With respect to files being "in use" I do not expect Linux will make an issue of that, but the truth is that I am not sure about the behaviour, so check first.

```

#!/bin/bash
SOURCE=/home/vanadium
DESTINATION=/media/backupdrive/bk

# make sure we're running as root
if (( `id -u` != 0 )); then { echo "Sorry, must be root.  Exiting..."; exit; } fi;

# I included the process a function so I can easily repeat it for another directory tree.
# $1 is the argument you give. For example, if I later issue "backup Documents"
# then $1 will be replaced by "Documents". $SOURCE/$1/ will translate to
# "/home/vanadium/Documents/" and $DESTINATION/$1/ ... well, you get the idea by now.

function backup {
	# step 1: delete the oldest snapshot, if it exists:
        # Backup "snapshots" are stored under a directory e.g. Documents.1, 
        # Documents.2, etc. I maintain three versions, you can maintain as many as you want
        # This uses simply "rm"with the r "recursive" and f "force" option, so
        # the entire directory three is wiped without confirmation
	if [ -d $DESTINATION/$1.3 ] ; then			\
	    rm -rf $DESTINATION/$1.3 ;				 \
	fi ;

	# step 2: shift the middle snapshots(s) back by one, if they exist
        # This renames Documents.2 to Documents.3 using the standard "mv" command
        # Next one renames  Documents.1 to Documents.2
        # The if makes sure that the rename only proceeds
        # if the directory to move already exists
	if [ -d $DESTINATION/$1.2 ] ; then			\
            mv $DESTINATION/$1.2 $DESTINATION/$1.3 ;	\
	fi;
	if [ -d $DESTINATION/$1.1 ] ; then			\
	    mv $DESTINATION/$1.1 $DESTINATION/$1.2 ;	\
	fi;
        # This is the "heart"of the operation: using rsync in a special way, 
        #  your source files are backed up to Documents.1.
        # The special way involves the --link-dest option. For each file of the source, 
        # rsync will check whether it already exists in Documents.2. If it does, a hard
        # link to it is created under Documents.2. This makes sure that only new or 
        # changed files are being copied to the backup. Other files are just included in the 
        # backup by hardlinking them to the copy of the file that already exists in the 
        # older snapshot. As a result, only new and changed files need to be copied
        # and take additional space. Thus, the backup proceeds both very fast and
        # space efficient.
	rsync -av --link-dest=$DESTINATION/$1.2/ $SOURCE/$1/ $DESTINATION/$1.1/ ; \
}

### This then performs a range of backups by calling the "backup" function defined above
backup Documents
backup Pictures
backup Music

```

---

