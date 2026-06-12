---
title: "log off does nothing"
date: 2005-10-28
forum: General Help
---

### Post by stoeptegel on 2005-10-28
I was gaming with quake4 when all of sudding the whole system hanged. AFAIK i could only could use the reboot button at this time, so i did.  
After reboot, the kdm didn't showed up, so i $ startx, which asked me to remove /tmp/.X0-lock.

So now i am in gnome, but i want to log off and get in kde, but it doens't work. There is a sound when i press 'log off', but nothing happens.

What to do?

---

### Post by stoeptegel on 2005-10-28
Nevermind, it's gone working again after i started konsole.

---

### Post by mykey on 2005-10-28
try these two:
[B]sudo rm -rdf /tmp/*
sudo reboot[/B]
and let us know what happens

Oh - o.k. it's fixed .. good - sometimes it just helps to clean out the garbage from older sessions

---

### Post by stoeptegel on 2005-10-28
Thanks i'll keep that in mind for next time.  \o/

---

