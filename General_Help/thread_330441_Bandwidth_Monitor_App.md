---
title: "Bandwidth Monitor App?"
date: 2007-01-03
forum: General Help
---

### Post by NeuroticKiss on 2007-01-03
Hi, sorry if this is the wrong forum for this, basically I'm looking for an app for Linux that monitors the network bandwidth and logs and displays the bandwidth monthly. As my internet bandwidth has a monthly limit and I do not want to go over it. On XP I had an  app for this but I can't seem to find one for Linux.

Any help would be great. Thanks!

---

### Post by opticyclic on 2007-04-21
Netmeter is a freeware Windows application that looks very similar to DU meter
[http://www.softpedia.com/get/Network-Tools/Bandwidth-Tools/NetMeter.shtml](http://www.softpedia.com/get/Network-Tools/Bandwidth-Tools/NetMeter.shtml)

It also works perfectly under Wine
[http://appdb.winehq.org/appview.php?iVersionId=5626](http://appdb.winehq.org/appview.php?iVersionId=5626)

---

### Post by Matt Yun on 2007-04-21
> **NeuroticKiss said:**
> Hi, sorry if this is the wrong forum for this, basically I'm looking for an app for Linux that monitors the network bandwidth and logs and displays the bandwidth monthly. As my internet bandwidth has a monthly limit and I do not want to go over it. On XP I had an  app for this but I can't seem to find one for Linux.

Any help would be great. Thanks!

This may be what you're looking for:  [Linux.com: Bandwidth monitoring with vnStat (2007 April 09).]("http://enterprise.linux.com/article.pl?sid=07/04/02/154220&from=rss")  

From the article: "f you want to monitor and manage your Internet bandwidth, perhaps to make sure your ISP is not overbilling you, try vnStat, an open source, Linux-based application that gives you a clear picture of your bandwidth usage. "

vnStat is a console application, but has a PHP browser-based frontend.  The article explains how to set all this up.

---

### Post by vdawg on 2007-08-26
> **Matt Yun said:**
> This may be what you're looking for:  [Linux.com: Bandwidth monitoring with vnStat (2007 April 09).]("http://enterprise.linux.com/article.pl?sid=07/04/02/154220&from=rss")  

From the article: "f you want to monitor and manage your Internet bandwidth, perhaps to make sure your ISP is not overbilling you, try vnStat, an open source, Linux-based application that gives you a clear picture of your bandwidth usage. "

vnStat is a console application, but has a PHP browser-based frontend.  The article explains how to set all this up.
have a look at bandwidthd also - [http://bandwidthd.sourceforge.net/](http://bandwidthd.sourceforge.net/)

runs in the background as a service and generates html pages which show network usage; works great :)

---

### Post by opticyclic on 2007-08-27
Knemo is pretty good too.

---

### Post by madelman on 2007-09-18
> **vdawg said:**
> have a look at bandwidthd also - [http://bandwidthd.sourceforge.net/](http://bandwidthd.sourceforge.net/)

runs in the background as a service and generates html pages which show network usage; works great :)

I could not make Banwidthd work in ubuntu 7.04. You can't even install it, do not use it:

[https://bugs.launchpad.net/ubuntu/+source/bandwidthd/+bug/111165](https://bugs.launchpad.net/ubuntu/+source/bandwidthd/+bug/111165)

---

### Post by eyelessfade on 2007-09-18
my favorite is iptraf.

---

### Post by evilc on 2007-09-18
If you are using Firefox try out the extension called Net Usage Item, it can track your daily usage and if you have a peak/off peak broadband it will give both. Best i've seen.

---

