---
title: "Strange Disk Space Problem"
date: 2007-06-07
forum: General Help
---

### Post by wiz561 on 2007-06-07
Hi!

I have an issue with drive space.  It seems like I don't have much installed on my drive, but yet it somehow takes up 40 gig and runs out of space in a few days.  I have no clue where these files are either that are causing me my headaches.  I ran a find / +500M to look for all the files over 500M, but they are on a different drive than the one that constantly runs out of space.

Just a few minutes ago, I deleted a ~300 meg file.  I did a df -h before and after.  Before I deleted, I had 7.7 gig available.  After I deleted the file, I had 8.0 gig available.  10 minutes later, I do the df -h again, and now I have 7.8 gig available.  What in the world is going on!?!?

I've also checked /lost+found and there are no files in there.  I also don't have a ~/.Trash either.  The only thing I can possibly think of is related to zoneminder.  I have a script that runs that does a wget on a wireless IP cam I have setup.  It stores the file in /tmp/something.jpg.  Every couple of seconds, it overwrites the file in /tmp with the new one.  In the perl script, it is...

open OUTF, "> /tmp/hawking.jpg" or die "Can't open $outfile : $!";

Now, I'm guessing that the above line overwrites the file and the original file doesn't get stored elsewhere on the file system, right?  Are there any other areas where I can look to see what's going on?


Thanks,
mike

---

### Post by wiz561 on 2007-06-07
d'oh.  After I hit submit, I remembered something.  With zoneminder, it stores ALL of the video in the web server directory.  I checked it out and it looks like that is where all my space is getting used.  

Too bad there's not a delete for a posting on these forums!  :-)

---

