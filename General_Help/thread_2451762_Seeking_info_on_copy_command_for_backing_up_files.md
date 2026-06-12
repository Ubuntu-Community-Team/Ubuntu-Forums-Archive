---
title: "Seeking info on copy command for backing up files"
date: 2020-10-10
forum: General Help
---

### Post by coley9225 on 2020-10-10
I'll start as I usually, by mentioning that I'm a noob...lol. I have a 1TB ssd in my computer. I do my backups to an external 2TB hdd, with multiple partitons for different types of backups. I use timeshift for a majority of my backups, at least weekly, to 1 partition. I wrote a bash script to run multiple cp commands to backup an ntfs partition of all my documents, picture, music, etc. I need the ntfs because, although rare these days, I do still boot to windows occasionally. I have an entry in fstab for my backup partition. My script goes like this( not doing entire script, just enough to show setup). 

sudo mount /home/.Backups

cp -ruv /media/charles/common_data_files/Documents /home/.Backups &&
# I have 7 lines like this, 1 for each dir(folder) to backup. the delay ( && ) is so I don't overload my weak machine trying to copy multiple dir at once.)

sudo umount /home/.Backups

then a zenity command to place info dialog box on my screen.

I don't sleep or hibernate my computer, I lock the screen so display goes black at night. I edited my sudoers file so I don't get a password prompt ( I still have to use sudo). I made an entry in crontab ( not root crontab) to run this at 12:05 on sunday morning, and the zenity box is there after I log in so I know it ran.
I have 2 questions about the copy command and setting this up the waay I did. The first( I think I know the answer, but want to be sure) question. If I go into a directory say movies, and delete a file, will it be deleted from the backup next time this runs. I don't think it will because that's 1 of the reasons for a backup. The other question is, if I go into my photos and rename a file, from some string of numbers to something I can understand, will it rename the file in the backup, or is it going to make a duplicate picture with the new name. I download photos of family and friends and they are always a string of letters and numbers, and want to rename to something like jon_doe 10_6_20 so I know what it is. If it makes a dupe file, is there an easy way to do this, or will I have to remove them from my backup manually. Sorry if this is confusing. I've been trying to think of a way to word it for couple hours. Questions to clarify are of course welcome. As always, any help would be appreciated.

---

### Post by TheFu on 2020-10-10
Don't use cp, use **rsync**.  rsync has lots and lots of options, including --delete.

For datafles only, ntfs is ok, but not the best choice.  In Unix, the data is only 50% of what a backup requires. The permissions, acls, xattrs, owner, and groups are just as important. 

Really, a proper backup tool would make all this extra effort unnecessary. If you need more than 1 tool, I'd say you are doing it wrong; making it hard.

If you insist on using rsync, something like this:
```
ionice /usr/bin/rsync  -av --stats --progress $EXCLUDES --delete /d/D1/ /d/b-D3/
```

Every command has a manual page on Unix systems. in the man pages are all the options and a description for each.  Either **man** or **xman** can be used.  Some commands support --help option too. This is a summary, not as complete as the manpage.  We aren't supposed to tell people to check out the manpage here, but most questions like this really are best answered in that way.  Additionally, running a small test between two temporary directories with just a few files would answer the other questions quicker than posting and waiting.  There are a number of caveats with the humble 'cp' command. The manpage has those too.

Backups are different from mirrors or clones. each has a different purpose. 
[LIST]
[*]For mirrors, rsync is the tool. Depending on the way it is run.
[*]For cloning, there are lots; dd ddrescue, fsarchiver, clonezilla. 
[*]For backups, things are seem more complex because people confuse a mirror or clone as a backup all the time. They are not. Rsync can be abused into a backup tool, but there are other tools that are almost the same, but add versioning, but also handle ACLs, xattrs, owner and group.
[/LIST]

---

### Post by coley9225 on 2020-10-10
Thanks for the reply and feedback. I definitely want an easier way to do the backups. As I mentioned, I use timeshift for my / and /home partitions. If I understand what I've read, this doesn't back up all the docs, pictures,etc. 
Also, afaik, I can't backup to or from from a ntfs partition, it must be ext4 or some other linux file system. I have a long list of bookmarks for how tos and tutorials, so I'll do searches and add some for rsync to the list. If I read a tutorial or 2 that I can understand, I may write a new script and start using rsync as my primary backup. Whatever I settle on, I need to keep the ntfs until I totally wipe windows from my computer, which may be in the not to distant future at this point. I'm sure going straight linux based would make this a much simpler task.

---

### Post by TheFu on 2020-10-10
rsync is a smarter 'cp'.

