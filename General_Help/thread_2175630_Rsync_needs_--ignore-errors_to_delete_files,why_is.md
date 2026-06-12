---
title: "Rsync needs --ignore-errors to delete files,why is that?"
date: 2013-09-20
forum: General Help
---

### Post by cogset on 2013-09-20
I've just found out that all my rsync backups include a large amount (around 35.000 files in total) that are no longer on the source:I have several backups on different drives,and upon restoring one of these on a new hard disk for a test,I spotted some files on the desktop that I had deleted months ago,then I've had a look in my home directory and found lots of stuff that was not supposed to be there anymore-long story short,rsync has not been deleting lots of files that was supposed to delete,in all my backups.

After some tries using --dry-run to avoid issues,I've discovered that only using the** --ignore-errors** option I can delete those files,which are mostly old firefox backups and old pictures in my home directory,but there's also stuff in  /usr/lib or /var/log that needs to be deleted.

So,why is this happening and should I run all my backups with the **--ignore-errors **option from now on? Is it safe?

---

### Post by Habitual on 2013-09-20
without knowing what the exact syntax of the rysnc command or script, it's hard to tell.
Personally, I use and advocate something like
```
cd ~ && rsync -avz --no-perms . /media/Keepers --exclude "/home/jji/.gvfs" --exclude "/home/jj/.cache/" --exclude "VboxVMs/"  **[COLOR=#ff0000]--delete[/COLOR]**
```
Where /media/Keepers is my USB Drive mounted with 
/dev/sdb1     /media/Keepers ntfs-3g    rw,uid=1000,gid=100,dmask=022,fmask=133 0 0
**[COLOR=#ff0000]--delete[/COLOR]** will remove files **at the destination that do not exist on the source** when it is run.

This has kept my backups in sync for months, exactly, file for file.
does your rsync command/script have a --delete option?
Maybe a combination of --ignore-errors  **and** --delete?

man rsync for those options or
[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

hope that helps you out.

---

### Post by Kirboosy on 2013-09-20
It looks like other people have been afflicted with this bug as well. 

[Rsync not deleting files on destination]("http://ubuntuforums.org/showthread.php?t=1745350")

You might want to use ```

 -n, --dry-run               perform a trial run with no changes made
```

Just to make sure nothing is wrong with the new configuration. 


Hope that helps!
~Caboose

---

### Post by cogset on 2013-09-20
Thanks for your replies,and sorry for forgetting to post the rsync command I'm using,which is 

```
sudo rsync --delete -avv --progress --exclude='/mnt' --exclude='/media' --exclude='/proc' --exclude='/sys'  --exclude='/dev'  --exclude='/tmp' --exclude='/var/run'  --exclude='lost+found' --exclude='VirtualBox VMs' --exclude='/home/ubuntu/.thumbnails'  / /media/backup_device
```

as you can see,the **--delete** option is obviously there and yet those files which I'm positive are  no longer on the source (namely,my current operating system,mostly my home directory) are not being deleted on the destination device:I've done many tests using --dry-run,and apparently the only way to delete such files using the command above is  to add to it the ** --ignore-errors** option.

Unless,I simulate synchronizing _only some specific subdirectories inside my home directory_   (like,say,firefox backup profiles) with their backup copy,in which case file deletion succeeds even without the --ignore-errors option:why is that?

Is this really some kind of bug in rsync,or is there anything wrong with my command above? I did not see this coming,as I've said I've only discovered it by accident while doing a test of  restoring my system on a new hard drive.

_Edit_:since I'm doing this from a running system whilst logged in as superuser (using sudo,I mean),would possibly make a difference if I'd do this with all partitions unmounted,i.e. from a live CD or while booted in another OS (I have a multi-boot set up) ?

---

### Post by cogset on 2013-09-24
Update:well,of course I did not mean really "unmounted",I rather  actually meant "from a non-running system" (accessing partitions / and home from another OS),in which case I can report  that interestingly rsync works properly and deletes the old files   without needing the -ignore-errors option.

Come to that,does anybody have a clue about why this happens?

---

### Post by cogset on 2013-09-30
I may have found the cause:excluding the directory **.gvfs** solved the issue,as the IO error that caused rsync to skip file deletion was indeed related to this directory.

I knew that it was not meant to be backed up,but I wrongly assumed that rsync would be skipping it without side effects-which clearly wasn't the case.

---

### Post by Habitual on 2013-09-30
I just checked my target for backups and it has the .gvfs directory, even though I have excluded it.
Bizarre.

rsync  version 3.0.9  protocol version 30

---

### Post by cogset on 2013-10-01
On this system,I have rsync  version 3.0.7  protocol version 30 -I might have to check which version I have on Mint 13,that had the exact same issue with rsync.

---

### Post by Habitual on 2013-10-03
Well, if it all worked without issue, we'd have nothing to do, heh?

One thing I see in your command is [COLOR=#ff0000]--exclude='VirtualBox VMs' [/COLOR]
Who's VirtualBox VMs? All? some? someone's? 
You can specify *patterns* in the /root/rsync.excludes file described below. see ```
man rsync
``` for specifics on 
**--exclude-from=FILE     read exclude patterns from FILE**

There's an Ubuntu user? Or is that **your** userid? (sorry, I don't use Ubuntu)

You may wish to try this approach...stolen from [here...]("http://articles.slicehost.com/2007/10/10/rsync-exclude-files-and-folders")
as root
```
 vi /root/rsync.excludes
``` and add 

```

/mnt
/media
/proc
/sys
/dev
/tmp
/var/run
/lost+found
/VirtualBox VMs 
/home/ubuntu/.thumbnails
```

and **[COLOR=#ff0000]*test*[/COLOR]** it with
```
sudo rsync --delete -avv **[COLOR=#ff0000]*--dry-run*[/COLOR]** --progress --exclude-from=/root/rsync.excludes /  /media/backup_device
```

If it appears to be working as expected, the remove the --dry-run from the command. 
I ran it in dry-run mode and even though it said "Deleting ...." I was pretty nervous seeing it. They were NOT deleted using "dry-run".
It really is just a dry-run.

Good luck and I'll check back tomorrow.

---

### Post by cogset on 2013-10-05
As for  [COLOR=#ff0000]--exclude='VirtualBox VMs' [/COLOR],that is a pattern to exclude my whole VirtualBox VMs directory,as I couldn't figure out how to quote (for the embedded space) and enclose in** --exclude=' '** at the same time...it works,so I've left it like that.

Talking about the **--exclude-from=FILE  **approach,that's interesting and definitely neater than writing a lot of exclusion rules (indeed,I may give it a shot and make a dry run test),but what other advantage may it give in this specific case? Given that apparently the culprit was the .gvfs directory,and excluding it makes rsync work as it should,I take there would be no difference in using a file or manually writing the exclusion rules one by one ?

---

### Post by Habitual on 2013-10-05
Strictly personal preference, but I tend to Avoid Repetitive Tasks after 20 years in IT, so I use techniques that keep it that way, in scripts.sh
Prevents accidental typos also. ;)

As usual in Linux, there's more than one way to get 'er done.

---

