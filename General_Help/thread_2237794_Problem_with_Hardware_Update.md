---
title: "Problem with Hardware Update"
date: 2014-08-04
forum: General Help
---

### Post by mikeebean on 2014-08-04
Software Update informed me of a hardware update, which I installed. On reboot, my computer is now sluggish, my GNOME 3 desktop looks like GNOME 2 (and Unity has lost all tweaks), my NVIDIA settings are gone, and the NVIDIA manager has no real options. I reinstalled GNOME Shell, but it didn't fix anything.

Can anyone suggest how to recover my system without reinstalling Ubuntu? Thanks.

Michael

I'm using Ubuntu 12.04 with GNOME 3 Desktop

---

### Post by 3rdalbum on 2014-08-04
Sounds like your graphics driver is not installed. You'll have to go into the Additional Drivers program and install/enable it.

If you manually installed the Nvidia driver from the Nvidia website, you need to reinstall it whenever the X server gets updated.

---

### Post by mikeebean on 2014-08-05
> **3rdalbum said:**
> Sounds like your graphics driver is not installed. You'll have to go into the Additional Drivers program and install/enable it.

If you manually installed the Nvidia driver from the Nvidia website, you need to reinstall it whenever the X server gets updated.

Additional Drivers wouldn't open, so I installed the NVIDIA driver from their website, and my computer became unbootable. 

Further reading suggested that installing from the Nvidia website isn't recommended, and several threads had various suggestions on how to fix the problem. I picked the most promising solution, but unfortunately those instructions stopped working about halfway through. I couldn't warrant the research and experimentation to get my system back, so I upgraded to 14.04 Ubuntu Gnome. Problem (sort of) solved! 

Thanks for your advice, Additional Drivers would have been the best solution if my system had cooperated, but it was time for an upgrade anyways.

Michael

---

### Post by Jessie_James_A._At on 2014-08-05
open terminal;

```
sudo apt-get purge nvidia*; sudo apt-get install nvidia-331-updates-dev
```


Restart your computer. Go to Software & Updates -> Additional drivers and switch to recommended open-source driver

---

### Post by mikeebean on 2014-08-08
> **Jessie_James_A._At said:**
> open terminal;

```
sudo apt-get purge nvidia*; sudo apt-get install nvidia-331-updates-dev
```


Restart your computer. Go to Software & Updates -> Additional drivers and switch to recommended open-source driver

Hi Jessie_James_A._At, this would have probably been the best solution, unfortunately the solution I found and tried was much more complicated and left my system unbootable. 

Rather than trying to sort it all out, I decided to upgrade to 14.04; it was time. Thanks for your advice though!

Michael

---

### Post by Jessie_James_A._At on 2014-08-09
it been solve mate?

---

