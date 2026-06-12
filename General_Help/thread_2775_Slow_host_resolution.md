---
title: "Slow host resolution"
date: 2004-10-31
forum: General Help
---

### Post by freefood on 2004-10-31
So far, I'm really enjoying Ubuntu.  I even decided to dump my XP partition in favor of Ubuntu.  My only issue at this point, however, is slow web browsing.  It doesn't matter which browser I use - Mozilla, Firefox, and Epiphany all do the same thing - it takes forever for a page to START loading.  Once it starts, the connection's plenty fast.  But if I type in (for example) "www.google.com", it will sit there for 10 or more seconds before the page starts loading, displaying "Resolving host google.com..." in the status bar.  Once it appears, pages on the same server no longer lag like that.  I can then usually do some googling for 5 or 10 minutes before the "resolving host" thing happens again and I have to wait 10 seconds.  Also, this seems to happen if I leave that server for a while and come back.

Seems to me that it's taking a long time to establish a connection with the server; then once it's connected, the connection is as speedy as normal.  If that connection times out, however, it takes forever again to re-establish the connection.

Am I right?  And what can I do to fix this?

---

### Post by Joeb on 2004-10-31
Most likely, it's an IPv6 problem.  If you search the forums on that, you'll find how to remove it.  If your only problem is with firefox, though, an easier solution is to tell firefox not to use it.  To do so, enter about:config in the address bar of firefox, then scroll down until you see something called network.dns.disableipv6 and set it to true.

Once you close all instances of firefox and restart, it shouldn't try to use ipv6.

---

