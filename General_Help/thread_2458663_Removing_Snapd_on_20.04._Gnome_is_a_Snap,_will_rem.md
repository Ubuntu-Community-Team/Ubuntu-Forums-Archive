---
title: "Removing Snapd on 20.04. Gnome is a Snap, will removing it break my system?"
date: 2021-03-01
forum: General Help
---

### Post by galacticstone on 2021-03-01
I want to completely remove and disable Snapd from my system. I don't have many and my list of Snaps is :

> Name               Version                     Rev    Tracking         Publisher   Notes
core               16-2.48.2.1                 10823  latest/stable    canonical&#10003;  core
core18             20210128                    1988   latest/stable    canonical&#10003;  base
gnome-3-26-1604    3.26.0.20200529             100    latest/stable/…  canonical&#10003;  -
gnome-3-28-1804    3.28.0-19-g98f9e67.98f9e67  145    latest/stable    canonical&#10003;  -
gnome-3-34-1804    0+git.3556cb3               66     latest/stable    canonical&#10003;  -
gtk-common-themes  0.1-50-gf7627e4             1514   latest/stable    canonical&#10003;  -
snap-store         3.38.0-59-g494f078          518    latest/stable/…  canonical&#10003;  -
vlc                3.0.12.1                    2103   latest/stable    videolan&#10003;   -

I see that Gnome is a Snap. Will removing it break my system? Should I Install a non-Snap Gnome before deleting the Snap?

---

### Post by deadflowr on 2021-03-01
Those relate to runtimes and libraries for snaps to integrate with the desktop to run properly.
Removing those won't do anything to the desktop itself.

You can remove all of them, note that you'll need to reinstall the apt version of vlc.
And snap store can be replaced with either gnome-software or synaptic.

---

### Post by galacticstone on 2021-03-02
Thanks! I removed Snap completely and my boot-time went from 1min-47sec to about 56sec - an improvement of almost one full minute!

---

