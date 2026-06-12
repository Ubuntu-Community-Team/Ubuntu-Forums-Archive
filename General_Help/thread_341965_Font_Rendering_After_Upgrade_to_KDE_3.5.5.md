---
title: "Font Rendering After Upgrade to KDE 3.5.5"
date: 2007-01-19
forum: General Help
---

### Post by true_friend on 2007-01-19
HI
i am facing a strange problem. i have upgraded my kde 3.5.2 to kde 3.5.5 through synaptic. after upgrade i am facing font rendering problems in my default user account. but it is ok in root account( upgrade was made using root GUI account). plz see these images for detail both are of konqueror one is of root account and other is default account (ss). root account snapshot is taken by running Konqi in 'kdesu' mode. 
I think there is some configuration problem not whole system is gone wrong. plz suggest me solution.
Regards
True_Friend
Root Pic
[[IMG]http://img403.imageshack.us/img403/8859/rootlz2.th.png[/IMG]](http://img403.imageshack.us/my.php?image=rootlz2.png)
User Pic
[[IMG]http://img294.imageshack.us/img294/1949/usermw0.th.png[/IMG]](http://img294.imageshack.us/my.php?image=usermw0.png)

---

### Post by ahaslam on 2007-01-19
Add **forceFontDPI=96** to **~/.kde/config/kcmfonts**

Tony ;)

---

### Post by true_friend on 2007-01-19
i report after restart
thnx for answer

---

