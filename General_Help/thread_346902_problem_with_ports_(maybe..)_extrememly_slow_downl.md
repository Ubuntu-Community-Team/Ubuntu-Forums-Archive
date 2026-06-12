---
title: "problem with ports (maybe..)? extrememly slow download speeds on p2p?"
date: 2007-01-26
forum: General Help
---

### Post by ashleywalton on 2007-01-26
When I try to use peer-to-peer software like IRC and BitTorrent, I suffer exruciatinly slow download speeds (im lucky if I get 1 kb/s), however, my download speeds from HTTP are just as fast as ever (upwards of 800kb/s).

Originally, I couldn't even get downloads to start, period, but after I installed firestarter, I was able to get these slow speeds at the least. I've tried unblocking all the ports specific to IRC (1025-7000), yet I noticed no difference in speed. My friend who also recently made the switch to Ubuntu with me is also noticing these problems with p2p programs (specifically, BitTorrent).

Could anyone give us a hand on how to solve this? We're really at the end of our rope, and have tried everything to get this working! I've tried posting to another forum, but I've recieved no help, the Ubuntu release I'm using is 6.06 LTS.

-Thanks to those kind people who can help us,
-Ashley & Vangs

---

### Post by an.echte.trilingue on 2007-01-26
Could be lots of things.

Could be an IPv6 problem.

[See Here.]("http://ubuntuforums.org/showthread.php?t=126221")

You could be that you are trying to upload more than you can chew; try limiting the number of upload slots you have set up and limiting your upload speed to 54kbps.

It could also be that your ISP throttles p2p, like mine does.

Take care,
-mat

---

### Post by ashleywalton on 2007-01-28
Holy crap... disabling ipv6 ACTUALLY worked (I seriously had doubts that it would). My gawd you're a genious man o_O;; Thanks a bunch, you rox so many s0x. I'm going to go permanently disable it now =D

---

