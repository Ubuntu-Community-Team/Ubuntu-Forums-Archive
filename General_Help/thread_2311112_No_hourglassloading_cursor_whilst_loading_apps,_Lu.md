---
title: "No hourglass/loading cursor whilst loading apps, Lubuntu 15.10"
date: 2016-01-24
forum: General Help
---

### Post by midgleyi on 2016-01-24
Whilst waiting for Chromium to take ages to load (see [http://ubuntuforums.org/showthread.php?t=2311098](http://ubuntuforums.org/showthread.php?t=2311098) ) I noticed that there is no indication that the machine is actually doing anything, nor on other application loads.  I have been into preferences and can see a couple of standard cursor themes DMZ White and Black which include a round "busy" type cursor of the type I would be expecting. I can change to the black version of the same theme (needs a reboot it seems) and that just behaves exactly the same. Any ideas?  

Thanks!

---

### Post by vasa1 on 2016-01-24
> **midgleyi said:**
> ... I noticed that there is no indication that the machine is actually doing anything, nor on other application loads.  I have been into preferences and can see a couple of standard cursor themes DMZ White and Black which include a round "busy" type cursor of the type I would be expecting. ... Any ideas?  
Thanks!
I think what you want is called "startup notify". I think Lubuntu doesn't support that. Re. the busy cursor, I see that only after a GUI program is loaded and some operation takes some time.

Edit: Googling led me to this: [https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1336521](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1336521) That bug indicates the problem lies in Openbox. Newer versions of Openbox, sadly not the one in Lubuntu 14.04, may have fixed this problem. I didn't find a ppa for a more recent Openbox built for Trusty.

Oops, you're on 15.10 which has Openbox 3.6.1! So I'm not sure why you aren't seeing the "waiting" cursor. Maybe try yet another cursor theme?

---

### Post by midgleyi on 2016-01-25
Seems from a bit more of a dig around on Google, this issue is widely reported in LXDE but I haven't found a working solution in the posts just yet. Because Chromium takes sooooooooooooo long on my machine to load, I've actually set it to autostart and also set startupnotify=true, but that doesn't make any difference. I'll see if I can find another cursor theme to try as you suggest - thanks!

---

### Post by midgleyi on 2016-01-25
Got a bit of a problem now. I managed to download a cursor theme (Comix) and get that working. It actually didn't make any difference to my original issue - but now I've come to remove it, when I hit the remove button, LXAppearance just exits without any error and without removing anything. I can't put any other themes in either by the look. Any idea what it might be upset about?

---

