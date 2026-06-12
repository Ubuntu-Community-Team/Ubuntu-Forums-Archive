---
title: "Congested and slow"
date: 2008-03-09
forum: General Help
---

### Post by dawhistler on 2008-03-09
Is there some way to make my Ubuntu more lean,,,less congested...faster?

I am willing to throw things out and such but dont know what to throw out and/or what to keep.

Any ideas?:-?


Da

---

### Post by Super TWiT on 2008-03-09
You can disable tracker.  Tracker is a file indexer.  It is meant to make searching faster, but it also uses up system resources.  Searching will work without it, but it may be a little slower.  You can disable this by going into a command line and typing ```
killall trackerd
```  You also probably want to disable it from automatically starting.  To do this go into the System menu, then Preferences, and finally clicking on Sessions.  Find the Tracker entry, uncheck it, and click close.  This will stop it from starting with Ubuntu.  If you find it is still too slow you can install Xubuntu.  It is another desktop frontend and uses less resources than the Gnome desktop frontend.  To install this, type in ```
sudo apt-get install xubuntu-desktop
```  After this is finished, you will need to reboot for Xubuntu to load.  There are other ways to speed up the gnome desktop environment if you don't like Xubuntu, however, some of them are complicated and risky.

---

