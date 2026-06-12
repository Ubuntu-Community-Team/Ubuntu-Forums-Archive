---
title: "Xubuntu on my laptop / Requirements"
date: 2007-04-23
forum: General Help
---

### Post by Strid on 2007-04-23
While Ubuntu runs fine on my desktop, my laptop is still running Windows XP. It's not the newest of all laptops and I tried to run Ubuntu on it, which was rather slow on the laptop.


Its a 800 MHz, 192 mb RAM, and 80 GB HDD Compaq something. 

Do you think that Xubuntu would run smoothly on this thing? What would the minimum requrements for a smoothly running (X)ubuntu machine be?

Thanks,
Anders Christensen

---

### Post by aysiu on 2007-04-23
Xubuntu could run smoothly on it, but I'd advise a window manager like IceWM instead:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by cookfromfrozen on 2007-04-23
I run Xubuntu on a 600 MHz P3 with 128 MB of RAM.  It is very usable, slightly slower than XP on the same machine, but still definitely usable.

---

### Post by simonn on 2007-04-23
> **aysiu said:**
> I'd advise a window manager like IceWM instead

I did some testing a couple of weeks ago. The difference in memory usage between iceWM and XFCE is barely, if at all, noticeable. The windows manager seems to make very little difference. Firefox and X11 are the real memory hogs, both of which are pretty much unavoidable if you want to have a decent/normal desktop OS (No, opera and konqeror do not save you any/much memory if you are running them on a GTK based system).

IMHO, Xubuntu will be smoother than XP on that lappy, but do not expect miracles - there ain't no free lunches.

---

### Post by aysiu on 2007-04-23
> **simonn said:**
> I did some testing a couple of weeks ago. The difference in memory usage between iceWM and XFCE is barely, if at all, noticeable. The windows manager seems to make very little difference. I'm sure that's why Puppy Linux uses IceWM and Damn Small Linux uses Fluxbox. I've seen a huge difference, and so have many others. I'm sorry your testing didn't see that, too. > Firefox and X11 are the real memory hogs, both of which are pretty much unavoidable if you want to have a decent/normal desktop OS (No, opera and konqeror do not save you any/much memory if you are running them on a GTK based system). But Galeon, Epiphany, or Dillo will.

---

### Post by RedSquirrel on 2007-04-23
> **simonn said:**
> I did some testing a couple of weeks ago. The difference in memory usage between iceWM and XFCE is barely, if at all, noticeable. The windows manager seems to make very little difference. 



What are the specs of the machine you used for testing? 

Sometimes on a really fast machine, everything is fast and you won't see any difference in performance. 

On the other hand, if you try GNOME or KDE on older hardware it will likely be sluggish and the only way to squeeze maximum performance out of the machine is to use a barebones install with your choice of lightweight WM (IceWM, Fluxbox, etc.). 

Note as well that a system with a lightweight WM installed on top of GNOME or something will not be as fast as the barebones install.

---

### Post by aysiu on 2007-04-23
> **RedSquirrel said:**
> 
Note as well that a system with a lightweight WM installed on top of GNOME or something will not be as fast as the barebones install. Even if you're not running any of the Gnome services?

---

### Post by bws on 2007-04-23
I'm running a 650MHz P3 with 256MB of RAM.  As I mentioned elsewhere, boot-up times have been cut in half from Windows 2000.

I do use Firefox which isn't bogged down with a lot of plug-ins, so it isn't any worse.  I may try Gaelon although I do want a way to block ad banners on web pages the way Adblock Plus and NoScript are able to do.  I'm sick of those java-script animations suddenly appearing out of nowhere, blocking my view.

---

### Post by RedSquirrel on 2007-04-23
> **aysiu said:**
> Even if you're not running any of the Gnome services?

Good point. The nice thing about the barebones install though is that you dont' have to turn them off. 

Also, if one makes a point of using lightweight applications to replace the ones in GNOME, the system will be even faster. I can't imagine installing the barebones system and then adding a bunch of programs that have GNOME dependencies.

