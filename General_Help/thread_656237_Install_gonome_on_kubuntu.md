---
title: "Install gonome on kubuntu"
date: 2008-01-02
forum: General Help
---

### Post by IPOD on 2008-01-02
I have  a kubuntu desktop and  I was wondering if I could get gnome on it  is is it possible?:confused:

---

### Post by joselin on 2008-01-02
Don't know it for sure, but think that you can do it by installing ubuntu-desktop package.

sudo apt-get install ubuntu-desktop.

---

### Post by Nunu on 2008-01-02
I installed the KDE desktop on ubuntu using synaptic package manager, makes it really cool so that you can decide which one of the two u want to use.  You just end up with a massive amount of icons in the menus.

---

### Post by IPOD on 2008-01-02
When ever I try to do that it will say E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

And nothing else is using it if I try to kill processes it says I cant what sould I do?

---

### Post by meindian523 on 2008-01-02
You sure you are not using Update Manager/Adept/Synaptic simultaneously with the apt-get?

---

### Post by IPOD on 2008-01-02
It still is not working :( what else should I try?

---

### Post by knutschr on 2008-01-02
Restart your session. Then you should be sure another program using /var/lib/dpkg is not open ehen you paste the command in terminal.

---

### Post by IPOD on 2008-01-02
I ran the command in recovery mode and it worked but it gave me the old version of gnome

---

### Post by knutschr on 2008-01-02
```
sudo apt-get install dist-upgrade
```
may be will fix it?

---

