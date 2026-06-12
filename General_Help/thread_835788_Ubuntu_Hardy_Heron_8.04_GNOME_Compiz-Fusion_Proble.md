---
title: "Ubuntu Hardy Heron 8.04 GNOME Compiz-Fusion Problem"
date: 2008-06-20
forum: General Help
---

### Post by Googool on 2008-06-20
Hello,

I have been using Gutsy Gibbon 7.10 for a while but decided to clean off the system and make a fresh install of Hardy Heron.  I had compiz-fusion working on 7.10 previously, but I can't find a way to install it into 8.04 now.  

1.  All the guides I've looked for repeat downloading "compiz compizconfig-settings-manager" but as far as I have tried to do so according to the instructions, this no longer exists (though I remember using it on 7.10).

2.  Is there any guide for downloading it which is up to date, or specialized for Hardy Heron?  I can't find any clear guides to installing compiz-fusion which work.

Thanks for the time.

---

### Post by sapient2003 on 2008-06-20
> **Googool said:**
> Hello,

I have been using Gutsy Gibbon 7.10 for a while but decided to clean off the system and make a fresh install of Hardy Heron.  I had compiz-fusion working on 7.10 previously, but I can't find a way to install it into 8.04 now.  

1.  All the guides I've looked for repeat downloading "compiz compizconfig-settings-manager" but as far as I have tried to do so according to the instructions, this no longer exists (though I remember using it on 7.10).

2.  Is there any guide for downloading it which is up to date, or specialized for Hardy Heron?  I can't find any clear guides to installing compiz-fusion which work.

Thanks for the time.


Compiz :

By default 8.04 will detect your video hardware and will choose the best available driver for it. There are open source drivers for these video cards which do not enable the the majority of the Windows-based drivers can do. You will have better luck using The Restricted Hardware utility/Hardware Drivers. Once you download the proprietary driver and install it without error, reboot. Compiz will then be usable.

---

### Post by bromix on 2008-06-20
You are searching for the wrong package  try this:

> sudo apt-get install compizconfig-settings manager

It seems that you had compiz in there one time too many.  This should put ccsm back in your system-->Preferences menu.

---

### Post by bromix on 2008-06-20
And of course, providing you have the proper video drivers enabled, you can enable compiz-fusion, already native, by right clicking the desktop and choosing the Change Desktop Background, then select the Visual Effects tab.

---

