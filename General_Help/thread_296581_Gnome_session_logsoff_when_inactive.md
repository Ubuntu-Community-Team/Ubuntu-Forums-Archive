---
title: "Gnome session logsoff when inactive"
date: 2006-11-09
forum: General Help
---

### Post by weyh on 2006-11-09
When I login to my gnome desktop if I don't start doing something right away or walk away from my computer for a few minutes it's gone back to the logon screen.  Is there some setting I'm missing?

I am using the KDM logon manager.  I installed it from Kubuntu 5.10 release and have done the updates to dapper then edgy.

I'm gonna start a new thread on this but what do I change to use GDM instead.

Thanks
Darwin

---

### Post by jpeddicord on 2006-11-09
Try typing the following into a terminal, and it should ask you if you want to set the manager to GDM.
```
sudo dpkg-reconfigure gdm
```

---

