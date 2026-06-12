---
title: "Cinnamon breaks the system after upgrade to 13.04"
date: 2013-04-26
forum: General Help
---

### Post by Darknote on 2013-04-26
Yup... No login screen after upgrading to 13.04. After logging into the command prompt and removing cinnamon DE the login screen reappears and I can login to Gnome Shell.

Yup, Gnome Shell! Not a Unity fan and I didn't know that I wouldn't gain anything from upgrading to 13.04 if I'm not using Unity until after the upgrade.

Best would be if I could just downgrade back to 12.10 or switch to another OS, but I'm going to stick with Ubuntu for at least three more months before I would consider something like that. In the mean while I need to get my OS to a stable state and hopefully get it to work with Cinnamon.

Is anyone able to point out any helpful tips on how to fix this?

---

### Post by dino99 on 2013-04-26
i'm not using cinnamon; but as its itself a fork of GS, why dont you make the jump ? Gnome-shell is my choice as it closely mimic unity (or vise-versa) and its stable.
Is lightdm the default on your system ? or gdm ?

sudo dpkg-reconfigure lightdm

---

### Post by deadflowr on 2013-04-26
Cinnamon no longer need be installed with a PPA, for what it's worth.
It's in the raring repos.
Last I checked I think it was version 1.7-something.
I'm not a big Cinnamon user, but I installed during raring development and it worked great.

---

### Post by Darknote on 2013-04-26
Hey..., gdm is my default :)
I decided to switch to Cinnamon from Gnome Shell since I thought Gnome Shell was starting to get a bit heavy. As a result my desktop became a little bit more snappy which made me happy. :)

---

### Post by Darknote on 2013-04-26
I removed the PPA from where I installed Cinnamon first and the Cinnamon which comes with Raring also broke my system. :/

---

### Post by deadflowr on 2013-04-26
> **Darknote said:**
> I removed the PPA from where I installed Cinnamon first and the Cinnamon which comes with Raring also broke my system. :/

Did you run ppa-purge?

---

### Post by Frogs Hair on 2013-04-26
Post the results of sudo apt-update in code tags using the # symbol . There may be suggestions to further commands in the output . If the PPA was not fully purged there are probably broken packages. If synaptic is installed that can be helpful for fixing broken packages.

---

### Post by cylgalad on 2013-05-25
This SHOWSTOPPING problem still exists.
The only workaroung I found is to install all the PPA .deb manually, which ends up breaking apt-get, all this for a simple bad useless dependency.
If it was about Microsoft, somebody would already have been FIRED.

If I have known this SHOWSTOPPING issue I would never have upgraded to raring! I can tell that I'm not gonna upgrade to saucy anytime before 2014.

---

### Post by cylgalad on 2013-05-27
I found the source and the solution to my problem: I used the gnome3-team ppa, so I had an updated libgjs0c v1.36 while it's the v1.34 that cinnamon works fine with, so I got rid of the gnome3-team ppa and reinstall the "normal" libgjs0c and cinnamon installs fine!

---

