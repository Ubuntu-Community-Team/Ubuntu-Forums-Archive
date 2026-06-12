---
title: "No 'make' Xubuntu, normal?"
date: 2006-08-27
forum: General Help
---

### Post by Phyzzip on 2006-08-27
*Disclaimer: I've already solved this problem on my own. This isn't a request for help. I am curious though.*

Ok, my little sister had some lovely Windows Genuine Advantage warnings on her computer so, on my dad's suggestions we decided to just install Xubuntu over it.  Didn't think it would be a big deal, I've been running Breazy Badger for several months on an old computer. Gotten fairly comfortable with CLI.

My dad downloaded the latest CD Image from the official Ubuntu site during the night. Started the install and it worked fine, except the wireless NIC wasn't detected. Not a big surprise as I've been researching wireless compatibility and Linux. Went to ndiswrapper, downloaded the Tarball and appropriate driver, transfered it over with a USB keydrive. And was shocked when I tried to install it and got "bash: make: command not found". Biggest fricking shock ever. I eventually  ended up unplugging another machine and running its network cable to the machine in question. And then doing google searches until I found what package to install, the winning string was "where's make" on this forum.

So is Xubuntu supposed to by default not have make included. Was my image corrupted somehow? If it is not in there by default shouldn't that be noted in the Xubuntu guide in really big letters? I mean in the initial tweaking on my old machine I had to compile from source a couple times. Anyway, just wondering, it's all lovely now.

---

### Post by aysiu on 2006-08-27
That's the way it is. More details [here](http://www.ubuntuforums.org/showthread.php?t=192840).

---

### Post by Phyzzip on 2006-08-27
Ah, I'll read right now. Funny, it was your post that had the apt-get I needed. And I just read ["Anatomy of a well-intentioned Linux Troll"]("http://ubuntuforums.org/showthread.php?t=58017").

---

### Post by aysiu on 2006-08-27
> **Phyzzip said:**
> Ah, I'll read right now. Funny, it was your post that had the apt-get I needed. And I just read ["Anatomy of a well-intentioned Linux Troll"]("http://ubuntuforums.org/showthread.php?t=58017").
Yes, people tell me I'm everywhere.

---

### Post by Phyzzip on 2006-08-28
Things are much clearer now. I guess at some point very soon after installing the distro I installed it (perhaps inadvertently) on my Breazy Badger box and forgot, which left me confused when it wasn't there on the fresh box.

---

