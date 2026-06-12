---
title: "Ubuntu Minimal logout hangs"
date: 2014-03-05
forum: General Help
---

### Post by Tristan_Williams on 2014-03-05
I am running Ubuntu Minimal 13.10 with Xfce4

Here lately, when I logout, it takes over 5 minutes to actually logout and make it to the lightdm login screen.

I think this may be firefox related (not completely sure)
When I close out of firefox, the firefox "process" keeps on running, and I have to issue 'killall firefox'

Any ideas as to what may be causing this, or how I can fix it?

---

### Post by Portaro on 2014-03-05
I think that you have a extreme processe requesition on the machine, but you use Xfce this DE with Lubuntu also have a light RAM required and processes have more effective work by processor.

HUm what are the specs of your PC?

can you give to us the result of command :

free -m

and the result of :

top

Try to use Midori browser to see if firefox have a colapsed cookies, if the pc run well with Midori I suggest to you to use Bleachbit **to clean firefox cache and cookies**.

---

### Post by Tristan_Williams on 2014-03-05
Dell Vostro 220
Intel Core 2 Duo @ 2.93 Ghz
4GB DDR2 RAM

Ubuntu Minimal 13.10
Xfce4, Firefox, Thunderbird, and most of the other "resource-intensive" packages on my system were built from source (using apt-build)

The main processes that are running are:
Firefox
Thunderbird
Preload
Guake

I have a "Clear Cache" button on Firefox, which autocleans the cache when it reaches 40% of the total alloted space for cache (so when it reaches 4 MB)

The output of 'free -m' is:
```

             total       used       free     shared    buffers     cached
Mem:          3999       2427       1572          0        218       1686
-/+ buffers/cache:        522       3477
Swap:         4059          0       4059

```

---

### Post by mmcl26554 on 2014-06-20
Tristan, Did you ever find an answer to your log out hang?   I have the same problem with 14.04.  After I installed, it was working &  log out was quick but now it takes about 3 minutes to get to the login screen.    I am by no means a Ubuntu expert but learning so I have no idea what has caused this new behavior.   I cannot seem to get any answers from the forums.
Michael

---

