---
title: "sendmail causes delay at boot time"
date: 2008-03-17
forum: General Help
---

### Post by DavidS on 2008-03-17
Using Gutsy with gdm, sound was working fine until recently.  Now it doesn't, so as advised on
[http://ubuntuforums.org/showthread.php?t=205449&highlight=gconfaudiosink](http://ubuntuforums.org/showthread.php?t=205449&highlight=gconfaudiosink)
I did
apt-get --purge remove linux-sound-base alsa-base alsa-utils
then reinstalled gdm, unbuntu-desktop and the above packages.

Now sound still doesn't work, but as result of what I did a few other problems have arisen.  Notably, that when I boot, sendmail causes the boot process to delay for one minute before reporting "OK" and carrying on.

How can I cure this?

---

