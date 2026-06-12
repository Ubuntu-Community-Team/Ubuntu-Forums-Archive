---
title: "KDE desktop"
date: 2008-03-26
forum: General Help
---

### Post by balagunner on 2008-03-26
I don't have kubuntu 7.10 and I have GNOME desktop now. Can I change my desktop to KDE?

Will Compiz work then?

---

### Post by thedarkwinter on 2008-03-26
"sudo apt-get install kubuntu-desktop" in a terminal
will install KDE, but not uninstall gnome

At the login screen you can choose which one you want to use. I'm not sure whether compiz works properly in KDE or not, but it hasn't been streamlined into KDE - so it takes more work to get it working.

---

### Post by tubasoldier on 2008-03-26
Yes. Very easily.

```
sudo apt-get install kdebase kde-core
```
Then you can select it from the "Sessions" menu on the login screen (gdm)

As far as compiz working... 
That depends on your hardware. I've gotten it to work with my Nvidia card but still have issues getting it to work with my ati card.

---

