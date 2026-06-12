---
title: "Ubuntu 6.10 Edgy Login GUI"
date: 2007-03-14
forum: General Help
---

### Post by UpperNinety89 on 2007-03-14
My System:

Intel Pentium 4 3.1 GHz Processor
1 GB RAM
80 GB HDD
GeForce 6200 TurboCache with 256 MB
Realtek Onboard Audio

Ok so to start off my post it might be helpful to let you know that I'm not really skilled in the linux environment yet. Anyway, I'm currently running Ubuntu Edgy in VMware Server and had it up and running fine most of yesterday. However, after applying updates and also installing VMware Tools, I haven't been able to load up the OS past the initial loading screen (picture enclosed in an attachment). After that it just stays there and nothing happens. I have no idea where to go from here so any advice would be fantastic.

---

### Post by visible on 2007-03-14
try booting in recovery mode and look for any odd errors or see where it stops in the boot up procedure.  and then take it from there.  I had a harddrive I was trying to use that did the same hang up at boot and thats how I figured that one out.  The recovery mode deal lists everything that is goin on during boot from what I can figure out.

---

### Post by UpperNinety89 on 2007-03-14
Well I think it could be the xserver or something, but I haven't the slightest clue how to set that up

---

### Post by zvacet on 2007-03-14
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by UpperNinety89 on 2007-03-14
Zvacet:

I know thats probably the big problem, but I don't even know how to get to a terminal window. The Ctrl-Alt-F1 thing you told me to do didn't do anything.

---

### Post by rowdy15 on 2007-03-14
if you go into recovery mode, a black screen comes up....................login and then the terminal line will start...

that is where you put "  sudo dpkg-reconfigure xserver-xorg  "

then you can reconfigure the Graphical User Interface (GUI)

NOTE: read everything at first even if it doesn't make sense and then feel free to do the reconfiguring a few times as it is reasonbly harmless.......the GUI will either work or it won't!!! 

rowdy15

---

### Post by gotglint on 2007-03-31
> **UpperNinety89 said:**
> My System:
Ok so to start off my post it might be helpful to let you know that I'm not really skilled in the linux environment yet. Anyway, I'm currently running Ubuntu Edgy in VMware Server and had it up and running fine most of yesterday. However, after applying updates and also installing VMware Tools, I haven't been able to load up the OS past the initial loading screen (picture enclosed in an attachment). After that it just stays there and nothing happens. I have no idea where to go from here so any advice would be fantastic.I have been generating the same load screen hang, and it might be fruitful to add for those trying to help that Ubuntu boots just fine when I'm NOT running it as a guest OS in Windows XP.

I experienced no problems running Ubuntu as a guest OS after upgrading from Ubuntu 6.06 to 6.10.  I upgraded to VMWare WS 5.5.3 without generating errors, too.  But for whatever reason, the machine started hanging a week or two later and generating the same horizontal graphical glitch identical to your posted screenshot.  I used to get around this by loading in recovery mode, which allowed me to bypass this hang.  Yet, after a while I couldn't even load Ubuntu in recovery mode as a guest OS.  

I re-installed Ubuntu, erased all of my old .vm* files on windows, yet I still have this hang.  (Note that the OS still runs when booting straight from grub and not as a guest OS.)

I'm willing to bet that it's some trivial thing that's making VMware unhappy (i.e. something like in this blog-post [http://www.nth-order.com/tim/?p=21]("http://www.nth-order.com/tim/?p=21"), which outlines dbus version errors.  I didn't have this problem, but I bet there's just some similarly subtle thing that VMware's not liking.

---

