---
title: "Can't find kicker or K menu to upgrade from Ubuntu 5.10 to 6.02"
date: 2006-10-19
forum: General Help
---

### Post by HalF on 2006-10-19
I loaded Ubuntu 5.10 today from CD because I could not load 6.06 from DVD because my system does not recognize the DVD as a bootable device.

Now I want to upgrade from 5.10 to 6.06.  The "...Official Ubuntu Book" says to use the K menu, associated with kicker. which can be found on the bottom bar.  I have looked all over the screen and menus, top, bottom, right-clicking everything, and cannot find anything resembling kicker or the K menu.

Where might I find either one.](*,)

---

### Post by HalF on 2006-10-19
Addundum:  The Official Ubuntu Book is written for 6.06, so it is possible that the kicker and K menu do not exist in 5.10.  The question "How do I upgrade" is still valid.

---

### Post by Zeddicus on 2006-10-19
Kicker is KDE's panel.  The K menu is the KDE equivalent of the "Start Menu".

Are you using KDE or Gnome?

(That said, regardless of using KDE or Gnome, you can edit (with sudo privileges) your /etc/apt/sources.list.  Change all instances of breezy to dapper.  Then just:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

There are graphical ways of doing this, but I'm not clear on which desktop you're using. :)

---

### Post by HalF on 2006-10-19
Thanks Zeddicus.  I am using the default Gnome.  I will try what you suggested.

---

### Post by Zeddicus on 2006-10-19
No problem -- it sounds like you might've been looking at a guide aimed at Kubuntu users, then.  In any case, I'm assuming by 6.02 you meant 6.06 (dapper).

In which case, this upgrade guide will be more useful:

[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

---

### Post by HalF on 2006-10-19
Thanks again Zeddicus.  It is indeed 6.06.  When I attempted to edit the sources.list, I could not change anything, even though I am the administrator.

I will try the guide you pointed to.

---

