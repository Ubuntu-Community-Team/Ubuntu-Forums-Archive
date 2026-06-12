---
title: "Need to remove files (3+ Days old) from directory"
date: 2008-05-07
forum: General Help
---

### Post by rjm1982 on 2008-05-07
Ok, I'll try to be as descriptive as I can be.

Here is the basic structure of the files we're working with.
```

/
---fileserver/
------user1/
---------projects/
---------daily/
------user2/
---------projects/
---------daily/
------user3/
---------projects/
---------daily/
```

I need to come up with a script to clear all files in userX directories older than 3 days.  The trick, is I want to avoid the  "projects" and "daily" folders, but delete any other folders they may add.  Basically, this is a "dump" for files they need to get to themselves without cluttering up the other directories.  (they can access this from in the office, or from outside with sftp, so its a handy place to drop a file)

I just need to remove all files that arent specific directories that are over 3 days old...  I will put this as a cron job to run nightly.

I dont think it matters much, but this is on 7.10

---

### Post by andrewc6l on 2008-05-07
A naive way to do it (which users could get around, but which might be good enough):

```
# Delete all files that are older than 3 days since last modified
# (which aren't in daily or projects)
find /fileserver -mtime +3 -type f | grep -v projects | grep -v daily | xargs rm
# Delete all directories that don't have projects or daily in their path
find /fileserver -type d | grep -v projects | grep -v daily | xargs rm -rf
```

You would want to test it with xargs echo before actually putting rm /rm -rf in the script to make sure you're getting what you want, of course. 

The trick is to generate the whole list of files to delete, then exclude the ones you don't want to delete with grep -v. Life gets more difficult if users have files with spaces in them... then you'll need find -print0 and xargs -0.

---

### Post by rjm1982 on 2008-05-08
Thanks, I'll start with that..

I'm not worried about them working around it...we're a small shop with just 12 people...mostly designers.  None of them would do anything malicious and if they wanted something to be more long term, they would just ask me how...

Thanks again!

---

