---
title: "Weird double-mount problem"
date: 2007-05-25
forum: General Help
---

### Post by scradock on 2007-05-25
I'm running Feisty - very nice, esp. with XGL and Beryl.

But I want to keep Edgy around, and I have this weird problem. Some time ago when I was first installing edgy it decided to mount its partition (let's call it /dev/hda4) both as / and as /dev/.static/dev . It didn't seem to matter too much; everything just works.

Now I have copied Edgy into a larger partition, and <3.0GB of files are apparently occupying 5.8GB of an 8GB partition. Could this be related to the double mount?

How can I "undo" the double mount? I can't see extra files anywhere, either within Edgy or from Feisty. The report from Gparted says that the space occupied is 5.8GB; the sum of all known files is 2.3GB.

fstab has only one entry for /dev/hda4     /   ext3 defaults 0 0
mtab only shows it once

the directory /dev/.static/dev exists, but has no hda entries.....

I'm baffled - any ideas?

---

