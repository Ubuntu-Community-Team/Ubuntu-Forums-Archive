---
title: "specific directory backup?"
date: 2018-05-26
forum: General Help
---

### Post by garyed on 2018-05-26
I have a directory with a bunch of sub directories that all have a sub directory with the same name. I want to back up only every instance of that common named sub directory & all its contents . I'm trying to find a command or bash script that will do it. If I'm not explaining things right I'll give an example.
Say I have a directory called  names: Under names  I have /names/gary , /names/jim, /names/sam etc... They all have the same named subdirecties like /names/gary/address/city ,  /names/jim/address/city ,etc. .  Is there way that I can copy all at once to another directory only  /names/gary/city & /names/jim/city etc.. ? The reason is that each one of those main directories have a bunch of subs that can amount to 100 mb that I don't really need to back up. Any ideas?

---

### Post by TheFu on 2018-05-26
100mb?  I wouldn't worry and just grab them all.
You can use rsync, but that isn't a great backup tool when used normally. Backup tools need to get versioned backups.

You can use wildcards with many tools, so **rsync -avz /names/*/city  /backup-storage/**
should work.  I've used this technique this week and for years.  It also works with cp.  I'd look to use a backup tool with built-in versioning.  rdiff-backup is my tool for backups, but I've never tried to use intermediate wildcards with it. 85% it will work. Give it a test.

---

### Post by garyed on 2018-05-26
> **TheFu said:**
> 100mb?  I wouldn't worry and just grab them all.
You can use rsync, but that isn't a great backup tool when used normally. Backup tools need to get versioned backups.

You can use wildcards with many tools, so **rsync -avz /names/*/city  /backup-storage/**
should work.  I've used this technique this week and for years.  It also works with cp.  I'd look to use a backup tool with built-in versioning.  rdiff-backup is my tool for backups, but I've never tried to use intermediate wildcards with it. 85% it will work. Give it a test.

I tried cp & rsync but the problem is they don't preserve all the hierarchy directories. I may have a hundred different names directories but all the cities for all the names will end up in the same directory. The reason I don't want to back everything up is the difference is 10 to 20 gig compared to about 5mb. I'm doing ```
rsunc -avhu
``` for incremental backups now but it takes a while as the directory gets bigger. If you or anyone else is familiar with Android Studio which is really the directory system I'm working with, you'll know how big things can get after a while.

---

### Post by monkeybrain20122 on 2018-05-26
You can use unison to back up the whole thing and sync with the original periodically. Or since it is just 100mb, you can just copy and paste it somewhere.

---

### Post by TheFu on 2018-05-26
rsunc?    Posting exact commands will get better help, since details are very important.  rsync has a test mode to see what it will and won't get, BTW.   [https://rsync.samba.org/documentation.html](https://rsync.samba.org/documentation.html) is the best documentation.  Finding examples on the web is pretty easy too.  I almost always add --progress --stats to my interactive rsync commands. The trailing / is very important in directory spec.   **rsync -avz /etc/ /backup-storage/** and **rsync -avz /etc /backup-storage/** are VERY different.

rsync does retain the files and contents.  That's sort of the point for the command.  If it isn't, then there is something wrong with the command options.

In the OP, it said "100 mb", so I took that as truth.  No mention of 10G+.  That does change things, though 10G is still pretty minor IMHO, if that is the total.  rsync is good to mirror files without versioning.  If you need/want versioning, like a proper backup tool should do, then use rdiff-backup (or some other backup tool that does proper versioning).  rsync can do versioning, but it loses changes in permissions over time. Solid backup tools retain permission changes with each version.

There are many options to rsync and similarly rdiff-backup.  You can exclude and include things as needed. Both those use regex matching or you can provide exact lists of files to be included or excluded.  If you are a programmer, then regex should be 2nd nature.  The rsync documentation has examples.   rdiff-backup will use almost identical methods to rsync.

I don't know anything about unison, but there are 500+ different ways to solve this, so there are a multitude of methods available.

---

### Post by garyed on 2018-05-26
> **TheFu said:**
> rsunc?    Posting exact commands will get better help, since details are very important.  rsync has a test mode to see what it will and won't get, BTW.   [https://rsync.samba.org/documentation.html](https://rsync.samba.org/documentation.html) is the best documentation.  Finding examples on the web is pretty easy too.  I almost always add --progress --stats to my interactive rsync commands. The trailing / is very important in directory spec.   **rsync -avz /etc/ /backup-storage/** and **rsync -avz /etc /backup-storage/** are VERY different.

rsync does retain the files and contents.  That's sort of the point for the command.  If it isn't, then there is something wrong with the command options.

In the OP, it said "100 mb", so I took that as truth.  No mention of 10G+.  That does change things, though 10G is still pretty minor IMHO, if that is the total.  rsync is good to mirror files without versioning.  If you need/want versioning, like a proper backup tool should do, then use rdiff-backup (or some other backup tool that does proper versioning).  rsync can do versioning, but it loses changes in permissions over time. Solid backup tools retain permission changes with each version.

There are many options to rsync and similarly rdiff-backup.  You can exclude and include things as needed. Both those use regex matching or you can provide exact lists of files to be included or excluded.  If you are a programmer, then regex should be 2nd nature.  The rsync documentation has examples.   rdiff-backup will use almost identical methods to rsync.

I don't know anything about unison, but there are 500+ different ways to solve this, so there are a multitude of methods available.

Sorry about the misspelling: I use rsync -avhu source destination for most of my backups & it works fine but for this particular directory it seems wasteful & that is why I'm looking for something different just for this one directory. I use a bash script that runs rsync to back up all my important files across different computers so that is not a problem.

---

### Post by garyed on 2018-05-26
> **monkeybrain20122 said:**
> You can use unison to back up the whole thing and sync with the original periodically. Or since it is just 100mb, you can just copy and paste it somewhere.

If it was only 100 mb that wouldn't be a problem but that is just one of the sub directories. There is probably about 100 sub directories in the directory I'm trying to copy. Some of them are closer to 200mb so i'm talking about 10 to 20 gb instead of just a few mb of data that I really need backed up.

---

### Post by TheFu on 2018-05-26
And the --excludes option?

---

### Post by garyed on 2018-05-26
> **TheFu said:**
> And the --excludes option?

Thanks, that sounds like a good idea so i'll experiment with that.

---

