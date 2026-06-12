---
title: "Slooow responding minimal gnome!?"
date: 2008-02-04
forum: General Help
---

### Post by .neo on 2008-02-04
I've installed minimal Gnome on my P4 2.4GHz / 1gig RAM machine (installed first Gutsy desktop command line, and then did sudo apt-get of enough packages to have Gnome load ok)... The point until Gnome loads is sufficiently fast but what I can't get worked out are some delays in Gnome that seem to happen somewhat randomly.

For instance, if I click the shutdown button in the right upper angle I'll wait for at least a minute of two until the dialog to shut down/restart Ubuntu appears? Also, similar problems occur when I add things to Sessions. So, for example, even though my desktop became responsive almost immediatelly after autologin (set up via System>Administration>Login Window), the Sessions entries, simple things like startup of Firefox (command line in Sessions is only Firefox call and nothing else!!!) takes minute or two to load!

Anything anyone please!?? ;-(

TIA

---

### Post by danwood76 on 2008-02-04
which packages did you install to get gnome up?
It could be that a package or two is missing and is giving you these issues.

Also have you tried install gutsy from the standard install?

regards,
Danny

---

### Post by .neo on 2008-02-05
I've installed xserver-xorg, gnome-core and gdm (I've also added feisty themes cause it needed theme human). 

I've found the source of the sessions startup delay though.** It's was the nautilus entry in /usr/share/gnome/default.session **!!!

Now I've commented that out (in fact I commented everything out except gnome-wm) the firefox sessions starts up in seconds :-) ... Only thing is there's still a delay to wait for shut down/restart/log out/switch user dialog when you use ctrl-alt-del key combination.

> **danwood76 said:**
> which packages did you install to get gnome up?
It could be that a package or two is missing and is giving you these issues.

Also have you tried install gutsy from the standard install?

regards,
Danny

---

