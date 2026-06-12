---
title: "LVM question"
date: 2007-01-18
forum: General Help
---

### Post by kuja on 2007-01-18
I've been thinking for the last week or two about redoing my partition scheme for all three of my disks, and have started to make my move.

My plan is to create an LVM volume containing two disks - /dev/sda and /dev/sdc, and then go forth and create an enourmous (650GB ... okay, so I think it's enormous) partition on the LVM volume.

How would I go about doing this post-install. I know the alternate install disk has a tool for setting this up, but I'd like to do it now, without having to run the installer. How would I go about setting up the LVM? Also, seeing as I did a text install from the Edgy DVD, will I need any additional packages. Any help with this would be appreciated!

Hopefully this post doesn't go unanswered like any and (nearly) all of my previous questions posted here :s

---

### Post by birkensteen on 2007-01-19
> **kuja said:**
> How would I go about doing this post-install. [snip] How would I go about setting up the LVM?

Sorry I can't give you explicit steps, but I did exactly what you're talking about. I hunted around and found numerous guides, and while I got close I didn't really get it up and running perfectly until I used webmin to assist.

Actually, webmin was great for setting up my nfs share, too.

I'm planning on flattening my box this weekend and rebuilding it so I'll be happy to post something in a few days, but, if you're in a hurry, I'd say install webmin and use that in conjunction with a good LVM guide like [**this one**]("http://http://www.howtoforge.com/linux_lvm") or [**this in-depth one**]("http://www.tldp.org/HOWTO/LVM-HOWTO/").

---

### Post by kuja on 2007-01-22
Thank you sooooooo much for your reply birkensteen! Deeply appreciated.

I'd already been over the first link, and though informative, it really didn't tell me much about how to use it ... plus it seemed like it was feeling its age, as many tldp docs do (great site ... old docs). The second link you gave me though ... wow, right on the money. I had it up and going in minutes!

---

