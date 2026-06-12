---
title: "pypanel ripping off my resource!"
date: 2007-10-30
forum: General Help
---

### Post by oldcpu on 2007-10-30
So I was trying out openbox.  But it does not have a taskbar.  I installed pypanel and looked at how much resource it used.  To my surprised, it uses more resource than openbox or fluxbox!

That little tiny thing on the bottom uses more resource than a windows manager?  How is that so?  Fluxbox comes with its own taskbar and it uses less resource than pypanel!

Is it just me?  Or is this really how much resource pypanel uses?  Any of you using pypanel?  If so, would you please confirm if pypanel is indeed using more resource than fluxbox or openbox?

---

### Post by jviscosi on 2007-10-30
I seem to recall pypanel slowing things down on my machine when I tried it a long time ago.  I still have it lying around and will try it again to confirm.

You might want to look at perlpanel or fbpanel instead.  I've used both (eventually settling on fbpanel) and they don't suck down too much in the way of resources.

---

### Post by jviscosi on 2007-10-31
I just tried pypanel again and it maxed out at about 2% of CPU, which isn't as bad as I remember, but I haven't used it in a long while.  When it wasn't actively updating it dropped lower than that.  Probably it's highly dependent on your version of python.

I'd still recommend checking out perlpanel or fbpanel instead.  I find them more functional.

---

### Post by urukrama on 2007-10-31
It is like that on my computers as well. It is normal.

> **jviscosi said:**
> I'd still recommend checking out perlpanel or fbpanel instead.  I find them more functional.

Perlpanel is much heavier on resources than pypanel, though it has more options. I'm not too sure about fbpanel, as I've never really used it.

---

### Post by rjmdomingo2003 on 2007-10-31
Why not try tint task manager?

---

### Post by jviscosi on 2007-10-31
> **urukrama said:**
> Perlpanel is much heavier on resources than pypanel, though it has more options. I'm not too sure about fbpanel, as I've never really used it.

On my machine fbpanel uses about 80K more memory and roughly the same CPU time as pypanel.  It's worth it to me for the pretty icons.  ;-)  

Perlpanel seems to use about twice as much memory as fbpanel and a similar CPU utilization to the other two.  I should point out that it's also more functional than fbpanel -- it has GUI configuration of plugins, you can drag plugins around, etc.  It's more like the Gnome panel.  However, I don't really care for the way it themes, and it won't go vertical along the side of the screen.  These are the main reasons I don't use it.

Of course, YMMV.

---

### Post by oldcpu on 2007-10-31
I have tried fbpanel before, and did not like it, because it was very GNOME-like; did not match the Openbox theme I was using.

I am trying to go for something lite since this is an old machine.

I looked into tint, but it turned out to be some kind of Tetris game.  I looked it up in the Ubuntu package site and there was no task manager by that name.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=tint&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=tint&searchon=names&subword=1&version=feisty&release=all)

---

### Post by mali2297 on 2007-10-31
> **oldcpu said:**
> I have tried fbpanel before, and did not like it, because it was very GNOME-like; did not match the Openbox theme I was using.

I am trying to go for something lite since this is an old machine.

I looked into tint, but it turned out to be some kind of Tetris game.  I looked it up in the Ubuntu package site and there was no task manager by that name.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=tint&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=tint&searchon=names&subword=1&version=feisty&release=all)

See here:
[http://code.google.com/p/ttm/](http://code.google.com/p/ttm/)

I hope you didn't install the Tetris clone, the name conflict will confuse the system.

---

### Post by jviscosi on 2007-10-31
GDesklets offers a number of taskbar-style widgets but I wouldn't characterize it as "lightweight".

Tint looks pretty slick and on my box uses about half the resources of pypanel and fbpanel.  That's probably a good choice.

---

### Post by urukrama on 2007-11-01
Or you can *not* use a panel. It takes a little while getting used to it, but it creates a great working environment. Try it out, and see if you like it.

---

### Post by oldcpu on 2007-11-01
I just tried tint.  It uses almost as much resource as Openbox.  And it takes a few seconds to start.

I am trying to get used to no panel.  However, at the moment, it is much quicker to point-and-click than to cycle with Alt+Tab.

---

