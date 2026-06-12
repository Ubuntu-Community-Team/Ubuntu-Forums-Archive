---
title: "Where does Ubuntu keeps firmware files."
date: 2021-01-14
forum: General Help
---

### Post by gardenair on 2021-01-14
hi,
     I am using Ubuntu 20 on a Laptop just for test point of view. I want to ask one thing that where does  LAN, sound card, graphic card and Bluetooth firmware are loaded durning boot process? If I talk about Debian it keeps the wifi file in /lib/firmware. In the case of Ubuntu what will be ? It is just for the sake of  knowledge.

---

### Post by ActionParsnip on 2021-01-14
Same location. Ubuntu is based on Debian

---

### Post by gardenair on 2021-01-14
I am sure that in Debian the wifi firmware is their inside /lib/firmware rest of the hardware firmware I even not know where actually it keeps the files. Suppose I want to see Graphic card firmware so it will be in the same location?

---

### Post by TheFu on 2021-01-14
Crazy idea - did you look in /lib/firmware?
Ubuntu is over 90% similar to Debian. That last 5-10% were it is different is usually in how system upgrades and packaging differences.  My normal thoughts are assume it works like debian at first, check that, then read any manpages for differences.

For example, **do-release-upgrade** is how to move from release-to-release in the Ubuntu world.  Debian makes people edit their apt-sources files.
Ubuntu has **ubuntu-drivers** which will search, find, and install known-good proprietary drivers for GPUs, NICs, stuff like that.
**ubuntu-security-status** is used to see which packages are directly supported by Canonical, which by 3rd parties and which are unsupported.
I always assume for package management stuff, that ubuntu is a little different than debian, since grabbing a .deb file often will break dependencies in an Ubuntu system in a few months, leading to a system that cannot be patched. If you can't use some other installation type besides a manual .deb file, keep a note about that file so you can manually remove it when/if APT gets stuck in 3-12 months. Remove it, do all the upgrades, seek out a newer version of that .deb file and install it ... still keeping track.  Or use a trusted Ubuntu PPA or snap or flatpak if you must.

---

### Post by gardenair on 2021-01-14
Thanks for the reply. Well, we can say that Ubuntu is the more refine OS than Debian? Or we can say Debian is just for Server-side because it is Rock Solid. If some like to switch from Windows to Linux based OS what should you suggest? Debian or Ubuntu? It is a personal choice because both are stable in my point of view. For new user, I can say to use Ubuntu :). Debian is for experienced users.

---

