---
title: "memory cache is huge"
date: 2007-02-15
forum: General Help
---

### Post by christoforever on 2007-02-15
hey guys I didnt know where to post this, but this seemed as good a place as any.
Anyway after running some apps and looking through the internet and just doing all
sorts of things i noticed my memory cache was about 1.2 gigs. HOLY SUGAR!!! (for lack of a better term) But my actually used memory was a little under 240. I was just wondering if there was a way to clear the cache, or will ubuntu make use of it as it needs it?

Sincerely,
Chris Dancy

---

### Post by lloyd_b on 2007-02-16
> hey guys I didnt know where to post this, but this seemed as good a place as any.
Anyway after running some apps and looking through the internet and just doing all
sorts of things i noticed my memory cache was about 1.2 gigs. HOLY SUGAR!!! (for lack of a better term) But my actually used memory was a little under 240. I was just wondering if there was a way to clear the cache, or will ubuntu make use of it as it needs it?

That's perfectly normal.  Basically, if there's ANY free memory in the system, Linux will try to use it for cache.  When an application requests more memory than is available, the system will release a suitably sized chunk of that cache, and give the memory to the application instead.  

Lloyd B.

---

### Post by n00bish on 2007-02-16
It is in your best interest for your ram to be used as cache - if your ram isn't being used for anything, it's kind of useless, isn't it?  It's much faster to cache something in ram than it is to get it from disk via swap or reading from the file system.

---

