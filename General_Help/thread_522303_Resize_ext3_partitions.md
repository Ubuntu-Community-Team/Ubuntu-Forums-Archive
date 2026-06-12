---
title: "Resize ext3 partitions"
date: 2007-08-10
forum: General Help
---

### Post by billgoldberg on 2007-08-10
I'm pretty new to ubuntu (been using it for a month now). I recently (last week) bought a new computer, it came with vista already installed. I installed ubuntu on it (dualboot with vista). I have a harddrive of 250 gb, 50 for vista and 200 for ubuntu (7.04). Now I need more room for windows vista (torrents don't seem to work well on ubuntu/gaming (cs:s)). I tried resizing the ext3 but it doesn't work. I downloaded gparted and it tells me to unmount the ext3 drive before resizing, but when i try to unmount it it gives me this "error":

The partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually.

I get this message if i right click the ext3 partition and click unmount.

Any help on this one guys?

(i don't use search functions on forums, i refuse)

---

### Post by billgoldberg on 2007-08-10
no one guys?

---

### Post by merlinus on 2007-08-10
Have you tried gparted live cd?  It is newer, and will allow re-sizing of partitions from either end.

Since it is a live cd, none of your partitions will be mounted when booting from it.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by kellemes on 2007-08-10
That's the issue indeed..
You can resize you partition fine as long as the partition is not mounted, there are a lot of lifecd/dvd's you can use to have GParted do the job.

---

### Post by billgoldberg on 2007-08-18
Thanks, it did the job

---

