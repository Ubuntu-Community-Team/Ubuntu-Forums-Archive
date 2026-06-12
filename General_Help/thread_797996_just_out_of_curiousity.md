---
title: "just out of curiousity"
date: 2008-05-17
forum: General Help
---

### Post by djmoore85 on 2008-05-17
Hey yall, had a quick question out of curiousity. I installed Xfce and KDE desktops, just to try them out and settled on GNOME for my environment. How do I remove all the apps that came along with those two desktop environments even after I used the purge option in apt-get, yet still have several KDE and Xfce apps leftover. Any help is appreciated.

---

### Post by mardawi on 2008-05-17
I think you have to remove them one-by-one. Wait for more experienced users to comment before you do anything

---

### Post by Victormd on 2008-05-17
If you've already removed them, you can try
```
sudo apt-get autoremove
```

---

### Post by p_quarles on 2008-05-17
You can also look for a package upon which everything else depends. For instance, uninstalling "ktip" will help you get rid of most KDE-related thigs.

---

### Post by Sef on 2008-05-17
How did you install them?  Via Synaptic or the command line?

---

### Post by aysiu on 2008-05-17
You could also remove them by following this tutorial:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by djmoore85 on 2008-05-18
Thnks yall for the help. I installed them via synaptic, I went to the psychocats tutorial and that seems to have cleared everything out. Thanks again, I'll be more attentive in the future when I install things to try out

---

