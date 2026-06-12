---
title: "Problem with latest update to Audacious plugins"
date: 2008-02-16
forum: General Help
---

### Post by RgnKjnVA on 2008-02-16
I use Audacious as my go-to music player and was psyched to see an update yesterday in Update Manager. The install of the plugins fails though with the following error. I've tried installing audacious_plugins separately from audacious_plugins_extra but they seem to be conjoined packages (so why aren't they just consolidated into ONE package eh?).  Anyone know a fix or work-around for this? Removing the existing pulse_audio.so does not solve the issue.

E: /var/cache/apt/archives/audacious-plugins_1.4.4-1ubuntu1~gutsy1_i386.deb: trying to overwrite `/usr/lib/audacious/Output/pulse_audio.so', which is also in package audacious-plugins-extra

---

### Post by luke16 on 2008-02-23
EDIT: Try this:
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/audacious-plugins_1.4.4-1ubuntu1~gutsy1_i386.deb
sudo apt-get install -f
sudo apt-get dist-upgrade
```

---

### Post by RgnKjnVA on 2008-02-24
ah thx Luke.  I wound up just deselecting the extra-plugins in Synaptic and reinstalling them one at a time. I thought Synaptic was supposed to reconcile this sort of thing?

---

### Post by acl123 on 2008-03-25
I'm getting this error again with the next update - does anyone know why this happens?

---

### Post by RgnKjnVA on 2008-03-25
me too. The error this time is...
E: Couldn't configure pre-depend audacious-plugins for audacious-plugins-extra, probably a dependency cycle.

I've posted on the Audacious forum but no response yet. Not sure if it's the repo or the way the code is packaged up. I'm sure the 'nice' dev guys at Audacious will let me know if it's not their issue.
[http://boards.nenolod.net/viewtopic.php?f=5&t=975&start=15](http://boards.nenolod.net/viewtopic.php?f=5&t=975&start=15)

---

### Post by elamericano on 2008-03-29
Lucky you. Audacious gives: Segmentation fault (core dumped) when audacious-crossfade is installed. 

It's out for now. plugins-extras is OK though.

---

### Post by pbardet on 2008-04-26
> **RgnKjnVA said:**
> The error this time is...
E: Couldn't configure pre-depend audacious-plugins for audacious-plugins-extra, probably a dependency cycle.

I got hit by this error message during upgrade to 8.04. I'm glad I was able to finish that upgrade by removing audacious from my system. Not the greatest feeling to see the failure in the morning.

---

