---
title: "Best place to install 3rd party software?"
date: 2004-12-13
forum: General Help
---

### Post by Dark Ocean on 2004-12-13
So i've you're the only user on the system and you're planning to install some 3rd party software like Azureus, what is the best place to put it? Is that /usr/locale/bin or /home/username/apps or whatever?

---

### Post by randy on 2004-12-13
Usually the default for software that is built from source is /usr/local

---

### Post by adbak on 2004-12-13
Or you can opt for /opt, which was created specifically for this reason.  I think the one advantage this has is that there are no other files in /opt unless you put them there, so if you go to delete files you won't be getting rid of any necessary or pertinent files.  But then again, that's if you don't know what you're doing.  ;)

---

