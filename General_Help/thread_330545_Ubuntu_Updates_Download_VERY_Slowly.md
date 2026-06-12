---
title: "Ubuntu Updates Download VERY Slowly"
date: 2007-01-03
forum: General Help
---

### Post by carney1979 on 2007-01-03
Doesn't matter if I use Synaptic or the commandline, updates through Ubuntu repositories happen very slowly, at dial-up speeds.

I tried changing repositories and it didn't help. Doesn't matter what time I try to download from the repositories, it's always slow.

If I download anything else, it comes in very quickly.

Please see the attachments.

David

---

### Post by fragos on 2007-01-03
The download spead is a function of the slowest link.  In this case an Ubuntu repository being accessed by many users at the same time.  The sharing of the repositories bandwidth gives you a slower download.  System-> Administration-> Software Sources allows you to select where to download from.  Mine was defaulted to Main Server.  There is a US server that you can select.  This may give better performance since you are physicaly closer.  You will still be impacted by the number of users sharing access to that server.

---

### Post by chunk on 2007-01-03
> **fragos said:**
> The download spead is a function of the slowest link.  In this case an Ubuntu repository being accessed by many users at the same time.  The sharing of the repositories bandwidth gives you a slower download.  System-> Administration-> Software Sources allows you to select where to download from.  Mine was defaulted to Main Server.  There is a US server that you can select.  This may give better performance since you are physicaly closer.  You will still be impacted by the number of users sharing access to that server.

Someone should implement bittorrent for repo sharing.

---

### Post by fragos on 2007-01-03
BitTorrent is a natural for this kind of application, particularly when one end or the other has limitted bandwidth available.  By it's nature it will always be slower than a higher speed connection which seems to take better advanage of periods of higher available bandwith.

---

### Post by emarkay on 2007-01-03
I get from 35.0 kB/s down to almost 0 (500 B/s)at times with the typical DL being at about 20 kB/s, so you are not to far from me in terms of DL speed.  But yes it does have to di with the server load at teh DL site.

Where did you get that speed meter?  Interesting, but I'd prefer to find one that gives me an average of, say, the past 15 minutes average of DL and UL speeds...

---

### Post by carney1979 on 2007-01-05
The speed meter is new from [http://www.broadbandreports.com](http://www.broadbandreports.com)

I believe you have to have an account (free registration). Login, click on the tools button, the the speed test button. Then select the flash speed test.

David

---

### Post by MasterAslan on 2008-01-29
I just found a way to speed mine up MAJORLY.  I am on virgin media and noticed that my ISP had a mirror in the other list.  Made it WAY faster.  If you can find your ISP in the list definately use it.  Went from 30kbps to 1500kbs.

---

