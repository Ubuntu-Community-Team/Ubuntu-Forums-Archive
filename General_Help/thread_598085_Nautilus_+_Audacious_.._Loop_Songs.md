---
title: "Nautilus + Audacious .. Loop Songs?"
date: 2007-10-31
forum: General Help
---

### Post by DjBones on 2007-10-31
well.. i've been using audacious/xmms practically forever, but i've stumbled on a new configuration that i like alot more (using nautilus as the library browser basically)

i think the descending tree format is alot easier to navigate, and xmms or audacious can't do that to my knowledge [SIZE="1"](although i vaguelly remember a pimped out xmms that had all the library functions, although it could have been a skin for amarok that looked a ton like xmms)[/SIZE]

the only problem is that since that when you click on each song in nautilus, it becomes the sole thing in the playlist so it doesn't loop to any others.
I'm trying to have it play the next song in line inside nautilus,
any ideas? maybe a nautilus plugin? a script?

heres a screen so you guys sorta know whats goin on lol
thanks by the way!

---

### Post by MrFSL on 2007-10-31
Sure right click on your media file and go to "Open with > open with other application"

Next click on use a custom command.

Finally use the -e option to not clear the playlist:

something like: 
```
audacious -e %1
```

---

