---
title: "rsync help"
date: 2018-03-22
forum: General Help
---

### Post by grangemd-3 on 2018-03-22
I am trying to use rsync to make a local backup of my data.  I would like to make incremental backups where the first folder is a full backup and then the folder will get moved as days go on keeping a hard link to the first folder.  I found an article on this here: [http://www.admin-magazine.com/Articles/Using-rsync-for-Backups/(offset)/2](http://www.admin-magazine.com/Articles/Using-rsync-for-Backups/(offset)/2)   The problem i am having is that when I seem to do the mv command it copies all the files rather than making a hard link thus I lose all my hard disk space.  Any advice on what I am doing wrong.  

Here is my script:

```
#!/bin/bash 

Source4=/mnt/user/Recordings/Test
Destination1=/mnt/disks/BackupB1/Daily

#####################
### Destination 1 ###
#####################

### Source 1 ###
rm -rf $Destination1/TVShows/Daily5
mv $Destination1/TVShows/Daily4 $Destination1/TVShows/Daily5
mv $Destination1/TVShows/Daily3 $Destination1/TVShows/Daily4
mv $Destination1/TVShows/Daily2 $Destination1/TVShows/Daily3
mv $Destination1/TVShows/Daily1 $Destination1/TVShows/Daily2
cp -al $Destination1/TVShows/Daily0 $Destination1/TVShows/Daily1
rsync -a --delete $Source4/ $Destination1/TVShows/Daily0/ |& logger
```

I have also tried it with this as my last two lines but no luck:

mv $Destination1/TVShows/Daily0 $Destination1/TVShows/Daily1
#rsync -avh --delete --link-dest=$Destination1/TVShows/Daily1/ $Source4/ $Destination1/TVShows/Daily0/ |& logger

---

### Post by vanadium on 2018-03-22
Looking at your code, I do not see the error. This statement "The problem i am having is that when I seem to do the mv command it copies all the files rather than making a hard link thus I lose all my hard disk space. " is unclear: I do not see how the problem can be at the level of the move: move/rename just changes the name of the folder, so should not result in copying or unlinking the files. Are you sure all your drives involved fully support linux file attributes (i.e. ext4 or another native linux file system, no ntfs)? Otherwise, rsync might not consider source and destination equal and thus copy over all files each time.

f.y.i., that's how I work:
```

function backupinc {
	if [ -d $1 ] 
	then 
		if [ -d $2 ]
		then
			rsync -av --delete --exclude '*/ImapMail/*' --link-dest="$2" "$1" "$2-new"
			mv "$2" "$2-$date"; mv "$2-new" "$2"
			sync
		else 
			echo "Destination $2 not available"
		fi
	else
		echo "Source $1 not available"
	fi
}

backup "$SOURCE" "$DESTINATION"

```
rsync nowadays can make the hardlinks itself. It makes a new copy involving hardlinks if possible. The current copy is then renamed by appending a date and time stamp, and the new copy is then renamed to be the current copy.

You might also want to look at rsnapshot, which is a script available in the repository that works in a similar way.

---

