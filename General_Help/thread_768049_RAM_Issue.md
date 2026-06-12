---
title: "RAM Issue"
date: 2008-04-26
forum: General Help
---

### Post by puppyfarts on 2008-04-26
When I go to my system monitor and add up all the memory being used by everything open, it is always about 50% of the total I see when I run conky to check.  Is this an error with conky, or is there more going on behind the scenes that doesn't show up in system monitor?

I'd like to know, since unless Firefox goes crazy, I am always under 128, but it always shows around 260.

---

### Post by ryanhaigh on 2008-04-27
The system monitor doesn't show the cache that is being used. You can use the command free to check memory usage including cache. My guess would be that conky is showing cache also.

This may be interesting to you:
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

