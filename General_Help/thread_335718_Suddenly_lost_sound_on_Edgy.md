---
title: "Suddenly lost sound on Edgy"
date: 2007-01-10
forum: General Help
---

### Post by goneskiing on 2007-01-10
Ouch, Edgy is proving to be a bug filled upgrade.

Now I just lost all my sound - including the login drum sounds.   Other posts indicate it could be from Samba shares (I haven't implemented Samba) or from auto login (I have that disabled).  Running on Lenovo 3000.   Any ideas ?

---

### Post by K.Mandla on 2007-01-10
This is the only time I can think of where someone spontaneously lost sound. 

[http://ubuntuforums.org/showthread.php?t=314700](http://ubuntuforums.org/showthread.php?t=314700)

I don't know if there's an answer in there for you, but it never hurts to look.

---

### Post by goneskiing on 2007-01-11
Yea, the only thing I can think of is I added a bunch of the gstreamer stuff, including bad and ugly - maybe ugly is really ugly.  I'll try to delete alsa and reinstall it.

---

### Post by goneskiing on 2007-01-11
okay, I deleted alsa-base which also deletes ubuntu-minimal.  Then restarted.  Then reinstalled.  Then restarted.  All is well again.  Go figure.  But maybe it helps someone else.

---

