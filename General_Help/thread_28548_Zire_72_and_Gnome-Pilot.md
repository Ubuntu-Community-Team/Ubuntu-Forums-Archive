---
title: "Zire 72 and Gnome-Pilot"
date: 2005-04-20
forum: General Help
---

### Post by Kigresyl on 2005-04-20
So far, through the UbuntuWiki and various Google searches, I have not found a workable solution - though I might add I'm quite new with Linux.

I'm trying to connect my Palm Zire72 via USB, and it's just not working. I don't see any USB devices listed in /dev/, either.

Please direct me towards a total solution for this madness. Thanks.

---

### Post by TravisNewman on 2005-04-21
Have you tried this one out?
[http://howtos.linuxbroker.com/howtoreader.php?file=PalmOS-HOWTO.html](http://howtos.linuxbroker.com/howtoreader.php?file=PalmOS-HOWTO.html)

It's the one that got me through-- I tried probably 20 howtos before I found that one, and that one worked wonders.

---

### Post by Bob D. on 2005-04-21
I won't swear this will work as I haven't had a chance to try this myself. However, this worked just fine on my Fedora Core 3 box which uses udev, as does Ubuntu.

[http://fedoranews.org/tchung/gnome-pilot/]("http://fedoranews.org/tchung/gnome-pilot/")

The key point is the update in the gray box near the top of the page. I couldn't get it to work with ttyUSB1 on my FC3 box...ttyUSB0 did work and syncs fine.

Bob

---

### Post by Kigresyl on 2005-04-21
[QUOTE=panickedthumb]Have you tried this one out?
[http://howtos.linuxbroker.com/howtoreader.php?file=PalmOS-HOWTO.html](http://howtos.linuxbroker.com/howtoreader.php?file=PalmOS-HOWTO.html)

It's the one that got me through-- I tried probably 20 howtos before I found that one, and that one worked wonders.[/QUOTE]
 Yeah, I've already tried it, and it's something you link to in every similar post. It just didn't work out for me for some reason :-\ Thanks though.

I'm gonna try out the fedora link. Thanks for that as well, just hope it works.

**Edit:** Second article works like a charm. Thanks for the replies.

---

### Post by Kigresyl on 2005-04-21
Well, all was good. For some reason now it doesn't want to sync anymore... Hrm.

---

### Post by Bob D. on 2005-04-21
Any luck getting the sync back?

I'd have posted back sooner but my Evolution/Tungsten T combo acted up today and created some 32,000+ blank records (ugh!). It has taken me a while to get that cleaned up. Unknown as to why it happens...3rd time in last 3-4 months.

When you say the sync won't work, is that for all conduits? Does the gnome-pilot daemon window pop up to show the sync progress, but nothing sync's? Or is it a case of nothing happening.

Bob

---

