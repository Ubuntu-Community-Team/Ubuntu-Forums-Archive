---
title: "Dropbox eating all my memory."
date: 2013-10-17
forum: General Help
---

### Post by NertSkull on 2013-10-17
For the past 3 or 4 days, I leave work at night and I come back in the morning and dropbox is eating ALL my memory.  I looked through my package manager history and I haven't updated anything recently.  But even after I killall dropbox my memory usage drops back down to normal, but I still end up restarting my computer because it feels sluggish.

I attached an image showing this.  

How can I fix this?

---

### Post by RobertLos on 2014-08-22
sudo bash -c 'sync; echo 3 > /proc/sys/vm/drop_caches'

cleans the memory. You can put it in a cron process to do it every 15 minutes or so but usually once is enough

---

