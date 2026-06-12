---
title: "Sluggsh UI...the one thing stopping me from using Ubuntu."
date: 2006-11-05
forum: General Help
---

### Post by mwob on 2006-11-05
Hi all.

I'm a bit peeved off with Ubuntu's general UI performance. I installed the latest 64-bit Edgy release of Ubuntu when it was released, because I'm keen to see if I could seriously use it as an alternative to XP.

But from a fresh install, I find the UI is just too slow for me - it just can't keep up. I'm running an AMD3500 64, with 768 Meg of memory. My GFX card is a ATI Radeon 9550 - not cutting edge but very capable! I'm talking about screen drawing - things like switching apps (alt-tab), resizing/moving windows, and even clicking into a text box to type - its all just a bit too slow! I installed the ATI (unofficial) driver to see if it made a difference, but it seems the same.... XP in comparison flies.

Even if Gnome was ignoring my gfx card and using the CPU for all UI rendering, I just wouldn't expect it to be this unresponsive. Is there anything I can do is it just tough?

Thanks

Matt

---

### Post by .t. on 2006-11-05
Are you using fglrx?

---

### Post by tronica on 2006-11-05
yeah it sounds like you don't even have the gfx drivers installed.

---

### Post by mwob on 2006-11-05
Yep, I followed the guide here : [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)


It seemed to go OK , and when I type "fglrxinfo" I get the correct info:  

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
...

To be honest I didn't notice a difference before I had installed it and afterwards. Even with this set, it still just goes slow :( I'm not saying its unusably slow, but its slow enough for me to be annoyed with it. For example, if I Ctrl-Tab to open a new tab I get a half-sec to 1 second pause. Moving a window is really slow, it can't keep up.

Could I have something wrong with my xorg.conf? Or could I perhaps have a graphics card that is badly supported?

---

### Post by TheRingmaster on 2006-11-05
maybe you need to try a lighter desktop manager like xfce.

---

### Post by nikhilk on 2006-11-05
Yes, it is true that ATI's drivers for Linux are not as good as that of Nvidia's drivers.
As "TheRingmaster" suggested maybe you should give some other lightweight desktop managers a try and see if they perform any better.

---

### Post by Amt0571 on 2006-11-05
For me Ubuntu's UI was also very slow, until I installed Kubuntu...

For some reason, KDE is way way faster than gnome in Ubuntu (more or less like Win XP on my system).

If you don't mind using KDE, maybe you can give it a try.

---

### Post by TheRingmaster on 2006-11-05
kde-core is supposed to be pretty fast.

---

### Post by d3v1ant_0n3 on 2006-11-05
For me, Gnome in Ubuntu FLIES compared to XP. I found XP a little laggy, but GNOME is great, even with Beryl running a lot of effects.

The only issue I can think of is the one many have mentioned- your ATI drivers. Other than that, your specs are superior to mine by far.

---

### Post by brottman on 2006-11-05
mwob, open a terminal and type 'glxgears' and that will tell you if your graphics drivers are installed right. It will bring up a box with rotating gears, and they should be rotating very smoothly. If there is any hesitation something ain't right yet.

---

### Post by sloggerkhan on 2006-11-05
I definately agree that something's wrong with his install. Maybe he should make sure his overlays are on?

---

