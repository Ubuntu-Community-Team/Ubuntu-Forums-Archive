---
title: "Bittorrent Odd Behaviour"
date: 2006-12-29
forum: General Help
---

### Post by mcwtlg on 2006-12-29
For any of you who use Bittorrent:

I have noticed that the app will start downloading slow, then build up speed after a few minutes (I understand this as normal), but then drop off considerably.  I will let it run for several hours and still only get 1-2 kb downloads.  If I kill Bittorrent and restart it, the speeds jump back up to fast and continue the downloads.

Anyone else ever experience this?  Any better client that will run on a low end box (500 mhz, 384 megs of RAM)?

---

### Post by PurplePenguin on 2006-12-29
What speeds does it peak at (ballpark)?  If it won't peak very high, you might have a port problem (if you do get peaks of 100kbps or higher, I'd say you can easily rule out blocked ports).

How many torrents does this happen on?  If it's just one or two, try more. 

Are the torrents well-seeded?

Since it seems that you do get high speeds at the beginning, but they cut down, it also might be possible that your ISP throttles bittorrent downloads.  Try using a different port (something higher than 20000) and maybe get a client that uses encryption such as Azureus.  This should help to fool your ISP. :)

---

### Post by mcwtlg on 2006-12-29
> **PurplePenguin said:**
> What speeds does it peak at (ballpark)?  If it won't peak very high, you might have a port problem (if you do get peaks of 100kbps or higher, I'd say you can easily rule out blocked ports).

How many torrents does this happen on?  If it's just one or two, try more. 

Are the torrents well-seeded?

Since it seems that you do get high speeds at the beginning, but they cut down, it also might be possible that your ISP throttles bittorrent downloads.  Try using a different port (something higher than 20000) and maybe get a client that uses encryption such as Azureus.  This should help to fool your ISP. :)


I have gotten as little as 0 KB/sec and as high as 200 or so, all using the same ports.  I do have a router, but it is set for port forwarding.  This behaviour seems to have started with bittorrent 4.26 running on Edgy.  When I Dapper was installed (and another, older version of BT), it did not have this behaviour.  

This seems to happen on most torrents...and I only look at well seeded torrents (30+ seeds).  I guess it could be my ISP...we recently were converted over to Time-Warner when Concast traded markets in North Central Texas, USA.

I have tried using Azureus, but it seems to be more of a resource hog than Bittorrent is and Bittornado must use separate instances of it self for multiple downloads.

---

### Post by mcwtlg on 2006-12-31
I tried Azureus but it seems to really hog my resources... :(

---

