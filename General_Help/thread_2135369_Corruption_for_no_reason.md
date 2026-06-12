---
title: "Corruption for no reason?"
date: 2013-04-14
forum: General Help
---

### Post by Theredbaron1834 on 2013-04-14
I have 1 computer with an HDMI port. It is my main gaming computer. I keep it in my room, but a friend wanted to watch something on it, because it is my only device that can output 1080p res, so I moved it out to my big TV in the living room. Watched it, played around with it a bit on the big screen (facebook/reddit/ect). Then I shut it down. Once it was fully off, I unpluged everything and moved it back to my room. 

Upon boot up it popped up errors saying / (ext4), /boot (ext2), and /home (ext4) had error's and needed fixing. Of course I did run the checks, and everything boot up fine after about 3 min.

But why would there be error's? I was under the assumption that error's accure, most commonly anyways (and the only thing that I was doing at the time) when a write doesn't get completed before a power failure. Why would such a thing happen when I did a full shutdown?

---

### Post by TheFu on 2013-04-14
Could be all sorts of things - loose cable, bad cable, loose RAM, failing HDD, failing HDD controller, cracked motherboard - anything.  What do the log files show?
[http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)

---

### Post by tubbygweilo on 2013-04-14
Theredbaron1834,
Do you have a liveCD holding partedmagic [http://partedmagic.com/lib/exe/detail.php?id=screenshots&media=desktop.png](http://partedmagic.com/lib/exe/detail.php?id=screenshots&media=desktop.png) close to hand? If you then a boot with this tool and a run of the System Profile & Bench Mark application from the desktop will both list you hardware & give you an idea as to it's health. If all is as expected then a loose connection as previously suggested may well be your problem.

Physical access trumps all others.

---

### Post by Theredbaron1834 on 2013-04-14
Was a loose connection. :)

I checked it out, and it seems that the movement has caused it to pop out a bit.

Thanks for the help.

---

