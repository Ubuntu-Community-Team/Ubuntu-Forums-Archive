---
title: "Remove all but newest directories"
date: 2018-01-26
forum: General Help
---

### Post by raleigh3 on 2018-01-26
I need help for a script that will remove all but the newest of these types of directories.
  
I know I need rm.

  ```

01-16-18-img
2018-01-26-11-img



```

---

### Post by TheFu on 2018-01-26
> **raleigh3 said:**
> I need help for a script that will remove all but the newest of these types of directories.
  
I know I need rm.

  ```

01-16-18-img
2018-01-26-11-img



```

Without seeing **all** the other directories that you DO NOT want removed, how can we guess?  Also, what have you tried?  Is the name the only thing?  Are there mtime/ctime/atime for the directory which could be used for filtering?  Like, it is common to remove all files/directories over 90 days old. That is trivial with* find -ctime +90d -delete*.  Be careful running that - it needs a starting directory level that is safe.

---

### Post by raleigh3 on 2018-01-26
I do not understand this. "Are there mtime/ctime/atime for the directory"

```
01_06_2018img  2018-01-26-11-img  Family_Movies_AND_PICS  MAXTOR_SDB2
01-16-18-img   Clonezilla_Images  lost+found          SDB2_Mountpoint
```

---

### Post by TheFu on 2018-01-26
A web search of those terms found this: [https://www.unixtutorial.org/2008/04/atime-ctime-mtime-in-unix-filesystems/](https://www.unixtutorial.org/2008/04/atime-ctime-mtime-in-unix-filesystems/)

For example, I create weekly backup version reports on Sunday mornings for all the systems here. This runs on the backup server.  Each report is a text file with a date-stamp in the name.  Eventually, I'd have 52 x the number of systems being backed up files.  Directories with too many entries get slow and there is a real risk of data corruption. Plus, since I only have 120 days of versioned backups, at most, for each server, keeping more than 120 days of those reports really isn't helpful.

Anyway, rather than manually clean up the old report files, the script that creates them also cleans up the old ones.
```
find $OUT_DIR -maxdepth 1 -type f -iname inc-sizes\* -mtime +90 -delete
```
is the exact line from the script.   I could use ctime instead of mtime. They are the same in this case, since the files are never modified after creation.

The *find* manpage explains all the other option/switches.

---

### Post by steeldriver on 2018-01-26
If you have zsh then you could do something like this: [Remove all files within directory older than the most recently added ten files](https://askubuntu.com/a/930709/178692)

--

---

### Post by raleigh3 on 2018-01-26
Before I run this since it will be deleting dirs, how does this look

Supposed to delete all but the newest.
```
% rm -v /media/andy/MAXTOR_SDB2/2018-01-26-11-*(om[2,-1])
```

---

### Post by TheFu on 2018-01-26
I've never seen someone do it that way.  Can't tell from the info provided.  Do you want recursive directory removal?

Try **rm -i** to have it request confirmation.
Using tee to have the output go to a file AND the screen could be helpful too.
As would having a backup for anything you can't afford to lose.  Whenever doing things like this, working in a temp area during the development is very smart.

I don't know what "all but the newest" means in this case .  Is that a filename or a date on the file inodes (mtime) or are there directories?  rm doesn't do directories, except recursive (last time I check the manpage).

Basically, I just don't understand enough to say if this will do anything you want or not while NOT removing other things that happen to be there too.

---

### Post by raleigh3 on 2018-01-26
> **TheFu said:**
> I've never seen someone do it that way.  Can't tell from the info provided.  Do you want recursive directory removal?

Try **rm -i** to have it request confirmation.
Using tee to have the output go to a file AND the screen could be helpful too.
As would having a backup for anything you can't afford to lose.  Whenever doing things like this, working in a temp area during the development is very smart.

I don't know what "all but the newest" means in this case .  Is that a filename or a date on the file inodes (mtime) or are there directories?  rm doesn't do directories, except recursive (last time I check the manpage).

Basically, I just don't understand enough to say if this will do anything you want or not while NOT removing other things that happen to be there too.

I keep Clonezilla images in a directory along with other files.

I only want -img directories removed. 

So if I have three images in the directory, I would want the 2 oldest deleted.

So for these items,

01_06_2018img  2018-01-26-11-img  Family_Movies_AND_PICS  MAXTOR_SDB2 01-16-18-img  

I would want 01-16-18-img,01_06_2018img removed while leaving the rest untouched.

---

### Post by TheFu on 2018-01-26
Ah ... so I'd do this a completely different way.

Is there always, only 1 file in a directory that you want?
Are the directories deep or shallow?
Are there any empty directories that need to be retained?
Are the newest files less than 1 day old?  5 days? 30 days?  It is trivial to remove files, just files, over 31 days old, for example.

Or you'll need to write a few functions / scripts that look in every directory, 1 at a time, then sort by name (or file date), then delete all but the latest, then move onto the next directory.  This is complex enough that I'd do it in perl.

Google found a few ways to accomplish it for 1 directory, but I'm unhappy using 'ls' to create lists of files.
[https://superuser.com/questions/268344/how-do-i-delete-all-but-10-newest-files-in-linux](https://superuser.com/questions/268344/how-do-i-delete-all-but-10-newest-files-in-linux) : says: 
```
$ ls -1tr | head -n -10 | xargs -d '\n' rm -f  -- 
```

That would have to be run in every directory, so finding all of the directories that matter is the first step.
Then come back through all the directories and rmdir on any empty directories (perhaps). I didn't test any of this.

---

### Post by raleigh3 on 2018-01-26
> **TheFu said:**
> Ah ... so I'd do this a completely different way.

Is there always, only 1 file in a directory that you want?
Are the directories deep or shallow?
Are there any empty directories that need to be retained?
Are the newest files less than 1 day old?  5 days? 30 days?  It is trivial to remove files, just files, over 31 days old, for example.

Or you'll need to write a few functions / scripts that look in every directory, 1 at a time, then sort by name (or file date), then delete all but the latest, then move onto the next directory.  This is complex enough that I'd do it in perl.

Google found a few ways to accomplish it for 1 directory, but I'm unhappy using 'ls' to create lists of files.
[https://superuser.com/questions/268344/how-do-i-delete-all-but-10-newest-files-in-linux](https://superuser.com/questions/268344/how-do-i-delete-all-but-10-newest-files-in-linux) : says: 
```
$ ls -1tr | head -n -10 | xargs -d '\n' rm -f  -- 
```

That would have to be run in every directory, so finding all of the directories that matter is the first step.
Then come back through all the directories and rmdir on any empty directories (perhaps). I didn't test any of this.

Looking at your questions, it looks like the answer will be quite complex.

There are sometimes more than one file in a dir that I want to keep.

Would it help if I moved all other dirs to another partition?

Then I would only have the -.img dirs, SDB2_Mountpoint, and the trash dirs.

---

