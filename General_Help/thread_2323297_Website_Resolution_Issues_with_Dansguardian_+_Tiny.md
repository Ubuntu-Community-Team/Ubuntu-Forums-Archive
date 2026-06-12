---
title: "Website Resolution Issues with Dansguardian + Tinyproxy"
date: 2016-05-04
forum: General Help
---

### Post by Michael_Griffith on 2016-05-04
Hello all!

Recently for my workplace I've setup a virtual Ubuntu Server (16.04) on our Hyper-V server. Installation went smoothly and I've been accessing the server just fine using Putty from my desktop. The goal with this server is to use it as an internal proxy to utilize Dansguardian to filter out certain websites. Currently I have Dansguardian installed with Tinyproxy and I have been testing using Chrome from my desktop routing it to the Dansguardian listening port 8080. Everything appeared to work and I was prepared to roll it out across my network when I realized that certain websites don't load when I'm connected to the proxy (they load for a while then leave me with a blank screen). And a specific internal website does not load either when I'm connected to the proxy. I'm not sure what's causing this to only happen with a few random websites and a specific internal website. Randomly testing websites I can't find a pattern. My computer is connected to a DNS on a windows servers so I'm not sure if that has any bearing on the issue. Testing the Ubuntu server I can connect just fine to these websites (tested using elinks).

Any advice would be appreciated,

Thank you much
Michael

---

### Post by SeijiSensei on 2016-05-04
Try right-clicking on a problematic page in your browser and choose "View Source." Perhaps you can see whether there are blocked objects.  Usually the links on the source page are clickable so you can see whether they work or not.  Also do you have a log that shows the disposition of each object requested from the Internet?  I've used Squid as a web proxy, and it provides a complete list of every request and its disposition.  My guess is that the problematic pages request information from other sites that are blocked by DansGuardian, but without logs it may be tough to diagnose.

---

### Post by Michael_Griffith on 2016-05-05
The page is definitely returning nothing as the source is completely empty. I'll see if I can review some logs and see what's going on I'll post them if I find anything interesting there.

---

