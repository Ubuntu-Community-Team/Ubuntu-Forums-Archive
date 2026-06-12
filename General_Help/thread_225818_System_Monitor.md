---
title: "System Monitor"
date: 2006-07-30
forum: General Help
---

### Post by Roasted on 2006-07-30
Just trying to understand something. In Windows, generally only the stuff you want running would appear in the task manager, and I'd just exit out whatever I didn't want running. Yesterday I was having some trouble getting Amarok to work and it just wouldn't open. So I went to system monitor and here there's like 12 Amarok's "sleeping" there. What in the world? What does sleeping mean, just sitting idle? I assume multiple programs of the same like running are what cause jamups like I experienced?

Like right now, I've probably got 40 things running. Everything is sleeping but 2 items. I have like 10 gnome things running, gaim, gaim server, esd, dbus-daemon, dbus-launch, trash applet, etc. Are these all normal?

---

### Post by vigleik on 2006-07-30
I have 125 processes running. 40 sounds like way too few. If I only count the processes owned by the user, it's 54, in which case 40 sounds reasonable if you have fewer things open than me.

Vigleik

---

### Post by cssutto on 2006-07-30
I have 42 running.

I can't understand how anyone can determine what should be on someone else's system.

I would think it would depend on what you are doing with your system.

For instance, I would expect someone on a network to have a  lot of stuff running that I would not have on my laptop.

Or a stand alone desk top.

CSSJR

---

### Post by Roasted on 2006-07-30
Well, what does sleeping mean? Is that when those particular things are idle? Are these things programs that I'm running, or are they system files to keep the GUI running? Is it like in Windows where I go to msconfig and can alter what starts up and what doesn't?

---

### Post by vigleik on 2006-07-31
Yes, sleeping means idle. It seems that the gnome-system-monitor only shows the processes owned by the user, as opposed to for example top. There are lots of other processes, such as init, which run on every linux system, so counting those 40 is too few. (It might be theoretically possible, but not with stock ubuntu.) Counting only your own, as reported by gnome-system-monitor, 40 is normal.

Anyway, some of the processes you see are there to run gnome, while others are the programs you are using. Note that some programs might have 2 or more processes, which is okay.

cssutto: check your processor count again, with something like top. I bet you have more than 100 processes there.

Vigleik

---

