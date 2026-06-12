---
title: "&quot;Failed to initialize HAL&quot; error"
date: 2007-01-17
forum: General Help
---

### Post by ArgentSilver on 2007-01-17
My laptop with Edgy suddenly started to come up into Gnome with a "Failed to initialize HAL" error on every boot, and USB items wouldn't be recognised. I searched here and found a recent thread [http://www.ubuntuforums.org/showthread.php?t=331824](http://www.ubuntuforums.org/showthread.php?t=331824) and tried the fix suggested; namely:
sudo update-rc.d -f dbus remove
sudo update-rc.d dbus defaults 12

That seems to have worked so I'm good to go, but this is an old fix pre-Dapper! Why is this still an issue? I'm not clear what the fix does...take out dbus from the startup and then reinsert it with an earlier start? And how does that fall in with Upstart? :confused:

---

### Post by fabbaz on 2007-01-25
i just had the same problem. attached is a screenshot.
additionally on my panel where the mounted devices should be shown, if any are mounted (cd, dvd, usbstick...) are two placeholders for my dvd drives.

---

### Post by ArgentSilver on 2007-01-26
Well, obviously <sarcasm> based on all the community answers here, there is great interest in this problem </sarcasm>...

Good luck finding a solution!

---

### Post by fsando on 2007-01-28
Hi - I just experienced the same problem  (again) - sigh!!
I believe you didn't get an answer because it has been answered so many times before.
I've had this problem before and quickly found the answer the other times - am going to look for it now.
Not really helping - but perhaps an explanation.

---

