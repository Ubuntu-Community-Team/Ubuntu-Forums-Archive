---
title: "Can anyone point me to a Grsync tutorial?"
date: 2019-04-26
forum: General Help
---

### Post by mmmmna on 2019-04-26
Ubuntu 18.04 and Cinnamon.
Last updated Wed Apr 24 20:27:18 2019


Just starting to get familiar wth Grsync.
Local to local backup is what I've done and will be the norm for me.

A few weeks ago, I succeeded in backing up several USB 2.0 based storage to an external USB 3 external hard disk.

I tried to back up one device last night, I thought I selected sensible options, but I had a surprise.

Can't quickly post a screenshot...

Grsync options I've selected (placed a check mark):
Under Basic:
Preserve time, Preserve owner, Preserve permissions, Preserve Group
Ignore Existing, Skip Newer, Show Transfer Progress,
The remaining options are unselected.

Under Advanced options:
I selected Protect Remote args.

Under Extra options:
Nothing is selected.


What actually happened:
Every file on the source media was copied to the destination, this backup took over an hour to copy 68 Gb

What I expected:
Only a few dozen files have been changed or added, I expected the process to skip existing files and only update or add the changed files; I expected maybe 20 minutes to complete at most.

Any ideas where I should place check marks?

---

### Post by Rubi1200 on 2019-04-26
This seems to be a fairly recent tutorial:
[http://averagelinuxuser.com/linux-backup-with-gui/](http://averagelinuxuser.com/linux-backup-with-gui/)

Have not used Grsync so unable to comment on whether this gets you further but hopefully will be of help.

---

### Post by dragonfly41 on 2019-04-26
> [COLOR=#000000]What actually happened:[/COLOR]
[COLOR=#000000]Every file on the source media was copied to the destination, this backup took over an hour to copy 68 Gb[/COLOR]

I suggest that you research when to add closing slash and when not to add closing hash to source/destination paths.

I don't have a link just now but google search for advice.

Another tip is to try a dry run before the actual run. This will avoid filling up your drive if slashes are incorrectly used.

---

### Post by Tadaen_Sylvermane on 2019-04-26
Know nothing about Grsync, but it's just a front end for command line rsync.

```
rsync -auv --progress $source $target
``` should do it, or close. Gui makes way to hard.

Research a command on the cli for 5 minutes. Will take less time than figuring out the GUI tools that do a very pathetic job at doing command line tasks. It's not scary.

---

### Post by speartip on 2019-04-27
I agree with the above poster.
I had problems with grsync so googled arould for a few minutes and started using the command line instead. Here are a few commands that I use that you can amend & play with:
For a dry run I use:
```
[FONT=Carlito]rsync -avzn /storage /media/veracrypt6/Rsync_Backup[/FONT]
```
So "storage" is the folder I am backing up, the destination is a partition I encrypted using veracrypt, where I created a folder called Rsync_Backup, to hold the backup.
The 'n' in avzn, shows only what would be done.
If I want to run for real, then:
```
[FONT=Carlito]rsync -avz /storage /media/veracrypt6/Rsync_Backup[/FONT]
```
If I wanted to checksum the Backup, (which takes considerably longer) I would add a 'c', so:
```
[FONT=Carlito]rsync -avzc /storage /media/veracrypt6/Rsync_Backup[/FONT]
```
Hope this helps.

---

### Post by mmmmna on 2019-05-01
Thanks for all the replies.

I asked about Grsync mostly because I was using that for copying source files to a backup. I know there is a cli beneath all of this.

Using the Grsync graphical interface, the process was ultimately backing up all the source files, even those files which had not changed. Not saving much time that way!

I figure I'll do dry runs until I understand where the correct settings will be found while I'm using Grsync. Then, if Grsync can't get to a mode where the second backup  is only working on changed files, I'll see if the developer has a suggestion.

Again, thanks for the assistance!

---

### Post by rbmorse on 2019-05-01
What you describe happens to me when I don't properly specify the destination directory and grsync goes where I tell it and finds no prior backup, so it ends up copying the entire source directory.   It usually ends up being one directory above or below where I really want it to go, but I've also specified the wrong hardware device on more than one occasion. 

Best practice for me is to set the source and destination directories using grsync's GUI...check the little block at the end of the source and destination lines and use the file browser to navigate to the correct places.  This method induces fewer errors for me than any other. 

And yes, if I know what I'm doing, have time to concentrate, not distracted by intractable problems forced upon me by dim, lazy and untalented supervisors,  not suffering from chronic lack of sleep or amusement and not particularly drunk, using rsync via the command line is a much more efficient way.  However, by the time of the day I get around to thinking about backup, I seldom meet all the prerequisite conditions.  It would be embarrassing if I worried about such things.

---

### Post by dragonfly41 on 2019-05-01
I refer to post#3 where I wrote ..

> [COLOR=#000000]I suggest that you research when to add closing slash and when not to add closing hash to source/destination paths.[/COLOR]

This point is explained further if in Grsync GUI you click on Basic Options tab and then the question button alongside "Source and Destination".

---

### Post by TheFu on 2019-05-01
Put me in the "use rsync, not grsync" group, but only if you want a quick and dirty mirror.  If you want a backup, there are better choices with options similar to rsync, but that handle the versioning, permissions, 

rsync between storage on the same computer doesn't do differentials by default.  If you want that, you'll need the -no-whole-file option and you'll need to understand the caveats in using it.  Over the network, rsync does to block comparisons by default.

If you plan to run this mirror weekly, it is best to script it, so exactly the same options, exactly the same source and exactly the same target are used.
USB2 is slow. If you mount it using a GUI, it will be 30% slower than it need be.  gvfs is slow.

I've never had luck with GUI back tools, and actually, for rsync to be more than a way to mirror or mirror and add files makes learning a real backup tool make more and more sense. rsync for backups has a number of limitations, especially if the file systems between the source and target are different. For backing up a single HOME, this might not matter too much, but if there is more than 1 userid or any system files, forget it.

Running almost all GUI tools with sudo/root is a bad idea for a number of reasons.  You can read up about that elsewhere.  For people new to Unix, it is just easier to say "don't, ever" then try to explain when it is ok.

To mirror a directory with storage connected to the same machine, this is what I use.```

#!/bin/bash
EXCLUDES="--exclude .Trash-1000 --exclude lost+found --exclude .cache"
ionice rsync -avS --stats --progress $EXCLUDES --delete /D/ /misc/b-D/
```
This deletes any files that aren't in the source. Notice the trailing slash? Out of all the gotchas in rsync, that is probably the most important one to learn. The trailing slash on the target doesn't matter, but I always use it as a reminder for the source. All the target files are owned by the userid running the command.

For going across the network, ```

ionice rsync -avzS --stats --progress $EXCLUDES  /D/ userid@server:/misc/b-D/
```
rsync over the network uses ssh for the tunnel, by default for about the last 15 yrs.  You can push or pull the files or have 3 systems involved, A, B, C where A ---> B but C is used to pull then push the files to B.  All the target files are owned by the userid specified in the TARGET part "userid" in this case.

Only root or root-equiv accounts can retain the userids in rsync that aren't the current userid.  rsync follows normal Unix file and permissions. Even with root, specific options are required to retain permissions, users, groups, and ACLs.

manpages for commands with hundreds of options, like rsync, are very useful```

       --size-only
              This  modifies rsyncâs "quick check" algorithm for finding files
              that need to be transferred, changing it  from  the  default  of
              transferring  files  with  either  a  changed  size or a changed
              last-modified time to just looking for files that  have  changed
              in  size.  This is useful when starting to use rsync after using
              another mirroring  system  which  may  not  preserve  timestamps
              exactly.
```

The rsync manpage has plenty of examples.  Best to check what every option means.

This doesn't handle hardlinked files in the way someone might wish. There is another option for that. Using hardlinks is common to get rsync to be used for versioned backups. If you don't specifically use hardlinks, then you 99% aren't using any.
The -S does handle sparse files, which may not be necessary.  I've been burned, so I include it in backups.  Once a 2.4MB sparse file was exploded to 50GB and filled the target storage.


For backups, something like rdiff-backup, which handles versioning and a few other things that rsync doesn't without extra effort would be worth using.  I use rsync only for huge media files.  For everything else, rdiff-backup with 60 - 180 days of versioning is the better choice, almost always.

---

