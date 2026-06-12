---
title: "non-contiguous data?"
date: 2007-08-01
forum: General Help
---

### Post by ninique on 2007-08-01
I have a dual boot of Windows and Kubuntu on my machine, with a separate home partition. For a couple of days, I keep getting this message every time I reboot saying my home partition "contains a file system with errors, check forced" and after it checks it, it tells me I have 5.4% of my files are non-contiguous. 

What does it mean? Do I have to defragment my drive or something? Is there a way to make it stop popping up everytime I reboot?

---

### Post by mathewb on 2007-08-01
After it checks it, it should fix the problems. Does it check it at every boot?

Non-contiguous = fragmented. However, there's no "safe" way to defrag a ext3 partition (i'm assuming your's is ext3). Also, the increase in speed is negligable in today's larger hard  drives.

---

### Post by ninique on 2007-08-04
Well it used to happen at every boot for about a week or so, but now it's back to normal. I guess it fixed itself or something.

---

### Post by benx009 on 2007-08-04
> **mathewb said:**
> After it checks it, it should fix the problems. Does it check it at every boot?

Non-contiguous = fragmented. However, there's no "safe" way to defrag a ext3 partition (i'm assuming your's is ext3). Also, the increase in speed is negligable in today's larger hard  drives.

there really is no need to defragment ext3 and reiser partitons -- and that's a good thing:wink:

---

