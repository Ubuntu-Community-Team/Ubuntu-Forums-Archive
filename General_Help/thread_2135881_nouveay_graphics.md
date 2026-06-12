---
title: "nouveay graphics"
date: 2013-04-15
forum: General Help
---

### Post by paulie-m on 2013-04-15
please help me.i have been using lubuntu for about 2 years now. i have 12.10.i make heavy use of project m music vizualization.todfay i did a system update from the software update program and i noticed it installed new nouveau drivers(which i have always used.-i have an nvidia graphics card but project m will not work with propietry drivers).after this update project m has stopped working!!whenever i run project m my system crashes and during shutdown i get a message saying gpu crashed.how do i fix or reverse this update?please help.watching project m while listening to music is my life!thanks in advance.paul.

---

### Post by humpty88 on 2013-04-19
You could try downgrading (if it lets you)
synaptic > search > nouveau

click on xserver-xorg-video-nouveau > Package > force-version

---

### Post by paulie-m on 2013-04-21
did what you suggested but force version is greyed out and hence am unable to select it.any ideas why.thanks.paul

---

### Post by humpty88 on 2013-05-17
It's greyed out cos it can't find an older version.
You'll have to search around for a repository that has an older version and add that repository to synaptic.

Failing that, a sure-fire way is to re-install from your original .iso being careful not to install updates during install.

---

