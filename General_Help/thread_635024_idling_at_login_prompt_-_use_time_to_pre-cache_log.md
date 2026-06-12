---
title: "idling at login prompt - use time to pre-cache login?"
date: 2007-12-08
forum: General Help
---

### Post by weblordpepe on 2007-12-08
Hello there.

I noticed a great many people load up their computer, and idle at the login box for a few seconds or even a few minutes (while they unpack, plug in laptop charger etc). I figure this time could be put to good use:

Anyone know what I can use to write a script during the idle time the login prompt?
I figure a simple script which loads a bunch of gnome libraries into memory (even while user is typing their password) would go a good way to speeding up the login process.

The end goal: When the user hits 'enter' and their desktop starts to appear, a good portion of gnome/system-libraries would have been loaded already.

What do you guys reckon? I gather I will need to find some Gnome documentationz which will let me know what files to  pre-load. But I need to know how to create a script that runs at the login prompt.

I figured even just copying the files to /dev/null would leave a cache of em in memory. Or is there a special utility to pre-cache files into memory?

---

### Post by Rhubarb on 2007-12-08
You might want to try out **preload** from the repositories.
> **adaptive readahead daemon**
preload monitors applications that users run, and by analyzing this
data, predicts what applications users might run, and fetches those
binaries and their dependencies into memory for faster startup times.

Note that installing preload will not make your system boot faster
and that preload is a daemon that runs with root priviledges.

 Homepage: [http://preload.sourceforge.net/](http://preload.sourceforge.net/)

If that's not quite what you're after, you could put a scipt into your /etc/init.d/ folder, and have your script executed at start up.

---

### Post by weblordpepe on 2007-12-08
I have a script somewhere that was set to launch when the runlevel changed. I can't remember how it was set up, but when the graphical login box appeared it spoke 'bla bla bla bla bla'
that timeframe (even the 1 or 2 seconds) where the user is typing their password is time that can be used loading.

---

