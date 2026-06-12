---
title: "How to recover from disk full error?"
date: 2005-06-13
forum: General Help
---

### Post by dpod on 2005-06-13
Hi,
I was just downloading a bunch of fonts using synaptic when I got a disk full error. I checked the file manager, which claimed I still had 10.2 gig free. But... when I rebooted, I can't get in to Ubuntu (except of a terminal) because the disk is full.

Does anybody know what to do or where to find where Synaptic saves partially downloaded files so I can clean them out? I must say that is seems like a bit of a design flaw for an operating system to allow a disk partition to fill up to the point that it can't reboot!

I've looked at the only other relevant post I can seem to find:[http://ubuntuforums.org/showthread.php?t=38715&highlight=disk+full+recover](http://ubuntuforums.org/showthread.php?t=38715&highlight=disk+full+recover), but it really only partially answers the question: I'm hoping the live CD (burning right now) will recover the data, but what about everything else? ](*,)

---

### Post by Joeb on 2005-06-13
Try looking in the /var/cache/apt/archives for any downloaded packages.  You might also look in /tmp and see if anything in there can be deleted (most likely it can be).

---

