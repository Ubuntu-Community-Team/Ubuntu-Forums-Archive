---
title: "Wierd HTTP access problem"
date: 2007-12-14
forum: General Help
---

### Post by Patriko_H on 2007-12-14
A few days ago a website I've often accessed started hanging with a "waiting for ......." status line.  All other websites I visit are loading fine. I thought perhaps the site's server was having problems but found I can access the site fine when I boot into WinXP. In both cases I'm using Firefox, either on Ubuntu 7.10 or on WinXP, one works for this site, the other doesn't. I checked with the site admin and through several online sources to access/test the site indirectly and found no apparent problems.  I then tried accessing the site with Konqueror and wget, both show the same symptoms, DNS lookup is working, the connection is established, then no further data comes, finally a timeout.  I found the problem to exist on 2 other Ubuntu "Gutsy" machines. All are on my home network behind a Lynksys router connected to my DSL. I've run the updates on a couple of the machines recently, not sure if this is related but I'm getting quite suspicious. I've compared the http requests between the WinXP and Ubuntu OSes, and spoofed the User-Agent strings to  test if the server was responding differently based on platform, doesn't appear so. Have any recent updates to Gutsy involved the TCP/IP stack?  This one's become a real head-banger!
For the sake of testing, the site I'm having problems with is [www.goldmoney.com](www.goldmoney.com). I have not affiliation with this site other than an account I can no longer reach by my Ubuntu machines. ( And for security reasons I prefer NOT to use Windows for financial activities on the web. :(  )

Thx,
Patrick

---

