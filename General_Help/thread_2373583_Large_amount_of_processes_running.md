---
title: "Large amount of processes running"
date: 2017-10-07
forum: General Help
---

### Post by joshualalonde on 2017-10-07
Running gnome3 on an hp laptop with 4GB ram..

The only programs I have running are htop and firefox with 6 tabs open, yet there are over 20 processes running for firefox alone.  Is this normal? My ram is maxed out and its often relying on about 10% of my swap.  This cannot be normal.  

Any idea why firefox needs so many processes running and how I can get around this to free up some ram so I can maybe run more than 2 programs at the same time efficiently?

Thanks in advance.

---

### Post by dragonfly41 on 2017-10-07
I'm afraid that it is normal to see a process per browser tab .. and more. 
If you open System Tools > System Monitor > Processes tab and click on Dependencies
you can see the process tree.

If you are short of RAM you may benefit from extensions for tab management.

When I was short of RAM I switched from Firefox to Chromium Web Browser
and used extensions such as OneTab and Session Buddy to minimise tab RAM usage.

---

### Post by oldos2er on 2017-10-07
Which version of Ubuntu? Which version of firefox? Have you considered running a lighter desktop environment such as xfce or lxde?

---

### Post by SeijiSensei on 2017-10-07
> **joshualalonde said:**
> My ram is maxed out and its often relying on about 10% of my swap.  This cannot be normal.
Sure it is.  That's why you have swap space.  Right now I'm running Kubuntu 14.04 with Chrome (six tabs), Thunderbird, and about a half-dozen terminal sessions running as tabs in Konsole, some connected to remote machines.  (I have an Apache and a PostgreSQL server running on this box as well.) I have about 290 total processes according to top.  Over a dozen  of them were spawned by Chrome.  Firefox behaves pretty similarly.

Run "ps ax" and look at the processes with low PIDs.  Most all of those were spawned at boot, and many of them are swapped out.  My desktop process ("plasma-desktop") has PID 2965.  The dozens of processes below that value were all spawned during boot.

---

