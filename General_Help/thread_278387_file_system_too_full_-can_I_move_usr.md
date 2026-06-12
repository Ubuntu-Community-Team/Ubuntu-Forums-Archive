---
title: "file system too full -can I move usr?"
date: 2006-10-16
forum: General Help
---

### Post by Hiroshima on 2006-10-16
I just setup my laptop like this:

partition 1: home 5gig
swap: 1gig
partition 3: 9gig
partition 4: root 2.8 gig

ran automatix, and found trouble real soon. The root drive is full already and prevented me from logging in.  I needed to delete files just to be able to log in.

I can't see anything that looks bigger than it should be, now that I compare folder sizes with my desktop.  Can I move the "usr" folder to the home partition... or do I need to start with a fresh install and resize everything?

I'll run synaptic to get rid of similar type programs (ie take off opera, and moxilla web browser and just keep swiftfox) to make some space.

ideas are welcome.

Hiroshima

---

### Post by Kateikyoushi on 2006-10-16
That partition might be too small, you could delete files from /var/cache/apt/archives it takes up 600MB for me.

---

### Post by Hiroshima on 2006-10-17
I've reinstalled with a reformat... Even though it took some time, I did that than having trouble for the rest of the time I use the computer.

Thanks for the help.

Hiroshima

PS in case you are wondering,

4G usr
4G /
1G swap
9G home

---

