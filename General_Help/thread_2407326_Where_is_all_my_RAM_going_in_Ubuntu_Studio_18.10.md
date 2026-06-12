---
title: "Where is all my RAM going in Ubuntu Studio 18.10?"
date: 2018-12-02
forum: General Help
---

### Post by handsomegenius on 2018-12-02
Hey everyone,

I switched from Windows 10 to Ubuntu Studio 18.10 about a month ago. I really like it.

I noticed though that if I leave it unattended for a while and then come back, it gets really slow and unresponsive. Windows would do that too, but you'd have to leave it a few days without rebooting.

Which is weird, because when it's freshly booted, Ubuntu Studio is *way* faster than Windows on the same machine. It just flies.

I initially figured that it was Firefox just chewing up all the memory, as browsers tend to do.

But after paying a little more attention to how the memory is being used, it actually seems to happen without running anything.

Just as an experiment, I rebooted the machine before I went to bed, ran "free -m" and then just left it to idle overnight. I then ran "free -m" again to see what was happening.

This is the result:

[IMG]http://i63.tinypic.com/287lqwy.png[/IMG]

That's happening with an empty desktop left idle.

Anyone got any ideas what's going on here? How do I delve into this further?

It actually isn't too big of a problem. The OS boots so much faster than Windows that it's not really a problem to reboot. But it's got me very curious.

---

### Post by Impavidus on 2018-12-03
It seems that the memory is actually used by an application, not by buffers/cache. Try and find out which application:```
top -b -n1 -o RES
```That should list all processes ordered by RAM usage.

---

### Post by handsomegenius on 2018-12-03
Thank you very much. That's a handy command.

ATM, looking in the "RES" column, it's showing that Firefox has about 650MB, which seems about right, 188MB to Dropbox, and then there are a few "Web Conte+" processes with about 180MB to 380MB each.

When I get a moment, I will reboot it and then leave it to idle a while so that these numbers distorted by my actual usage.

---

### Post by TheFu on 2018-12-04
There was a huge memory leak in gnome, something related to the desktop in the 17.10+ timeframe.  It wasn't fixed in 18.04 and I haven't followed the solution since I don't use any DE.  I vaguely remember that restarting some Gnome process every day was the recommended solution.  It didn't force-close any other applications, so your desktop should remain.   [https://www.omgubuntu.co.uk/2018/03/gnome-shell-memory-leak-is-being-fixed](https://www.omgubuntu.co.uk/2018/03/gnome-shell-memory-leak-is-being-fixed) is what I'm remembering.

But it is always best to have the real data to determine where the issue lies.  You can run top in a batch mode, write the output to a file, say once an hour, then review that file every few days to see which processes are growing.

---

### Post by handsomegenius on 2018-12-04
Thanks fu.

I'm pretty sure this is xfce though.

I rebooted the machine last night, ran both commands, left it to idle overnight and then ran both commands again:

[IMG]http://i65.tinypic.com/14sdwxw.png[/IMG]

So far it's still a mystery as to where the memory is going. Scrolling through the lower sections of the terminal windows, it's still fairly evenly matched.

---

### Post by handsomegenius on 2018-12-09
Does anyone have any ideas for what else I should look at here?

---

