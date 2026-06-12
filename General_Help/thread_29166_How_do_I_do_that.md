---
title: "How do I do that?"
date: 2005-04-23
forum: General Help
---

### Post by Nob on 2005-04-23
how to save curent sound configuration as the default configuration in XFCE?
everytime i restart computer, Master volume is 0%, and PCM is 0% too..
how do i set Master to 100% and PCM on 60% to be default settings on bootup?

---

### Post by nad on 2005-04-23
Please see:

[http://alsa.opensrc.org/index.php?page=FAQ021](http://alsa.opensrc.org/index.php?page=FAQ021)

Dan M

---

### Post by Nob on 2005-04-23
fixed, 10x for the link, but there isnt anything useful, i did it myself ;)

set your sound volumes, then type:
# alsactl -f /var/lib/alsa/asound.state store
# echo alsactl -f /var/lib/alsa/asound.state restore > /etc/init.d/sound_restore
# chmod a+x /etc/init.d/sound_restore
# ln -s /etc/init.d/sound_restore /etc/rc2.d/S59sound_restore
# ln -s /etc/init.d/sound_restore /etc/rcS.d/S59sound_restore
# reboot

and voila! :)

---

