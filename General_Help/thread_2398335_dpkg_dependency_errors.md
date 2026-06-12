---
title: "dpkg dependency errors"
date: 2018-08-10
forum: General Help
---

### Post by number33ak on 2018-08-10
I came across these errors when I tried to install the last nvidia drivers.

I ran 
```
sudo apt-get install nvidia-current
```

Then I noticed a bunch of dpkg dependency errors, here is a the full log: [https://paste.fedoraproject.org/paste/7lbn2iQ27KKrvuIi72I9DA](https://paste.fedoraproject.org/paste/7lbn2iQ27KKrvuIi72I9DA)

[ATTACH]280696[/ATTACH]

I've tried looking through similar posts but with no success.

Looking for suggestions.

Thanks

---

### Post by TheFu on 2018-08-10
Welcome to the forums.

Remove any manually installed .deb files - using dpkg.
Remove any 3rd party PPAs from /etc/apt/sources.d/
Do and update/upgrade cycle.  That should fix everything.

Generally, the drivers provided from the official repos "Load proprietary drivers" are the ones to be used.  Going outside those can lead to dependency problems.

Manually installing .deb files almost always will lead to dependency issues in 3-6 months. If you stay with the supported repos and only use trusted PPAs from reputable sources, then dependency issues are seldom seen.

BTW, the pastebin was empty.

Flatpaks and Snaps should remove these issues for many stand-alone applications.  Applications that need outside library support or extensions haven't been fully addressed, IMHO. Hopefully, the snap/flatpak team will solve that aspect.

---

### Post by number33ak on 2018-08-10
> **TheFu said:**
> Welcome to the forums.

Remove any manually installed .deb files - using dpkg.
Remove any 3rd party PPAs from /etc/apt/sources.d/
Do and update/upgrade cycle.  That should fix everything.


Thank you.

I'm not sure when this problem began, and can't remember which packages were installed manually.  Is there a way to find out?

Should I have a source.d?  As all I have in /etc/apt is ```
apt.conf.d  preferences.d  sources.list  sources.list.d  sources.list.save  trusted.gpg  trusted.gpg~  trusted.gpg.d
```

Regards.

---

### Post by TheFu on 2018-08-10
My mistake: sources.list.d/  is it.

I don't know how to find manually installed .deb files. Sorry.  apt-mark or dpkg manpages might be helpful.  IDK.  The problem is that apt-mark does know which packages were manually installed using APT, so don't confuse which.

Best to avoid installing .deb packages directly with dpkg or apt or aptitude or apt-get.  Stay with the package manager and PPAs.

---

### Post by mc4man on 2018-08-10
What flavour of 16.04 did you install & what are you running now?
You may not remember "when" this started but certainly you should know what you did to cause hundreds of gnome & unity packages to be marked for autoremove..

---

