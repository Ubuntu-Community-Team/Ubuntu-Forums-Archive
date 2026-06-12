---
title: "Need help with a bash script (auto-deletion of archives)"
date: 2007-03-25
forum: General Help
---

### Post by Entity on 2007-03-25
Hi... I use rsync cron ssh to backup my data. Everything works fine and my daily backups are saved as folders using a %F-%H%M%S name syntax (i.e.: 2007-03-25-043001).

Now I would like to have a script that would delete those folders which are older than 10 days. How can I do that?

---

### Post by pupeeler on 2007-03-25
I'm not a full-fledge programmer, but I believe if you pipe the list of filenames to sed or grep in a script, then the $3 variable or something like that would let you test on the 3rd column which would contain the day of the month.  If the script runs often enough, then you could check for the day being greater than 10 days ago and basically "reverse" the math when you rollover into the next month, or work with a 30/31 day offset if it doesn't have to be *exactly* 10 days when you delete old files.  I hope someone else replies if they know more about de-concatenation.

---

### Post by stylishpants on 2007-03-26
```
find . -type d -ctime +10 -exec rm -rf {} \;

```

Replace . with the directory you want to do this operation in.

Be very careful how you use this though.  Note that it contains rm -rf and could wipe out something important if you accidentally do it in the wrong place.

---

