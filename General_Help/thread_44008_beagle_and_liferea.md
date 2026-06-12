---
title: "beagle and liferea"
date: 2005-06-24
forum: General Help
---

### Post by burlap on 2005-06-24
Beagle indexing problems again...

It seems that beagle 0.0.11.1 is indexing everything I want, but I can't search Liferea (0.9.1) news.

This is what I get when beagle is launched (relevant part):
```
INFO: Scanning Liferea feeds...
INFO: Starting Evolution mail backend
WARN: Exception caught while executing Beagle.Daemon.LifereaQueryable.LifereaQueryable:Void StartWorker()
WARN: System.NullReferenceException: Object reference not set to an instance of
an object
in <0x002f1> Beagle.Daemon.LifereaQueryable.LifereaQueryable:IndexFeed (System.String filename, Priority priority)
in <0x0029c> Beagle.Daemon.LifereaQueryable.LifereaQueryable:StartWorker ()
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
in <0x0001f> Beagle.Util.ExceptionHandlingThread:ThreadStarted ()

```
Later I get all these messages (this is one of many):
```
DEBUG: Finished task feed:http://newsrss.bbc.co.uk/rss/newsonline_uk_edition/business/economy/rss.xml;item=http://news.bbc.co.uk/go/rss/-/1/hi/business/4114740.stm in ,00s
```
Counter in beagle-index-info shows more and more indexed items for Lifereas (as of this moment it is 1933)

When I try to search for something, only a few feeds are searched (bbc from the above example is **not** one of them). What about the rest? Is it beagle or liferea?

(BTW: I have tried blam: it works with the feeds that don't work in liferea/beagle. However, I don't like blam...)

---

