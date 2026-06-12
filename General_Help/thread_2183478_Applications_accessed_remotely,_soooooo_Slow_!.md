---
title: "Applications accessed remotely, soooooo Slow !"
date: 2013-10-25
forum: General Help
---

### Post by edy_sze on 2013-10-25
Noob here,

Yesterday I wanted to tighten up my security on my new Ubuntu 12.0.4 Server and so I went ahead and enabled UFW (firewall). After editing the IPtables and rules for the firewall I noticed that some of the applications became very slow.

For example I have a SOS Job Scheduler installed which I run on the server but provides a GUI for me to access remotely, that has slowed to a crawl. 
Also I have installed XFCE which I usually access remotely from my home PC (windows 7), that has also become very slow.

It's strange that instead of being blocked is has become very slow, might not even be the firewall.
Just wondering if anyone here have any ideas. Your help is very much appreciated.

[COLOR=#a52a2a][FONT=arial][SIZE=2]ufw status[/SIZE][/FONT][/COLOR]
[COLOR=#a52a2a][FONT=arial][SIZE=2]Status: active[/SIZE][/FONT][/COLOR]
[COLOR=#a52a2a][FONT=arial][SIZE=2]
[/SIZE][/FONT][/COLOR]
[COLOR=#a52a2a][FONT=arial][SIZE=2]To                         Action      From[/SIZE][/FONT][/COLOR]
[COLOR=#a52a2a][FONT=arial][SIZE=2]--                         ------      ----[/SIZE][/FONT][/COLOR]
[COLOR=#a52a2a][FONT=arial][SIZE=2]22                         ALLOW       Anywhere[/SIZE][/FONT][/COLOR]
[COLOR=#a52a2a][FONT=arial][SIZE=2]80                         ALLOW       Anywhere[/SIZE][/FONT][/COLOR]
[COLOR=#a52a2a][FONT=arial][SIZE=2]3306                       ALLOW       xxx.77.xxx.140[/SIZE][/FONT][/COLOR]
[COLOR=#a52a2a][FONT=arial][SIZE=2]4444                       ALLOW       xxx.77.[/SIZE][/FONT][/COLOR][COLOR=#A52A2A][FONT=arial]xxx[/FONT][/COLOR][COLOR=#a52a2a][FONT=arial][SIZE=2].140[/SIZE][/FONT][/COLOR]
[COLOR=#a52a2a][FONT=arial][SIZE=2]5900                       ALLOW       xxx.77.[/SIZE][/FONT][/COLOR][COLOR=#A52A2A][FONT=arial]xxx[/FONT][/COLOR][COLOR=#a52a2a][FONT=arial][SIZE=2].140[/SIZE][/FONT][/COLOR]
[COLOR=#a52a2a][FONT=arial][SIZE=2]5901                       ALLOW       xxx.77.[/SIZE][/FONT][/COLOR][COLOR=#A52A2A][FONT=arial]xxx[/FONT][/COLOR][COLOR=#a52a2a][FONT=arial][SIZE=2].140[/SIZE][/FONT][/COLOR]
[COLOR=#a52a2a][FONT=arial][SIZE=2]5902                       ALLOW       xxx.77.[/SIZE][/FONT][/COLOR][COLOR=#A52A2A][FONT=arial]xxx[/FONT][/COLOR][COLOR=#a52a2a][FONT=arial][SIZE=2].140[/SIZE][/FONT][/COLOR]
[COLOR=#a52a2a][FONT=arial][SIZE=2]5903                       ALLOW       xxx.77.[/SIZE][/FONT][/COLOR][COLOR=#A52A2A][FONT=arial]xxx[/FONT][/COLOR][COLOR=#a52a2a][FONT=arial][SIZE=2].140[/SIZE][/FONT][/COLOR]
[COLOR=#a52a2a][FONT=arial][SIZE=2]5904                       ALLOW       xxx.77.[/SIZE][/FONT][/COLOR][COLOR=#A52A2A][FONT=arial]xxx[/FONT][/COLOR][COLOR=#a52a2a][FONT=arial][SIZE=2].140[/SIZE][/FONT][/COLOR]
[COLOR=#a52a2a][FONT=arial][SIZE=2]5905                       ALLOW       xxx.77.[/SIZE][/FONT][/COLOR][COLOR=#A52A2A][FONT=arial]xxx[/FONT][/COLOR][COLOR=#a52a2a][FONT=arial][SIZE=2].140[/SIZE][/FONT][/COLOR]
[COLOR=#a52a2a][FONT=arial][SIZE=2]3389                       ALLOW       xxx.77.[/SIZE][/FONT][/COLOR][COLOR=#A52A2A][FONT=arial]xxx[/FONT][/COLOR][COLOR=#a52a2a][FONT=arial][SIZE=2].140[/SIZE][/FONT][/COLOR]
[COLOR=#a52a2a][FONT=arial][SIZE=2]4444                       ALLOW       127.0.0.1[/SIZE][/FONT][/COLOR]
[COLOR=#a52a2a][FONT=arial][SIZE=2]22                         ALLOW       Anywhere (v6)[/SIZE][/FONT][/COLOR]
[COLOR=#a52a2a][FONT=arial][SIZE=2]80                         ALLOW       Anywhere (v6)[/SIZE][/FONT][/COLOR]


FYI: Port 4444 is the default SOS Scheduler Port

Regards,
Edmond

---

