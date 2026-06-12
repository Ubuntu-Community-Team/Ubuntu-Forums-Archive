---
title: "Tracker indexes, but shows no results?"
date: 2007-10-20
forum: General Help
---

### Post by sancho panza on 2007-10-20
Tracker used to work fine for me till recently, it used to index and show results and seemed to do what I was wanting. Coupla days back, I noticed that it does not show any results for file that exist in my home dir. I have not made any changes/updates in tracker in a long time, so this is totally out of the blue. This is almost identical to what is shown in the screenshots on [this thread]("http://ubuntuforums.org/showthread.php?t=578923&highlight=tracker").
Anyone else has this problem?

---

### Post by wyth on 2007-10-21
Houston, we have a bug.

Same story here.  For about a week, it tracked and indexed and showed everything.  Today, I did a search, and all it will show is my emails.  

I had trouble like this in the past before Tracker was included -- I was trying it out.  Trying to track down the tracker problem myself, now.  When I've asked about this issue over at the tracker IRC, etc., seems I was the only person who ever had such a problem.  Not anymore.

*EDIT*

Got this tip from [here]("http://ubuntuforums.org/showthread.php?t=578923&highlight=tracker&page=2"):

First, in your session, make sure you kill trackerd

Then at the terminal run:

```
 trackerd -v 2 -R
```That will reindex everything, and should take care of any issues.  Seems something might have been jacked up in an upgrade.

---

### Post by dmglouis on 2007-10-21
Wow, that fix worked beautifully for me. And it didn't take long either. Tracker is now fully functional for me!

---

### Post by sancho panza on 2007-10-22
That fix seemed to have work for me too. But is it a complete fix? Could this problem crop up again? What if I change the indexing preferences? I'll wait a while before marking this as solved.

---

### Post by matt1980 on 2007-10-24
> **wyth said:**
> 
First, in your session, make sure you kill trackerd

Then at the terminal run:

```
 trackerd -v 2 -R
```


Interesting...I was having a similar problem, I did this, and after a good while, trackerd segfaulted! There were two emails in Evolution (spam messages, of course) that it didn't like. After I deleted them (took me two tries to find both of them) trackerd finished indexing, and seems to be working great, for the moment. I guess I'll see what you've got to do to file a bug report...I've got the emails saved to disk. But if you try this, make sure the *long* output doesn't end in a segfault! Otherwise, it didn't work. Actually, the process doesn't end by itself if it works, it keeps watching for additional changes, at which point you have to kill it...otherwise searches don't seem to work until you do.

---

### Post by ayoli on 2007-11-05
> **wyth said:**
> Houston, we have a bug.

Same story here.  For about a week, it tracked and indexed and showed everything.  Today, I did a search, and all it will show is my emails.  

I had trouble like this in the past before Tracker was included -- I was trying it out.  Trying to track down the tracker problem myself, now.  When I've asked about this issue over at the tracker IRC, etc., seems I was the only person who ever had such a problem.  Not anymore.

*EDIT*

Got this tip from [here]("http://ubuntuforums.org/showthread.php?t=578923&highlight=tracker&page=2"):

First, in your session, make sure you kill trackerd

Then at the terminal run:

```
 trackerd -v 2 -R
```That will reindex everything, and should take care of any issues.  Seems something might have been jacked up in an upgrade.

Thanks for the tip :) It seems that it resolved the issue for me.

---

### Post by eitan on 2007-11-25
ok, so i'd like to get tracker to index /usr/share/doc so i 
could search documentation, manuals, etc..

so i used the indexing preferences to add /usr/share/doc to 
  "additional paths to index and watch"

then for good measure i had to kill trackerd and ask it to
reindex.

then for good measure i waited like half a day.

when i do a search (by file name) for a file that i know is 
in /usr/share/doc it finds nothing.

i'm guessing perhaps trackerd is running with not enough
permissions to touch the files outside my home dir???
is there a log file to get a glimpse of the success/failure
to index?

the other weird thing i have *sometimes* seen is
tracker find tool saying
"i found 17 documents" but it shows you only 2.
or "i found 236 thingamabobs" but shows you only
seven.

---

### Post by eitan on 2007-11-25
update:  i tried this again and it works now.  i suppose i had to wait
a little longer for it to finish indexing.  it'd be nice if there was some
visibility into this.

but it works now.

thanks, / eitan

---

