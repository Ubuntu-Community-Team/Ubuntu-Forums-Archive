---
title: "Gnome not starting"
date: 2008-01-24
forum: General Help
---

### Post by peterf1972 on 2008-01-24
Hi everybody!

had a nice Gutsy system running, and broke it :-(

Computer boots up fine, but when i login it just stops rigth there. login screen disappears and the background has the standard ubuntu color, but nothing else happens. HDD has no activity, but i can switch between the virtual screens (1 & 2) and i can open terminal sessions. I tried several things in the console, but could not figure out exactly what was wrong. Starting in GNOME failsafe mode tells me, that gnome is not installed....

Ok, now to what i did before this problem occcured.

I tried to install the new OSS 4 sound drivers, and i tried cleaning up the system and deleted about every eventum appearance with the package manager.

i tried to install gnome from the console, and i got the response, that gnome is installed, but that dependencies are missing (for example a few eventum things), but downloading those fails as there is no network connectivity.

I have connected the computer via CAT5 to my router, but was not able get the network running.

I do have access to the ubuntu cd rom (after mounting it), but apt-get did not acccess the necessary files from cdrom.

Any idea how i can revive teh system without reinstall?

Almost forgot: created a new user form the console, and that user had the same problems loggin in.

Thanks for all your help!

---

### Post by mali2297 on 2008-01-24
Do you have the Alternate CD?

If so, try the advice from [here]("http://www.psychocats.net/ubuntu/nox").

> 
Do you have a graphical environment installed?
The first step requires you to have a software repository. In most cases, if you're connected to the internet, the commands given will use your internet connection. If you don't have an internet connection but do have the Ubuntu Alternate Installer CD, insert it in your drive and type

sudo apt-cdrom add

This will add the CD as a software package source since you can't get packages from the internet.

To make sure you have a graphical environment installed:

sudo aptitude update
sudo aptitude install ubuntu-desktop

If you didn't already have it installed, you'll notice Ubuntu downloading and installing a whole bunch of packages, either from the internet or from your CD.

If you did have it installed, you'll simply be told ubuntu-desktop is already the newest version.


---

### Post by peterf1972 on 2008-01-24
thanks, downloading alternate cd right now...

> **mali2297 said:**
> Do you have the Alternate CD?

If so, try the advice from [here]("http://www.psychocats.net/ubuntu/nox").

---

### Post by SpookyET on 2008-03-12
GNOME requires ALSA. OSS 4 can masquerade as ALSA. That is not the issue. It's looking for an ALSA library, which is missing if you uninstalled alsa. You have to keep ALSA around.

---

