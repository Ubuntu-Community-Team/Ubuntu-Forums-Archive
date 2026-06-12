---
title: "Resizing and merging partitions"
date: 2007-02-21
forum: General Help
---

### Post by shironeko on 2007-02-21
I am an ex-windows user, and when I first installed ubuntu it was only on a 17Gb partition since I thought I would continue working with windows.

Now, 3 month's after I don't touch windows anymore, don't need it and don't use it. And that's the moment when 17GB of HD start to suck.

I tried to use Gparted to resize the windows partition and merge it with the Linux partition. But I can't, here's what I get.

First all HDa's had a lock on it, but then I noticed that I had to unmount the MS partition, and that's what It looks like now:

[img]http://img503.imageshack.us/img503/131/screenshot1sc8.png[/img]

What do I have to do to resize the windows partition and merge the freed space with my ubuntu partition?

---

### Post by chggr on 2007-02-21
> **shironeko said:**
> 
What do I have to do to resize the windows partition and merge the freed space with my ubuntu partition?

First delete the /dev/hda1 partition and then right click on /dev/hda2 and choose resize.

---

### Post by saz on 2007-02-22
but can he do it when the partition is mounted? wont there be the lock?

i wanted to reduce the size of my ubuntu partition, so i could try another distro... but i can't cuz ubuntu's partition is mounted... i tried through partition magic on windows, but only got an ERROR... =S

---

