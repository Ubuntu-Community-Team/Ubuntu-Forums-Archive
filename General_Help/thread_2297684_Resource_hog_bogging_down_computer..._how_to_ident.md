---
title: "Resource hog bogging down computer... how to identify it?"
date: 2015-10-05
forum: General Help
---

### Post by Nixarter on 2015-10-05
I have a process that is a major resource hog atm, and I am all out of guesses.  How do I identify the culprit?

I assumed it was a file indexer, but all the ones I could find (nepomuk, updatedb) are not on my computer.  I found that whatever the file indexer is, it is likely called by anacron... so I uninstalled that.  (yes, I'm desperate)  That seems to have helped prolonged periods of being absolutely useless (though I don't know which program that was being scheduled caused the issue), but it still takes a massive amount of time to do simple things like navigate file structures in a file browser.  Simply double-clicking on a folder with a single item it it takes 5-30 seconds to open same for files.  However... once opened, they run just as fast as normal.  Videos/audio as well.  So it may be an issue with something other than a file indexer.  Maybe my file browser itself is having issues?  I have also been unable to find any ~/.local/ folders that contain indexes.  so I'm really confused.  SOMETHING is happening lol

I have a couple very large databases (in one, there are gigabytes of files under about 100kb, and hundreds of thousands of ~1kb files), and I'm beginning to wonder if their mere existence is somehow causing something to break.

same issues on 14.04 ubuntu, and 17.2 mint.  :/

any ideas/suggestions?

---

### Post by coldraven on 2015-10-06
Have you tried running the "top" command to see which process is using the most resources? Press"Q" to quit.
```
top
```

---

### Post by buzzingrobot on 2015-10-06
Launch System Monitor.  You can click on the column labels -- Name, CPU, Memory, etc. -- in the Processes tab to sort the entries in ascending or descending order. You may want to tell it to list "All Processes" and then do a refresh (check the menu options).

Probably a mistake to remove anacron since it is used to schedule necessary system operations.  And there are a number of other ways this process could be launched periodically.

Desktop search tools that depend on indexing all files on the drives may, in fact, consume a lot of system resources during the initial indexing. Once that's done, only new data on is indexed, and that's usually not an issue.  If it is that initial run that's the issue here, the best bet is to let it run to completion. The settings tools offered by different desktop environments may offer ways to configure which drives are indexed. E.g., you may not want an attached external drive used for backups to be indexed.

But, in any case, first thing is to identify the culprit process.

---

### Post by Nixarter on 2015-10-06
I already tried system monitor, but i could never find out which process was using the HDD so much.  I'll keep your suggestions in mind, though.  Thanks

Also, Thanks for the TOP suggestion.  That should prove useful.

And update on the problem:  After restarting the computer, the problem seems to be gone.  I did a hard reset after killing off the scheduler (and after I posted the above), and everything has been running peachy so far.  No more file delay when opening folders.  Whatever was causing it was apparently called by that anacron scheduler.  With that gone, nothing has initiated.  I am slightly worried that important things wont be done with that gone (like updates and whatnot... although I don't know about many scheduled tasks.  I'm sure there are a bunch).  I can just remember to manually update, though.

It has been liek 10-15 hours and still no issues, so it may be gone for good.  I'll keep it updated if anything changes.  I'll mark it as solved in a few days if all stays well and good.

For those with similar issues, if this does stop it for good, I can't say I recommend doing it this way.  I almost certainly have stopped some important processes from being scheduled.  With more research and time I probably could have narrowed it down to the single process that was causing all the issues.  I just don't have the time atm.  It is a mostly fresh install, so if I kill something, I can just reinstall Linux and not really lose anything.  I uninstalled anacron with that in mind.

---

