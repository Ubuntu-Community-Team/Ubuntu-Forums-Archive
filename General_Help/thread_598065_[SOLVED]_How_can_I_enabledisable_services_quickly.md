---
title: "[SOLVED] How can I enable/disable services quickly?"
date: 2007-10-31
forum: General Help
---

### Post by sci-fi guy on 2007-10-31
When messing around with Nmap, I found several open ports related to cupsys and samba. I do not use either very much, but I *do* use them. How can I make them activate *only* when I need them or at least make turning them on and off very simple (as in, a launcher on my desktop)?

---

### Post by troyer81 on 2007-10-31
I will certainly defer to other experts if they have better ideas, but I would think you could create a script as a "launcher" that runs the following execution:

```
sudo sh /etc/init.d/cupsys stop
sudo sh /etc/init.d/samba stop
```Or change the "stop" to "start" when you want the services started.  That won't necessarily "plug the holes", but it will at least stop those services from running.

Hopefully that helps a little bit....

---

