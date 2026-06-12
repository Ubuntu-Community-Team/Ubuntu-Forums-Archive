---
title: "Deleting files doesn't quite delete them"
date: 2018-03-11
forum: General Help
---

### Post by Adam_Jacobs on 2018-03-11
I have a shell script which runs every day via crontab. One of the things it does is delete some files (using rm).

Except that it doesn't completely delete them. It deletes the original file, but then leaves a small file in the place of the original file. If it tries to delete a file called "myfile", then the file it leaves behind is called "Old file myfile deleted". That file is a text file that contains the date and time that the file was deleted.

Any ideas what might be going on here?

Running Ubuntu 16.04.

---

### Post by TheFu on 2018-03-11
The process using the file isn't happy about the deletion?  File names and locations and the programs using those files would provide leads.

---

### Post by Adam_Jacobs on 2018-03-11
The files being deleted are at least a week old, and nothing should be using them, so I'd be surprised if there was a process using the files.

I suspect that this may be something to do with running the script as a cron job. If I run it manually, the files are deleted perfectly normally without the small files being created.

---

### Post by dragonfly41 on 2018-03-11
Intrigued, I searched around and found this ....

[https://www.linux.com/news/bring-back-deleted-files-lsof](https://www.linux.com/news/bring-back-deleted-files-lsof)

Is that related to your scenario?

---

### Post by TheFu on 2018-03-11
You can always use **lsof** to see if any process is using the files.  I'd use it with grep.   So, if I'm still editing a file from a different system and don't remember until I see the lock from another, ....
```

$ sudo lsof |grep {unique part of filename}
```
is how I'd find the process using the file.  There are probably a few other methods. Also, it assumes that at the instance the lsof is run, that the process responsible for renaming the file is running. Hard to say,but I'd think that unlikely unless it is a GUI program.

I've been running cron stuff for multiple decades.  Nothing in cron would do that.

---

### Post by Adam_Jacobs on 2018-03-12
Well this is strange. When it ran last night everything got deleted properly. The only thing I changed was to add the -v flag to rm and got it to write the results of rm to a logfile to see if that gave me a clue about what was going on.

I'd be surprised if that did the trick. Maybe it was some temporary glitch which has now gone away.

Anyway, thanks for the suggestions. Perhaps I should try investigating with lsof if the problem recurs.

---

### Post by TheFu on 2018-03-12
Almost all issues with cron are traced back to environment stuff. Different PATH, different aliases, not specifying exactly which programs should be used fully.
In the old days, we had to specify which set of core tools we wanted - BSD or SysV style.  They have different options and some of the same options mean different things.  Usually each individual would pick their defaults by setting up their PATH.  GNU versions of these tools eventually merged most of the options so it wasn't nearly as important.   Unless it is.  Then scripts, especially when run from cron, would probably find the other version and not behave properly/as expected.

So, this leads to some standard "best practices" for cron and other scripts that are shared by different userids.  The first of those is to always specify the full, complete, path, for every program run.  Don't say "rm", say "/usr/bin/rm" or "/bin/rm". Be precise. Be exact. 
The 2nd rule is NEVER assume some environment variable is set in cron, unless you set it.  For example, HOME isn't set. There are lots of other examples.  Environment variables set at login for a specific userid ARE NOT SET in cron.  This is a security feature.

Is this a hassle? Yes.
Is it extra work?  Yes.
Is it necessary?  Yes.

Care to post the script?  We all write scripts with assumptions - some of mine at home are really crap.

---