---

### Post by coley9225 on 2020-10-11
After reading a lot of tutorials on rsync,( some of it multiple times), I think I figured out the basics. I had a little trouble with the exclude option, but I believe I have that down as well. I will work with it a lot more to figure out how to do multiple directories,etc., and eventually write a script to do all my backups together rather than timeshift for system and rsync for personal files. Many thanks to TheFu for the help. I will mark this thread as solved, and do MUCH more studying. The one thing I'm still wondering is in reference to renaming files. I have a lot to rename and don't want to end up with a partition full of duplicates. I'm sure I'll get it figured out soon. Wish me luck, and you can expect to hear from me again.

---

### Post by oldfred on 2020-10-11
I was getting duplicates and since copying from one system to another, would houseclean on one system, but then restore from other system would restore duplicates.
I then added the parameter --delete.
I have multiple versions of similar scripts, on on each flash drive.
Sometime I just do everything, others may have separate line for each folder as flash drive is smaller & cannot hold all of my data partition's data.
I also include checking that partition is mounted and some other things as part of my script.

SOURCE="/mnt/data"
DEST="/media/fred/data256"
TODAY="$(/bin/date '+%Y-%m-%d')"
MODEL="z170"
SYSVER="$(lsb_release -cs)"
FN=$TODAY"-"$SYSVER"-"$MODEL

rsync -aruvlP --delete $SOURCE $DEST
rsync -aurvP --delete --exclude-from=backup_excludes.lst /home $DEST/home_$FN

I have a separate backup_excludes file. I may modify that to exclude the folder, but now only use for data in /home that does not need to be backed up. Lots of small hidden files in .cache and some other places. I try to houseclean a lot of that before backup, also.
I added some folders to my exclude list from these:

[https://askubuntu.com/questions/320458/how-to-exclude-multiple-directories-with-rsync](https://askubuntu.com/questions/320458/how-to-exclude-multiple-directories-with-rsync)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) & 
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

---

### Post by dragonfly41 on 2020-10-11
> [COLOR=#000000]The one thing I'm still wondering is in reference to renaming files.[/COLOR]

If you have Synaptic Package Manager installed, search "rename" and there are several tools you can try for batch file renaming.

---

### Post by coley9225 on 2020-10-11
Thanks for the additional tips. I know that 1 purpose of having backups is to recover files/directories if they are deleted by accident, so I'm hesitant to use the --delete option. I do have an alternative idea, since I have more than enough external storage, to cover my bases. I will use 1 partition to do daily backups, using the --delete option. I will also use a 2nd partition to do weekly, or monthly, backups without the --delete option. In this way, the files deleted from the daily backups are available to restore if the deletion was a mistake, since linux doesn't use a "recycle" bin. And, as for bulk renaming my files, I don't think that will work for what I need. What I'm going to do is rename files like:
184161+1861581.jpg   to John _at_beach_10_6_20.jpg
145665845555664.jpg  to  Kids_new_swingset.jpg
24852456255png  to  my_new_car.png
Name changes of that sort.
Again, many thanks for all the great tips and advice.

---

### Post by TheFu on 2020-10-11
**qmv** might be useful for bulk renaming.  I use it for similar needs.

If you want versioned backs, perhaps using a tool that does versioned backups makes since? **rdiff-backup** is very much like rsync, but with built in versioning.  There are other tools, but rdiff-backup is what I've used 8+ yrs. Before that I had some ugly rsync scripts.

---

### Post by HermanAB on 2020-10-11
Don't re-invent the wheel.

Read this: [https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html)

---

### Post by dragonfly41 on 2020-10-12
> [COLOR=#000000]What I'm going to do is rename files like:[/COLOR]
[COLOR=#000000]184161+1861581.jpg to John _at_beach_10_6_20.jpg[/COLOR]
[COLOR=#000000]145665845555664.jpg to Kids_new_swingset.jpg[/COLOR]
[COLOR=#000000]24852456255png to my_new_car.png[/COLOR]
[COLOR=#000000]Name changes of that sort.

This triggered a thought.
There are occasions when say after using photorec for data recovery there is a large
set of images which have only numbers as names. They need to be categorised.
A brief search shows that others have used machine learning algorithms to
attempt to classify such images into bins.

For example the algorithm might be "trained" from examples to look for beach, garden, car, pet, face images.

[Here is one blog I found.]("https://blog.machinebox.io/how-anyone-can-build-a-machine-learning-image-classifier-from-photos-on-your-hard-drive-very-5c20c6f2764f")


[/COLOR]

---

