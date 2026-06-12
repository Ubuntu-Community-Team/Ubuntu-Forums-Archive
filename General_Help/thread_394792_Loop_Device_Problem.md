---
title: "Loop Device Problem"
date: 2007-03-27
forum: General Help
---

### Post by ScottMorris on 2007-03-27
Hi, I'm trying to mount ISO images so I can use them on my server but I have more than eight to mount.  How can I increase the default amount from 8 to something bigger like 24?  I'm not sur if this is the place to post but it didn't fit into any other categories.

---

### Post by schilcha on 2007-03-27
That's an interesting problem... I've googled a littlebit myself and found a possible solution [here]("http://groups.google.com/group/nl.comp.os.linux.overig/browse_thread/thread/233b4c421896cbca/29e3073b12bad8a0?lnk=st&q=linux+8+mount+loop+devices+2.6&rnum=16&hl=en#29e3073b12bad8a0") (dont be afraid -- it's a dutch list, but the solution is in english)

In short, there's the max_loop parameter, that needs to be handed over to the kernel module or the kernel itself (whatever is handling the loopback block devices). Also make sure, you have enough device-files.

Good Luck!

---

### Post by ScottMorris on 2007-03-27
Thanks for the link - max_loop worked.  A co-worker of mine found that it has to be added to /etc/modprobe.conf as ```
...lines omitted...

options loop max_loop=64
```Then, at boot it adds the new devices once the 8 default devices are depleted.

'loop' I believe is the kernel module and the 'max_loop=*num*' is the maximum amount of devices to create - upto 256.

---

