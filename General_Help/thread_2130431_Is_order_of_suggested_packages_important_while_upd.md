---
title: "Is order of suggested packages important while updating ubuntu?"
date: 2013-03-29
forum: General Help
---

### Post by arroy_0209 on 2013-03-29
I am using ubutnu12.04 and I rely on update manager for updating my ubuntu. My doubt is, is there any significance of the order in which the packages are recommened in the update manager window? Is there any problem if I select a few of the packages for updating at a time (rather than doing the enrire updatation which is often huge and I may face problem due to poor connectivity issues, like connection getting timed out etc)? Here am I allowed to alter the sequence of packages suggested for updatation if I am updating selectively?

(e.g., suppose there are three updates in this order: xserver-common, xserver-xorg-core, xserver-xorg-video-nouveau. Can I update nos 1 and 3 this time and do no 2 later?)

Second, I always do the "important security updates" but there are some packages in "recommended updates" section which I never use and I sometimes do not go for those updates at all. Will there be any problem in future because of this?

---

### Post by grahammechanical on 2013-03-29
We have Update Manager to manage the updates for us. Update Manager will automatically include all the needed packages (called depends - because packages depend on other packages). That is its purpose. It will often fail to update or install certain packages if those packages have unmet dependencies.

If xserver-xorg-video-nouveau is needed by either xserver-common or xserver-xorg-core or by both, then you will not be able to update those two packages without the third one. This is done to protect us from ourselves. So, that we do not break the operating system.

We still have choices. We do not need to accept the updates if we do not want to download them. This applies even with "important security updates." We can even set Update Manager to never notify us of updates.

Ubuntu 13.04 has a modified Update Manager which gives a description of each update in words that ordinary users will understand. At least, I find the language used more understandable. We also get a tick box so we can un-check an update so that it does not download. 

Regards.

---

### Post by Jay_E on 2013-03-29
Hi there,
If you are interested,
try
[http://debian-handbook.info/browse/stable/](http://debian-handbook.info/browse/stable/)

[edit: might need to adjust for conforming version of ubuntu...]

The section on packaging is revealing.
It talked about a function that dealt with strict order of installation - but said developers should try to avoid using it.

have fun
Jay

---

### Post by tgalati4 on 2013-03-29
Normally you should be OK.  But once and a while, the order is important--especially if a configuration script breaks because a missing library or older framework is still installed on the system.  This would be a packaging error--a missing dependency.  It's rare, but it does happen.  Sometimes a reboot is necessary for a configuration script to finish and if one package fails to install properly, then other packages can fail as well.

Someone posted a picture on the web of the interrelationship of Debian packages and it looked like a fireworks display finale.  It's a miracle that any of this stuff works at all.

---

