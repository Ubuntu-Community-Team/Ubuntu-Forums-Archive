---
title: "Help calculating upload time in hours?"
date: 2006-12-02
forum: General Help
---

### Post by xyz on 2006-12-02
Hi,
A few weeks ago, I posted this thread [Free Mozart download til next Friday!]("http://www.ubuntuforums.org/showthread.php?t=292644&highlight=mozart")
The RSR Radio station had about 3h worth of Mozart downloads up there on their server for a limited amount of time: 1 week.

Several people have asked me if I could upload these files for them which I'll be glad to do here:
[Dropload]("http://www.dropload.com/")
That way they'll be available to download for yet another week!

*I need help figuring out how many hours it'll take me to upload a, say, 70 MB file up on Dropload based on the results of [ this Speedtest?]("http://www.speakeasy.net/speedtest/")*
> Last Result:
Download Speed: 3056 kbps (382 KB/sec transfer rate)
Upload Speed: 298 kbps (37.3 KB/sec transfer rate)
Numbers are far from being my best quality...so any help would be appriciated.Thx.

---

### Post by StormNet on 2006-12-02
> Last Result:
Download Speed: 3056 kbps (382 KB/sec transfer rate)
Upload Speed: 298 kbps (37.3 KB/sec transfer rate)

rough stimates

```
70 MB = 70MB x 1024kb/MB = 71680kb             so that we have a common base
71680 kb / 37.3 kb/sec = 1921.7 seconds          now we can just divide the size by the UL rate
1921.7 seconds / (60s/min) / (60 min/hr)          converting the time into hours:minutes:seconds format
.53 hrs or about 00:32:02
```

I used to like doing these in school. It is kind of like the "If a train leaves New York going at blah blah blah speed, when will it get to blah blah" Hope that helps.

Or you can use an [Online Calculator]("http://www.t1shopper.com/tools/calculate/downloadcalculator.shtml") just not as fun.

---

### Post by Kurt` on 2006-12-02
[http://www.google.com/search?hl=en&lr=&safe=off&q=70+MB+%2F+298+kbps&btnG=Search](http://www.google.com/search?hl=en&lr=&safe=off&q=70+MB+%2F+298+kbps&btnG=Search)

Google Calculator scares me

---

### Post by Endolith on 2008-05-03
> **Kurt` said:**
> [http://www.google.com/search?hl=en&lr=&safe=off&q=70+MB+%2F+298+kbps&btnG=Search](http://www.google.com/search?hl=en&lr=&safe=off&q=70+MB+%2F+298+kbps&btnG=Search)

Google Calculator scares me

Google Calculator is actually wrong for calculations like this, since they use the wrong definition of "kbps".  This will give you the correct answer:

[http://www.google.com/search?q=70+MB+%2F+298000+bps](http://www.google.com/search?q=70+MB+%2F+298000+bps)

In this case, the difference is tiny, and it's just a ballpark calculation anyway, so it doesn't matter.  But in other cases the difference is bigger and the exact value does matter, so be careful when you trust their results.

---

