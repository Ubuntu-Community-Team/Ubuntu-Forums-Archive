---
title: "Out of Control Log Files: Help please!"
date: 2006-11-01
forum: General Help
---

### Post by Aikon- on 2006-11-01
Okay... so I had my computer running, nothing out of the ordinary other than I had been trying to copy some DVD's earlier (without success).. when all of a sudden a message popped up saying 97% of the disk space on / was in use. I was like "ZOMG!" since I should have had several gigs free. A few minutes later, a popup comes up saying 98% was in use; I check out the system monitor and sure enough, disk space is going down at about 10MB/s. I shut down everything I had open, but to no avail, so I hard-reset my computer.

Upon reboot, turns out my /var/log is 5.4GB! The three big offenders:

syslog.0
messages.0
kern.log.0

Each of the three log files above weighs in at 1.8GB!!

I can't even open these files to look at them because they are so huge.. are they safe to delete? Any ideas as to what might have caused the problem?

Edit: I suppose the real question I'm asking is How can I go about *opening* these logs so that ***I*** can figure out what might have caused the problem?

-Aikon

---

### Post by Aikon- on 2006-11-01
/bump

---

### Post by AdNZL on 2006-11-01
I've just had a similar problem while backing up my HD to DVD. I was about to take a screen shot of it when the space freed up. it took about 30 minutes to do so, which is way to slow, so if and when it happens again I'll post the screen shot and hopefully we'll get some answers. ](*,)

---

### Post by AdNZL on 2006-11-01
:oops: OMFG thats so embarresing. Ive just figured out what I did wrong, at least I seem to have figured it out.

When I had finished burning one of the DVD's I had neglected to click the Finish button when The Dialog had asked me if I wanted to burn the disk again.

Once I hit the Finish button "Hey Presto" 4gig of HD space freed up.

Now I'm just hoping it continues to work :)

---

### Post by Aikon- on 2006-11-01
Here's a screenshot... Has been about 6 hours now, so doesn't look like its going to free itself up ><

---

### Post by AdNZL on 2006-11-02
wow.. Those are huge log files. :-k 

I just checked Mine, and even with the Dvd image still cached those log files are only a few 100k on my box.

You could always back them up and then Delete them. At least that way you could put them back if anything goes horribly wrong :neutral:

---

### Post by dcstar on 2006-11-02
Check out the "logrotate" package.

---

### Post by Aikon- on 2006-11-02
Well, they were all *.0, and after some googling I found that the currently active ones have no extension; the .X are archives; so I just deleted them and all is well.

Unfortunately, they were too huge to open with anything so I wasn't able to see what was filling them up, thus no way to find out what the problem was.

---

### Post by galileon on 2006-11-02
if you get them again, try open a terminal,

cat filename | less

that should give you them line by line...

---

