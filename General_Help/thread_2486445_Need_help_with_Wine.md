---
title: "Need help with Wine"
date: 2023-04-30
forum: General Help
---

### Post by jonfisher on 2023-04-30
I have Wine on my Desktop and Laptop - both running Ubuntu 22.x LTS

On the desktop, I can right click and choose to launch an .exe file.  On the laptop, I have to use terminal & the 2 Wine installations from Ubuntu Soft. Ctr  installs a version where I have to use terminal to launch .exe programs with Wine - Wine doesn't show up if I scan to try to locate it in applications either (when asked what app. to try to launch it).

Not a major problem, but was was wondering what I'd need to do to get the convenience of right clicking an .exe file to launch it with Wine again.

---

### Post by monkeybrain20122 on 2023-04-30
The wine.desktop file is for some reasons hidden in the wrong directory. Just copy or link it to where it can be found by the file manager.

 e.g

```
sudo ln -s /usr/share/doc/wine/examples/wine.desktop /usr/share/applications
```

If you right click your .exe file and go to  properties > open with, you should be able to see an entry called "wine windows program loader". You can then make it your default (if you don't find it, you may need to logout and log back in)

---

### Post by jonfisher on 2023-04-30
Thanks!
Marking this as solved.

---

