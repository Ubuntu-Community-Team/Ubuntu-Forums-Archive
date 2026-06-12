---
title: "k3b permissions issue"
date: 2006-10-29
forum: General Help
---

### Post by oliwally on 2006-10-29
```
Cdrecord has no permission to open the device.
You may use k3bsetup2 to solve this problem.
```

This is the error I receive when trying to burn in k3b as a user on my Dell d820. However it all works fine when I run k3b as root (kdesu k3b). And, it works well as a user on my desktop. Just no success with the laptop.

I have already changed permissions on the dev/scd0 and dev/sg1, but without any luck. I've shuffled thorough supposed help all over the net, but to no avail so far. 

Please help.

---

### Post by james016 on 2006-11-16
I got this problem last night in and had to do the same thing. Just changed the shortcut to have gksudo in the path.

---

### Post by Marsolin on 2006-11-16
Another option is to reinstall [CDRecord]("http://linuxappfinder.com/package/cdrecord") and tell it to install as set UID (I don't remember the exact phrasing) when prompted. That worked for me.

---

