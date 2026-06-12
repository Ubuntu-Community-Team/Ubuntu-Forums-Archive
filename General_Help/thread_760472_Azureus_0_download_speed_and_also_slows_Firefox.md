---
title: "Azureus 0 download speed and also slows Firefox"
date: 2008-04-20
forum: General Help
---

### Post by plo on 2008-04-20
I have a strange problem probably related to Azureus. Been running for some time under Gutsy without problems but a couple of weeks back something broke.

When I start Azureus download speed is at 0 or mayble a very slight trickle. If I start Firefox browsing is also very, very slow (went for a walk and then the webpage had loaded). If I quit Azureus , reboot and just start Firefox speed is normal. Other (windows) computer on same router work fine all the time. NAT is OK.

I also tried installing the Vuze version of Azureus with same result.

Any ideas?

Thanks
/Palle

---

### Post by leezer3 on 2008-04-20
Dunno precisely when this started, but I think something broke in the current set of updates (Last 3-4 days, although I don't always update fast).
Broken in both Gutsy & Hardy, and really annoying me ATM.

Nothing else handles the sheer number of torrents (90, various seed rules, plus downloading) and has the amount of options I need here :(

*Edit:* Definitely Java related. Changing the JRE from 1.5 to 1.6, Azureus no longer kills the connection, but still isn't downloading or uploading- Should be bouncing off the 50k upload limiter as a minimum, not even hitting 1k :(
Will post if I actually get things under control.

Cheers

-Leezer-

---

### Post by Ev1L on 2008-06-07
any improvement?

at first glance I would suspect it's an ISP limitation on number of connections recently set.
I had the same behavior with my ISP in Italy on my notebook.
With Vista+Azureus I downloaded at few kb/sec and unusable browser, while back to Germany I reached full bandwidth (over 1MB/sec).

I had to format, though, and I decided to move to Ubuntu, but now I can't even reach a total of 100k/sec with either Transmission or Azureus, and the rest of downloads/browsers slow down as well.

It's quite strange if the ISP changed policy on torrent exactly now, so I suspect it's something linux related.

Any suggestion?

---

