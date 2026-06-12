---
title: "AWN uses more ram after hours"
date: 2008-07-06
forum: General Help
---

### Post by ptgood on 2008-07-06
When i start up the system, the python process of the AWN, uses around  **11MB of ra**m

But after one hour it takes around **ram 50MB**, and sometimes up to **ram 150MB**.
If i colse it and restart, it gets back to **ram 11MB**.

Can anyone tell me why, please?

---

### Post by monoufo on 2008-07-06
the technically term for that is called a memory leak and it is caused by bad programming.  You will have to file a bug report. 

On my system, one of the clock/calander apps caused a huge memory leak in python, filling up my whole swap partition and bringing the computer to a crawl or crash. SO far, the other applet is running just fine, but I don't like it as much.  That will probably be fixed soon enough.

---

### Post by propolis on 2008-07-06
AWN is nice an I used it for some time. The problem is that being based on Python it its easy to code extensions but it requires a lot o memory. It takes me 9-10 Mb just for a desktop switcher.

I have been using Cairo-Dock that is written in C and is very customizable and have a great mac-like wave effect. In my opinion it is the best dock for Gnome. I substituted my Cairo-clock standalone for the Cairo-clock detached from Cairo-dock as a desklet saving 8 Mb of memory.

---

### Post by moonbeam on 2008-07-06
> **propolis said:**
> AWN is nice an I used it for some time. The problem is that being based on Python it its easy to code extensions but it requires a lot o memory. It takes me 9-10 Mb just for a desktop switcher.

I have been using Cairo-Dock that is written in C and is very customizable and have a great mac-like wave effect. In my opinion it is the best dock for Gnome. I substituted my Cairo-clock standalone for the Cairo-clock detached from Cairo-dock as a desklet saving 8 Mb of memory.

awn is actually not based on python.  The core bar is pure C.  As are a significant number of applets.  Applets can currently be easily written in C, Python or vala.  The architecture just makes it easy to write bindings... so expect more to appear over time.

---

### Post by moonbeam on 2008-07-06
> **ptgood said:**
> When i start up the system, the python process of the AWN, uses around  **11MB of ra**m

But after one hour it takes around **ram 50MB**, and sometimes up to **ram 150MB**.
If i colse it and restart, it gets back to **ram 11MB**.

Can anyone tell me why, please?

If you'd like to maximize the chance of it being fixed...Please determine the PID of the leaking applet.

Once you've done that then do something along he lines of

ps aux | grep PID

Where PID is the number.  You'll be able to see the culprit applet's name here.

and also do a 

pmap -d PID

Once you've done that open a bug report at 

[https://bugs.launchpad.net/awn-extras/](https://bugs.launchpad.net/awn-extras/)

Include the output from those commands and Also include the repo in use (awn-testing, reacocard's etc) and any other system info you feel is relevant.

If we get this info... it has a decent chance of being fixed eventually (the speed will determine if the applet has an active maintainer or not).

Thanks for using awn.

---

