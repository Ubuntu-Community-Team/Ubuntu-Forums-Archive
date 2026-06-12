---
title: "[SOLVED] Windows open behind panel"
date: 2008-06-08
forum: General Help
---

### Post by Raistlin82 on 2008-06-08
Hi all, sorry if this has been asked elsewhere, i have looked but didn't see it!!  I've been having a play with compiz and applying various effects to much satisfaction :-)  However now when i open a window the top frame of the window is behind the top panel.  I know I can move the windows using Alt and click but its an annoyance!  Any suggestions gratefully received!! :)

---

### Post by Forlong on 2008-06-08
If you haven't already, install ccsm ```
sudo apt-get install compizconfig-settings-manager
```

Afterwards, run ccsm and make sure the **Place Windows** plugin is enabled.
Then click on it and if the **Placement Mode** is already set to **Smart**, try **Centered** as a workaround.

---

### Post by Raistlin82 on 2008-06-08
Thanks will try that now and let you know how i get on!

Had installed compiz config, all I had to do was apply the Place Windows plugin!  Have a bad case of noobitus!

---

### Post by nortexoid on 2009-03-24
> **Forlong said:**
> If you haven't already, install ccsm ```
sudo apt-get install compizconfig-settings-manager
```

Afterwards, run ccsm and make sure the **Place Windows** plugin is enabled.
Then click on it and if the **Placement Mode** is already set to **Smart**, try **Centered** as a workaround.

Thanks. I had the same problem and it worked (on Smart). I had disabled a bunch of things, including Place Windows, not thinking they were useful.

---

