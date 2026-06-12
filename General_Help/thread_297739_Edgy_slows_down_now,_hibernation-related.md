---
title: "Edgy slows down now, hibernation-related?"
date: 2006-11-11
forum: General Help
---

### Post by fuujin on 2006-11-11
Ok, My last post didn't go through on this so I'll try to keep it shorter. Basically, I upgraded to Edgy a few weeks ago and had no real problems with it at all (great distro nowadays imo). However, after trying to hibernate yesterday, now it wants to slow down at random times. I have narrowed down the cause to a few programs/factors

- First noticable freeze-up was during an update-manager session. I had firefox running the first time, but it still freezes every time it tries to install updates now (resorted to aptitude to get the updates so I know that works at least).

- Add/Remove Programs is broken now. If you click apply, then the main window fades out like always, but no asking for a password or progress of any kind on installing. Other times, it'll lock up.

- If firefox is running, I've had issues running gedit, gnome-terminal, and the "about ubuntu" menu option. They all freeze or nearly freeze upon being opened or shortly thereafter.

- Viewing my own profile on myspace locked it up once. My guess is it's flash-related there, but this is a recent development so why flash is acting up now is beyond me.

- When I tried hibernating, it went black screen and one terminal line appeared saying a device could not be accessed or something with address numbers for the hardware (I think that's what it was at least). Problems arose later that day.

- No installation of software has taken place that should affect this.

- Gnome system monitor has been less than helpful as I see no spikes in memory/cpu usage by programs when I manage to open it before a total freeze. Even tried top so don't ask.

Any help would be appreciated, I can provide more info if needed so thanks in advance!

---

### Post by SteveF on 2006-11-17
I don't know if this will help, but I've been reading a few issues with the swap partition after people have tried hibernating.  So a search for "swap edgy" and you should see a few hits.  It may be related to your problem.

Lack of swap space would cause the system slow down and some apps not working and hibernate having an issue.

Steve

---

