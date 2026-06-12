---
title: "rsync doesn't seem to do anything"
date: 2014-05-23
forum: General Help
---

### Post by scottbomb on 2014-05-23
I have a folder full of other folders of picture files and I keep a backup on an external HDD. I'd like to execute a command to make all of the new files and folders copy over to the backup (recursively, of course) and it should only copy those files and folders which do not yet already exist on the destination drive. From what I've read, the command should be:
```
sudo rsync -av --ignore-existing /source/folder /destination/folder
```

But this is all I get:
```
sending incremental file list

sent 266,983 bytes  received 401 bytes  178,256.00 bytes/sec
total size is 17,397,777,420  speedup is 65,066.64
```

And nothing is actually copied. I have an entire folder called /Pictures/Family/2014 on the source drive and it still doesn't appear on the destination drive after running this command. What am I doing wrong?

---

### Post by PJs Ronin on 2014-05-23
Two things.   First, I think rsync automatically skips files that are up to date on the target location.   Second, I think you're missing a '/'.   Try this ```
sudo rsync -av /sourcefolder /destinationfolder/
```

---

### Post by oldfred on 2014-05-23
This is one of my rsync commands.

rsync -aruvlP /mnt/data/Documents /mnt/backup

It copies everything in my Documents folder into a Documents folder in the mount of my backup partition.
 When using "/" at the end of destination, rsync will paste the data inside the last folder.
When not using "/" at the end of destination, rsync will create a folder with the last destination folder name and paste the data inside that folder. 



And in my script I include this. It now looks like the r is redundant.

# backup script - mybackup.sh
# a - archive, retain file settings equals -rlptgoD (no -H,-A,-X)
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
# -l, --links copy symlinks as symlinks
# -i, --itemize-changes
# -t, --times preserve modification times
# --exclude option to prevent copying things

       Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

    But this may be better:
 Discussion of issues on rsycn bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)

---

### Post by scottbomb on 2014-05-24
Hmmm.... well the suggestion by PJs Ronin yielded the same result I got earlier. I tried oldfred's suggestion and the terminal spent several minutes scrolling through the thousands of files I have in the source folder but it didn't copy the new files and folders to the destination. There were no errors. It exited with this:
```
sent 17,402,788,124 bytes  received 243,278 bytes  46,719,547.39 bytes/sec
total size is 17,397,777,420  speedup is 1.00
```
Very puzzling.

---

### Post by papibe on 2014-05-24
> **scottbomb said:**
> sent 17,402,788,124 bytes
I'd take another look at the destination. It seems like ~1.7GB were transferred. Usually if rsync print a file name, it is because it is being transfered.

Regards.

---

### Post by vanadium on 2014-05-24
Just remove your --ignore-existing option: it tells rsync not to consider already existing files, and will cause it only to copy over new files if any. All you need is the -a option. You can add the v option to have some feedback during the operation.

Also indeed take attention for trailing slash or not: it has a different meaning.

---

### Post by The Cog on 2014-05-24
Are you sure there isn't just one folder in your destination folder? If you use this command:
```
rsync -av /source/folder1 /dest/folder2
```
then it will copy folder1 into folder2 and create /dest/folder2/folder1. If you just want to copy the **contents** of folder1 to folder2 instead, use this command:
```
rsync -av /source/folder1/ /dest/folder2
```

---

### Post by vanadium on 2014-05-24
```
rsync -av /source/folder1 /dest/
```
can be used to create a copy named "folder1" under dest.

---

### Post by Habitual on 2014-05-24
Also try adding the -n switch for "dry run" and you can get a "visual" of its intended operation.
ie: "sudo rsync -avn ..."

---

### Post by scottbomb on 2014-05-24
Finally got it! Using the "n" switch helped troubleshoot too. As it turned out, all I needed was to include a trailing / on both the source and destination and use the "r" switch for folder recursion. Here was the actual command that copied over all the new stuff:
```
sudo rsync -rv /media/Vulcan/Dropbox/Pictures/ /media/Romulus/Pictures/ 
```

Thank you everyone for your help!

Edit: I ran it again with "-av" instead of "-rv" as this seems to preserve permissions, symlinks, etc.

---

### Post by Habitual on 2014-05-24
Glad it worked out!

---

### Post by PJs Ronin on 2014-05-24
Glad that got sorted :)

Ok crew... coffee time!

---

