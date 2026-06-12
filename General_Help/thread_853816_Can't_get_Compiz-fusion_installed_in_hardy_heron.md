---
title: "Can't get Compiz-fusion installed in hardy heron"
date: 2008-07-08
forum: General Help
---

### Post by tehsilverdollar on 2008-07-08
I'm following dierctions for how to install compiz-fusion for Gutsy as I can't find any howto for Hardy...seen here

[Directions]("http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200")

Everything goes fine until i need to find gnome-compiz-manager.  It doesn't seem to exist in Hardy.  

Everything else seems to work fine, I am working on an IBM T61p with nVidia graphics card.  The proprietary drivers seemed to go okay, and all the other packages it told me to find were there.  The only thing that doesn't show up is the "custom" option under "visual effects"

Anybody who has this working, or has any ideas, let me know.

Thanks in advance

---

### Post by stats on 2008-07-09
i think you are looking for compiz-config-settings-manager

---

### Post by sayakb on 2008-07-09
Hardy Heron should already have compiz fusion installed.
To get the latest compiz working, at a terminal:
```
sudo apt-get install compizconfig-settings-manager
```And then follow this: [http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml) to upgrade to the latest compiz fusion.

To launch the compizconfig-settings-manager, goto System->Preferences->Advanced Desktop Effects Settings

---

