---
title: "System slows to a crawl for about half an hour; lots of hard disc activity"
date: 2008-05-31
forum: General Help
---

### Post by melat0nin on 2008-05-31
Hi all

I just experienced something bizarre.  I thought my Hardy had frozen after I came back to it after going to make a cup of tea, but when I moved the mouse i noticed that after several seconds it would respond.

My hard disc light was buzzing with activity, and for about 20 minutes my system was unusable while it did whatever it was doing.

There was, however, no feedback of any kind as to what was going on.  I'm now typing this from the same system, no reboot, post-'freeze'. #

I wonder if it's to do with indexing of files or something? Regardless, having the system become unusable like that with no warning or feedback is not good.

Any ideas?

---

### Post by paulphillips on 2008-05-31
If it happens again, you could try the system-monitor application (under System->Administration).  Then sort on % CPU (click on the column heading) and see what the offending process is.

In the past when I've noticed lots of HDD crunching, it's been the "locatedb" application which is linked to the "locate" command line utility.  It's a nifty little tool that allows you to quickly search for any file on your filesystem.  The locatedb process is the one that indexes the filesystem and puts it into a database.  Usually this is set to run in the wee hours when it won't cause any problems, but if not, will cause temporary performance problems.

---

### Post by diablo75 on 2008-05-31
How much RAM is in the system?

---

### Post by melat0nin on 2008-06-15
> **diablo75 said:**
> How much RAM is in the system?

It's got 1gb.  I've reinstalled Hardy fresh since this happened (the old install was an upgrade from Gutsy) so it'll be interesting to see if it still happens.

---

### Post by Pjotr123 on 2008-06-15
Possibly this:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 1 )

---

