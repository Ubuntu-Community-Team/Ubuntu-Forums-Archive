---
title: "Graphical login manager"
date: 2008-01-27
forum: General Help
---

### Post by fb2007 on 2008-01-27
I installed kdm on ubuntu (7.10) and after install I choose it to be default login manager. After a while I uninstalled kdm, but now I can't get gdm to work! I am only able to login in console mode. With startx I am able to get into graphical environment (gnome) working. 

I also can't shutdown my computer from graphical environment (only suspend, hibernate, log off, lock screen and switch user are available). 


Does anybody know how to fix this


thanks in advance
fb2007

---

### Post by jeffus_il on 2008-01-27
Reinstall gdm, it should set itself up as the default display manager. You can also run gdm from the console ```
sudo /etc/init.d/gdm start
```

---

### Post by fb2007 on 2008-02-03
I reinstalled gdm and it starts if I sudo gdm, but native login is still in console mode. On log on it prints an error (something about that it can't set resolution 1200x1024).

Any ideas how to fix that?


thanks

---

### Post by zvacet on 2008-02-03
[Here](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by Victormd on 2008-03-13
Only posting here because of the Graphical Login Manager topic...
I set up my ubuntu to auto-login. However, the Graphical Login Manager (gmd) service is still running. I was going to deactivate it when I received the following message:
"Are you sure you want to deactivate gdm? this may affect your system behavior in several ways, possibly leading to data loss."
To me this was a red flag so I thought I'd check disabling it.
Do I need the service to be enabled to automatically login to X?
If not, what kind of data loss could happen?

---

