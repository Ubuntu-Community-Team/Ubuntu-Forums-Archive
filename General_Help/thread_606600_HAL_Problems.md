---
title: "HAL Problems"
date: 2007-11-08
forum: General Help
---

### Post by niethslim on 2007-11-08
Every time I start the computer I get an err message that says: "internal error -- failed to initialize HAL". The problem started when I upgraded from feisty fawn to gusty gibbon and it prevents me from using the CD/DVD drives and some of my hard drive partitions.
Any idea how to fix this?

---

### Post by Boatswain on 2007-11-12
I've got the same problem--can anyone either give advice or post a link to somewhere that does?  Thanks.

EDIT:

Searching the forums a bit brought up a lot of posts from a lot of people having a lot of problems with HAL after upgrading to Gutsy.  Apparently there are several different sorts of things that can have gone wrong. Here are two of the more promising threads:

[http://ubuntuforums.org/showthread.php?t=538050&highlight=hal+internal+error&page=2](http://ubuntuforums.org/showthread.php?t=538050&highlight=hal+internal+error&page=2)
[http://ubuntuforums.org/showthread.php?t=583940](http://ubuntuforums.org/showthread.php?t=583940)

It was the first of those links that got me to a solution--basically, the advice in that thread is to go into Synaptic, search for HAL, and switch back to older versions of hal, hal-device-manager, libhal-storage1, and libhal1. Well, I tried that and got an error message saying that I needed to manually run dpkg--I don't remember the error message off the top of my head and I can't access the partition that I copied and pasted it to at the moment. Suffice to say, I did what the error message said, a bunch of stuff was updated, and I no longer get HAL errors and can access the network.

Hope that helps.

---

