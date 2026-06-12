---
title: "Completely removing LibreOffice"
date: 2020-07-23
forum: General Help
---

### Post by welshmike on 2020-07-23
I'm having problems with LibreOffice Writer so I'd like to completely remove LibreOffice then install a new version
Please advise.

---

### Post by dragonfly41 on 2020-07-23
I would use Synaptic Package Manager .. search libreoffice-writer .. right click .. choose options.

---

### Post by TheFu on 2020-07-23
To remove all libreoffice stuff
```
sudo apt-get remove --purge libreoffice-*
```

That assumes APT was involved.
If snaps are involved, use **snap remove**.

---

### Post by deadflowr on 2020-07-23
Probably also good to move/remove/delete the user settings at ~/.config/libreoffice.

---

### Post by TheFu on 2020-07-23
> **deadflowr said:**
> Probably also good to move/remove/delete the user settings at ~/.config/libreoffice.

Excellent point.  It is unlikely that reinstalling will change anything.  To see if the issue is with the current userid's settings, I'd create a new userid, login using that and see if the issue remains. If not, it is personal settings and you can research from that perspective.

If the package installed is a snap, being aware that snap packages have constraints would be important.  What exactly are the "problems"?  Anything like not being able to access files outside the userid's HOME directory?  That is indicative of snap problems.  Remove the snap version, install the APT version, be happy.

---

