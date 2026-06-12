---
title: "how to decrease the CPU load in my laptop?"
date: 2017-02-26
forum: General Help
---

### Post by boldas2 on 2017-02-26
Hi everyone!

I have a laptop which is quite old (2011) but still working very fine for me (once it fall down and hit the floor but...it's still on track!!) ... I have Ubuntu 16.04 installed on it and I enjoy it very much. The only issue is that sometimes the "response" is not so fast. For example, opening a new page on the browser, or i.e. typing with the keyboard in this forum... I do experience a certain "delay" which I would relate to the "CPU load" (in fact, when I open the System Monitor and check the amount of CPU currently used by the 4 core of Intel i3 processor, I see it's always between 50% and 100%, especially when I use a browser program such as Mozilla Firefox). The RAM, instead, I think it's enough (8GB, often below 50%).

So, my question is: is there a way "decrease" this CPU load (maybe installing a "lighter" distro?) or any other suggestion instead of buying a new laptop?

Thanks in advance,

Best,

boldas

---

### Post by Impavidus on 2017-02-26
Use **top** to find out which programs cause that CPU load, then decide whether you really need those programs.

I've got a laptop of the same age and the same memory (but with an i5 processor) that's very happy running Xubuntu. So a lighter flavour may work.

---

### Post by Autodave on 2017-02-26
Xubuntu would be a better alternative to run: much less memory hungry.

---

### Post by dragonfly41 on 2017-02-26
As another user trying to squeeze performance out of an old laptop (predating 2011) I offer these tips.


[LIST]
[*]Don't keep multiple applications running in background since they eat up resources.  Try to use only those you need at any time. So you tradeoff convenience of have apps instantly at hand vs.  performance. For example don't keep Thunderbird open after a mail admin session.
[*]When using browsers look for tab manager add-ons.  Currently I use Chromium Web Browser and use add-ons such as OneTab and SessionBuddy to keep tab count under control.  Each tab in use eats up a slug of memory (you can see this in System Monitor < Processes).  Previously I used Firefox and I can remember using TGH add-on (Tab Group Handler).  Also installed session manager so that I could switch to a lean profile.
[*]One obvious way of improving performance is to add memory, and memory cards can be quite cheap to purchase.  For old computers there is the local recycling shop to explore.
[*]For monitoring the usage of resources there is System Monitor.  But recently I found GKrellM (plus addons) found in Ubuntu repo.
[*]Lighter weight distro Xubuntu has been suggested earlier.
[/LIST]

---

