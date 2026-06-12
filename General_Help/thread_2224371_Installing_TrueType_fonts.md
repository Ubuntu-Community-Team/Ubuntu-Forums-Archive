---
title: "Installing TrueType fonts"
date: 2014-05-16
forum: General Help
---

### Post by OccasionallyY on 2014-05-16
I think I made a big mistake installing ubuntu-restricted-extras from the software center and am now paying dearly for it. It installed without prompting me to accept the EULA and I do not have access to the TrueType fonts as a result. I've tried to uninstall, remove and purge ubuntu-restricted extras from terminal and reinstalling (via terminal this time) but it has not fixed the problem at all. What do I do? These default Ubuntu fonts are god awful. Makes browsing online very nauseating.

---

### Post by OccasionallyY on 2014-05-16
I found out what happened. I *highly* suggest that the Ubuntu Documentation no longer suggest to install from the Software Center. During installation, Software Center completely froze and my only guess is because of the EULA pop up (which never actually popped up on my end..). What I had to do was:

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install --reinstall ttf-mscorefonts-installer[/FONT][/COLOR]
```

After this, the TrueType fonts were available to me.

---

