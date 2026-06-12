---
title: "DPMS Screen blanking sends me straight to LightDM."
date: 2014-03-07
forum: General Help
---

### Post by anubeon on 2014-03-07
Greetings all,

Of late whenever my laptop's display is blanked, be it by myself manually (via xset dpms force off/standby/suspend) or as a consequence of the automatic display off settings, the display flickers on and off several times (mode changes?), the nvidia splashscreen appears momentarily and then I'm dropped back into the LightDM login/switch user screen. Its clear that I am not logged out, but it's also clear that the screen isn't be locked (as AFAIK in Ubuntu 12.10 gnome-screensaver is still the locker of choice) and I've not set this machine to automatically log-out, lock the session or switch user.

This is rather frustrating as I typically use the 'display off' setting and/or various xset shortcuts to blank my laptop's display overnight. Only now I have to contend with a rather bright LightDM login screen blaring out at me overnight. The best work-around I've found thus far is to install xbacklight and reduce the display's brightness as low as possible (which sadly isn't 0%).

Does anyone have a clue how to diagnose and/or rectify this issue? As a novice, I'm at a loss.

I'm running…
Ubuntu 'Saucy' 12.10 x86-64
nVidia-319-updates on a GeForce® 8400M GT GPU (although I had nVidia-331 installed until yesterday afternoon; rolling back to 319-updates didn't remedy the above issue)
The Latest elementaryOS daily builds for Saucy (possible culprit?)

---

### Post by anubeon on 2014-04-06
[COLOR=#ff0000][SIZE=5][B][NOT SOLVED] 
[/B][/SIZE][/COLOR]
This issue appears to have solved itself with a recent update. I've rebooted twice now and during each session I've been able to blank the screen without the aforementioned issues. Unfortunately, it appears that Caffeine no longer circumvents the automatic display blanking settings the way it is supposed to. A shame, but a separate issue that I'll probably pursue via a bug report on launchpad.

---

### Post by anubeon on 2014-05-01
I just yesterday upgraded to Ubuntu 'Trusty' 14.04 and this blasted issue is back. I have no idea what solved this issue briefly under 'Saucy'. It was certainly nothing I did, so probably an update. All of which begs the question, why did this issue return with 'Trusty'?

I really, REALLY would appreciate some advice on this one. It's annoying as hell! :-(

---

### Post by grumblebum2 on 2014-06-02
Test in guest account or create and test in new user account.

---

### Post by anubeon on 2014-06-19
Greetings (Again) grumblebum2,

As it happens I have created a fresh user account for the purposes of testing, in fact I'm in the process of transitioning over to it as it would seem that a fresh user account is the cure for many of the things that ail my machine. Alas, this is not one such ailment. Even under a fresh account the same issue as detailed above occurs. 

Regards,

Lee.

---

### Post by bodo bootlin on 2014-09-08
I see the same thing on two different desktops now having upgraded to Trusty Tahr. I am using proprietary Nvidia drivers on both PCs. I could not find help in the forums so I live with it for the moment, just as you do. :(  At least you know now you are not alone...

---

### Post by bodo bootlin on 2014-11-16
For me finally doing this [HTML]http://ubuntuforums.org/showthread.php?t=2251377&highlight=[/HTML] (my post from November 16, 2014) worked. Fingers crossed...

---

