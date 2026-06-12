---
title: "Rogue Evolution processes on start-up"
date: 2013-05-17
forum: General Help
---

### Post by guice on 2013-05-17
I have two issues here. Why are there un-managed Evolution processes running when I explicitly do not have Evolution running? And how can I stop these processes from even starting automatically on startup?

First issue: When I exit Evolution, I still have 'evolution-calendar', 'evolution-source-registry', and 'evolution-addressbook-factory' still running. Why? When I explicitly exit Evolution, *all* associated evolution processes should be terminated. I can't even kill calendar or source-registry -- they come right back!

This comes into my second problem: Upon boot, my networks aren't correct. I have to enable a couple routes before Evolution can properly connect to our internal Outlook OWS. This is a problem when evolution-calendar and evolution-source-registry starts up before I'm able to enable these routes: these processes get hung, and nothing works until I run a kill command on them.

I had expected exiting Evolution would exit these other processes, thus correcting the issue. But this never happens... I have to manually running 'kill' on these rogue processes.

---

### Post by Ejdesgaard on 2014-03-09
I can confirm that this issue is also relevant for 14.04 as of this writing.

---

### Post by soldersplash on 2014-04-03
> First issue: When I exit Evolution, I still have 'evolution-calendar', 'evolution-source-registry', and 'evolution-addressbook-factory' still running. Why? When I explicitly exit Evolution, all associated evolution processes should be terminated. I can't even kill calendar or source-registry -- they come right back!

This comes into my second problem: Upon boot, my networks aren't correct. I have to enable a couple routes before Evolution can properly connect to our internal Outlook OWS. This is a problem when evolution-calendar and evolution-source-registry starts up before I'm able to enable these routes: these processes get hung, and nothing works until I run a kill command on them.

Me too! I read elsewhere that gnome-shell is starting the evolution-source-registry and evolution-calendar. Presumably for gnome-shell calendar integration, which is fair enough. But whats the deal with start up sequence of network and evolution? Any delay in my laptop finding the wi-fi connection and evolution ends up hung.

---