---

### Post by simonn on 2007-04-23
> **aysiu said:**
> I'm sure that's why Puppy Linux uses IceWM and Damn Small Linux uses Fluxbox. I've seen a huge difference, and so have many others. I'm sorry your testing didn't see that, too.

> **RedSquirrel said:**
> 
On the other hand, if you try GNOME or KDE on older hardware it will likely be sluggish and the only way to squeeze maximum performance out of the machine is to use a barebones install with your choice of lightweight WM (IceWM, Fluxbox, etc.). 

Sorry, I was excluding Gnome and KDE and should have made that clear. I was comparing XFCE, iceWM and Fluxbox. The differences were minuscule.

> **aysiu said:**
> But Galeon, Epiphany

Both of which have **firefox** (or mozilla) and gnome dependencies.

> or Dillo will.

Which does not support CSS and Javascript... May as well use lynx.

---

### Post by aysiu on 2007-04-23
> **simonn said:**
> Sorry, I was excluding Gnome and KDE and should have made that clear. I was comparing XFCE, iceWM and Fluxbox. The differences were minuscule. And I'm saying they're not. No one who wants performance on a computer with 32 MB of RAM is going to advise you to use XFCE over Fluxbox or IceWM.

> Both of which have **firefox** (or mozilla) and gnome dependencies. But they still run more lightly than Firefox.

> Which does not support CSS and Javascript... May as well use lynx. Quite an exaggeration there? Dillo has point-and-click functionality and image display. Lynx doesn't.

---

### Post by simonn on 2007-04-23
> **aysiu said:**
>  No one who wants performance on a computer with 32 MB of RAM is going to advise you to use XFCE over Fluxbox or IceWM.

No one who wants performance is going to use 32Mb of RAM. That is barely enough to run a GUI-less firewall distro.

>  Quite an exaggeration there? Dillo has point-and-click functionality and image display. Lynx doesn't.

But a lot of websites will not work properly without javascript.

> **RedSquirrel said:**
> What are the specs of the machine you used for testing?

A vm on qemu 0.9, running on a Sempron 64 3000+ with 1Gb RAM running Xubuntu edgy.

> **RedSquirrel said:**
> 
Note as well that a system with a lightweight WM installed on top of GNOME or something will not be as fast as the barebones install.

Also, if one makes a point of using lightweight applications to replace the ones in GNOME, the system will be even faster. I can't imagine installing the barebones system and then adding a bunch of programs that have GNOME dependencies.

Sorry mate, but I do know what I am doing. Distro schmistro, liteweight shiteweight... the ps command tells you exactly what you are running and what resources are being used. Stop every process you can and take it from there.

---

### Post by RedSquirrel on 2007-04-23
> **simonn said:**
> Sorry mate, but I do know what I am doing. Distro schmistro, liteweight shiteweight... the ps command tells you exactly what you are running and what resources are being used. Stop every process you can and take it from there.


It's just my opinion, but I feel it's easier to go with a barebones install with lightweight applications rather than starting with something heavy and trimming down. Both are valid approaches, it just depends on what sort of challenge one is looking for. :)

IMO, on older systems it does make a difference if you run lighter applications. They load faster, have fewer dependencies, and are (sometimes!) more stable. But that's one of the nice things about using a linux-based system: choice. If someone prefers middle-weight or heavy apps, there are plenty to choose from.

By the way, looking back on this thread, you *did* make it clear that you were comparing IceWM and Xfce. It was my mistake to introduce GNOME/KDE into this discussion. Sorry about that. And I didn't mean to imply that you didn't know what you were doing, but it looks like I did. Sorry.

---

### Post by Strid on 2007-04-25
Hi guys,

Thank you for all the suggestions! I just installed a fresh Ubuntu onto it. While starup of applications seems to be sluggish, it seems like everything works. Also the good news was that it has 320ish MB ram on it, which is more than I though! I've had Damn Small Linux on it previously but honestly, I find having a "full" OS like Ubuntu on it so much better.

---

