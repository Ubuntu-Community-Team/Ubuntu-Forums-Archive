---
title: "nVidia keeps killing my Ubuntu Server"
date: 2008-06-28
forum: General Help
---

### Post by Hopworks on 2008-06-28
If I may, I LOVE Ubuntu Gutsy (SERVER) and all the other flavors too, but hey! EVERY SINGLE TIME I update and get a nVidia update, I'm reduced to an awful resolution and other issues.

AND SURE ENOUGH, I updated like a good little Linux user, and sure enough there is an nVidia update, and sure enough, my monitor settings and resolution in my gnome desktop is hosed again.

WHY! "Why does it have to be like this?" quoting from Deadliest Catch on discovery.

Seriously... I'm getting really tired of this. And what ever I had tried on the xorg.conf file is ineffective. HELP! My desktop is hosed. I had it set just right before!

ALSO, this is the exact reason I didn't do hardy. Now I'm reduced to not seeing my 2208WFP dell monitor and maybe that hardy update filtered down to gutsy. Do I HAVE to reinstall with the gutsy image i got before this update? I HOPE NOT!

Thanks for your time!

Hop

---

### Post by sdennie on 2008-06-28
How have you installed the nvidia driver?  If you installed by downloading directly from the nvidia site, this is normal behavior that can be fixed by using this guide: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

Edit:
This won't fix the problem actually, it will just prevent it from happening in the future.

---

### Post by Hopworks on 2008-06-29
> **vor said:**
> How have you installed the nvidia driver?  If you installed by downloading directly from the nvidia site, this is normal behavior that can be fixed by using this guide: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

Edit:
This won't fix the problem actually, it will just prevent it from happening in the future.

It was a standard update via the gnome desktop. I guess it's the same as apt-get update  and apt-get upgrade.

---

### Post by cariboo on 2008-06-29
If things are working good, why update your driver?

To stop your nvidia driver from updating after you get it setup the way you want just lock the driver so it doesn't update. To do this go to System-->Administration-->Synpatic Package Manager-->Package-->Lock Version. this will lock the current version of the package and won't update.

BTW using a gui on a server wastes ram and cpu cycles, use something like webmin to administer your server. Then you can just stick it in a corner and run it headless.

---

