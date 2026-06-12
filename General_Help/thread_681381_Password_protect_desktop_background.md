---
title: "Password protect desktop background?"
date: 2008-01-28
forum: General Help
---

### Post by insert_name_here on 2008-01-28
Is it possible to require the user to enter a root password to change the desktop background?  I'm kinda sick of my roommates changing my desktop background to something obscene when I leave to use the bathroom, pop popcorn, etc.

---

### Post by seventhc on 2008-01-28
You could just lock your screen when you leave. On the same menu where you shutdown from, just choose lock screen.

---

### Post by insert_name_here on 2008-01-28
I suppose so...

Is there some way to get the screen to lock when I close the lid?  (This is a laptop.)

---

### Post by seventhc on 2008-01-28
I think there is a setting for that, I have to find it though. :D
I'll post back

---

### Post by PinkFloyd102489 on 2008-01-28
[http://ubuntuforums.org/showthread.php?t=563687&highlight=lid](http://ubuntuforums.org/showthread.php?t=563687&highlight=lid)


There's a guide on how to play sounds on open and close, Im use you can tweak it to lock the screen.

---

### Post by lsmobrian on 2008-01-28
I dont know the full repercussion, but if you are happy with your gnome appearance, can you change the permissions on the program that changes background.  

guessing its owned by root and executable by world.  so chmod it to root executable only.  someone please correct me if this would cause breakage.  

(you would have to chmod to make any changes, betting sudo wouldnt work)

---

### Post by seventhc on 2008-01-28
Did the link above work for you? So far I haven't found where I thought it was. I was thinking it could be changed in power management, but they only give options for sleep, suspend, or do nothing.:(
Let me know if the above link worked though if not I'll look around more.

---

### Post by seventhc on 2008-01-29
Well I found something, not exactly what you wanted, but I think this is what I saw. System>Preferences>Screensaver
you can set it to lock when screensaver goes on...I guess you'd have to sett your screensaver to start after 1 minute of idle time. This might be annoying though. But it will lock the screen ;)
Edit:::
try this
in power management set it so your screen suspend or hibernate...w/e then
from terminal open
gconf-editor
then go to
Apps>gnome-power-manager>lock
make sure there is a check mark next to suspend or whatever you chose for your power management choice.
I think if they match then suspend/hibernate/etc will = a lock.
I'm not positive but it's something I would try.

---

### Post by insert_name_here on 2008-01-29
I checked the blank screen key in apps->gnome-power-management->lock, and now when I close my screen, it locks.

Thanks!

---

### Post by seventhc on 2008-01-29
Glad it worked. :)

---

