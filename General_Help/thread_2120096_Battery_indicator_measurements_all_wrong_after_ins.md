---
title: "Battery indicator measurements all wrong after installing and removing zram"
date: 2013-02-25
forum: General Help
---

### Post by blackbird34 on 2013-02-25
My battery indicator now gives me the wrong amounts of time left over before the battery is empty. This is the case in both the Unity and Cinnamon DEs (I use both alternately). The upshot of this is that my computer suddenly runs out of power and turns off without warning and without shutting down properly, despite the indicator claiming I have 20% battery or so left.

I hope this isn't going to brick the system at some point (so far, so good - Firefox, Thunderbird and LibreOffice all save their sessions nicely). 

It all started after I had a look at ZRam [[link]]("http://mygeekopinions.blogspot.fr/2011/10/boost-system-performance-ram.html") , installed it, tried it, and then uninstalled it as I didn't really need it, and I really have enough RAM anyway. ZRam compresses stuff in RAM so that you have "more" RAM, but the actual compressing and uncompressing stuff for use consumes CPU cycles and thus consumes power. 

It is not only the indicator's fault though: when I look in the "Power Statistics" utility, sometimes it isn't actually measuring the amount of power left in my battery, or still thinks the computer is plugged in, when it's not...

Can anyone help me with this?

---

### Post by blackbird34 on 2013-02-27
bump :/

---

### Post by blackbird34 on 2013-03-03
And bump again...
I've checked, it also happens in Windows 7. Does a system corrupt if it's suddenly shut off like that a lot?

---

