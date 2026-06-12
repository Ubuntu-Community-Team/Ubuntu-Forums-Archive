---
title: "stop sound mute on shutdown"
date: 2006-08-29
forum: General Help
---

### Post by rally25rs on 2006-08-29
I've noticed that when Ubuntu shuts down, the sound level is muted.  The sound level is restored when Ubuntu is started back up.

This has been a problem for me because I am running it in VMWare, so every time I shutdown Ubunto, it mutes my host OS (XP Pro) and I have to go into the windows volume controller and unmute the master volume.

Is there a way to stop the mute from happening?

---

### Post by Rui Pais on 2006-08-29
Hi,
you can try to install something like sysv-rc-conf (from universe repository) and use it to remove any reference to alsa-utils from service level 0 

or 

remove manually any /etc/rc0.d/KXXalsa-utils (where XX are a number from 01 to 99).

---

### Post by rally25rs on 2006-08-29
removed the alsa-utils stuff from runlevels 0 and 6, and that did the trick.
thanks for the assist!

---

### Post by Rui Pais on 2006-08-29
runlevel 6 had alsa-utils simlinks too?... sorry i removed any reference to alsa-utils from all levels i couldn't now know.

Glad its solved.

---

