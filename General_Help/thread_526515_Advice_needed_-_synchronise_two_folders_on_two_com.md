---
title: "Advice needed - synchronise two folders on two computers over the internet"
date: 2007-08-15
forum: General Help
---

### Post by mozjonathan on 2007-08-15
Hi,

My need is quite simple : user A has ~/shared on computer A and user B has ~/shared on computer B. Both are on the internet, not on a local LAN. I want their two folders to be synchronised : when A adds somethings in its ~/shared, it also makes it to B's ~/shared, and when B adds something it also makes it to A's ~/shared. That is, not a server-client synchronisation but a two-way synchronisation. I was initially looking for rsync and [this guy]("http://ubuntuforums.org/showthread.php?t=154624") seems to have the same needs, but I'm not aware of rsync's abilities.

By the way, is there a GUI for this kind of operations ?

Thanks a lot,

Jonathan

---

### Post by reacocard on 2007-08-15
> **mozjonathan said:**
> Hi,

My need is quite simple : user A has ~/shared on computer A and user B has ~/shared on computer B. Both are on the internet, not on a local LAN. I want their two folders to be synchronised : when A adds somethings in its ~/shared, it also makes it to B's ~/shared, and when B adds something it also makes it to A's ~/shared. That is, not a server-client synchronisation but a two-way synchronisation. I was initially looking for rsync and [this guy]("http://ubuntuforums.org/showthread.php?t=154624") seems to have the same needs, but I'm not aware of rsync's abilities.

By the way, is there a GUI for this kind of operations ?

Thanks a lot,

Jonathan

rsync will likely do what you want, just keep in mind its one-way so you'll have to run it on both ends to get a complete sync.

---

