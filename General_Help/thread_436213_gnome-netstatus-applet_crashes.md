---
title: "gnome-netstatus-applet crashes"
date: 2007-05-07
forum: General Help
---

### Post by finer recliner on 2007-05-07
my gnome-netstatus-applet likes to crash all of a sudden. there seems to be a memory leak, because over a period of a couple days, it slowly starts using more and more memory. eventually the applet will just crash at random and ask me if i would like to reload it. a few days later and the same thing will happen.

i'm now up to %15 of my 2Gigs of memory. 

```

$ ps aux |grep netstatus
davef    15675  0.2 15.1 368628 313392 ?       S    May03  11:03 /usr/lib/gnome-netstatus/gnome-netstatus-applet --oaf-activate-iid=OAFIID:GNOME_NetstatusApplet_Factory --oaf-ior-fd=64

```



im using ubuntu 6.06. anyone have any ideas why this is happening or how to fix it?

recent changes to my system:
-installed pidgin
- upgraded my hardware to 2 gigs of RAM
- now using a switch, instead of connecting my laptop directly to the wall.

---

### Post by finer recliner on 2007-05-14
bump


im now plugged directly into the wall (no switch), and it still occurs.

---

