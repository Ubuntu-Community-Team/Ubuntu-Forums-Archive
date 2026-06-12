---
title: "Real Player disrupts system network connectivity"
date: 2005-08-28
forum: General Help
---

### Post by dodongo on 2005-08-28
This is the most bizarre thing ever. 

When RealPlayer tries to start streaming a clip, occasionally, and without any seeming sort of pattern, the entire system's network connectivity goes down.  A yellow warning ! icon appears in the wireless monitor, and resetting ath0 with /etc/init.d/netwokring restart does nothing to resolve the issue.

The only thing that helps is restarting my network router, then restarting the networking components.

As an example, the [Car Talk website](http://www.cartalk.com/Radio/Show/online.html) has a streaming page which is a playlist of 10 RA clips.  I can't listen past the second segment of the show; loading one of the first three clips always causes the connection to crap out.

This phenomenon also occurs with other streaming media RealPlayer is used for, so I'm quite certain it's not a server-side issue, but rather something locally.

I've also tried the currently-available package at real.com, to see if that changes the symptoms.  It does not.

Anyone have any thoughts?

---

