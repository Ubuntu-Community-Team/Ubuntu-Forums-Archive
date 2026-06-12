---
title: "Ubuntu doesn't seem to like me very much :("
date: 2007-06-21
forum: General Help
---

### Post by Tekee on 2007-06-21
So once again, I somehow screwed up my .xorg by attempting to make Beryl work and I have to start all over setting up my right screen resolutions and such.

I got it to support my resolution, but now whenever I reboot the computer, I'm faced with a "frequency out of range" message. 

I've googled it and there's a quick fix to it, but whenever I try that, the screen resolution I want goes away.
How can I get both working?

---

### Post by Majorix on 2007-06-21
Get a new monitor? Your monitor must be old.

---

### Post by Tekee on 2007-06-21
> **Majorix said:**
> Get a new monitor? Your monitor must be old.

It's quite new, actually.

---

### Post by nick_h on 2007-06-21
I assume you did not make a backup of your config file before trying to install beryl.  In future this would be a good idea.

What was the fix that you tried?

---

### Post by Tekee on 2007-06-21
It's basically changing the horizontal/vertical rates to specific values. But apparently those conflict with my resolution as well. :(

---

### Post by nick_h on 2007-06-21
Try running the following:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

What resolution are you trying to get?  Be careful not to select a resolution that your monitor does not support.

---

