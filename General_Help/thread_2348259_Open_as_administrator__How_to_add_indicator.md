---
title: "Open as administrator : How to add indicator"
date: 2017-01-02
forum: General Help
---

### Post by meetdilip on 2017-01-02
I have 16.04 + unity. It is up to date with recent updates. Currently, I have option to open a folder as *administrator*. I would like to have some sort of warning displayed ( a banner maybe ) to remind me that the folder is opened as administrator. I have seen such indicators in Cinnamon. Is it possible to have them in Unity as well ? Thanks.

---

### Post by vasa1 on 2017-01-02
One "trick" is to have visually different themes for root and for the standard user. That should serve as an indicator in any desktop environment.

For example, I use Greybird for the standard user and Adwaita for root.

---

### Post by mc4man on 2017-01-02
There is no indicator for this, could someone create one?, maybe. 
If you are using the default of global menus then you'll notice that root can't use them so menus will be in root app windows.
Also note that preferences for user & root are saved separately so for example with gedit it I set a different theme in gedit's pref's.

---

### Post by vasa1 on 2017-01-02
> **mc4man said:**
> There is no indicator for this, could someone create one? ...

I ran```
sudo -H pcmanfm
```and saw a little indicator with a tooltip indicating that I was in "super user mode".

Thunar has something even more obvious: see thunar.png

---

### Post by meetdilip on 2017-01-02
Thanks for reply guys. Is the file manager managed by Ubuntu team ? Is it possible to push a warning banner with the next update ?

---

### Post by mc4man on 2017-01-02
> **meetdilip said:**
> Thanks for reply guys. Is the file manager managed by Ubuntu team ? Is it possible to push a warning banner with the next update ?
Well nautilus is handled by possibly the Desktop team but they have nothing to do with running nautilus as root.
The current easiest method (that you may be using?) is thru the nautilus-admin package which is a nautilus extension in Universe, i.e. community supported.
So if anything file a bug against nautilus-admin & see if the author/maintainer (Bruno Nova) has any interest in pursuing.

---

### Post by meetdilip on 2017-01-03
Thanks @mc4man. Could you link me to the site where I should be filing the bug report ?

---

### Post by deadflowr on 2017-01-03
Report it here:
[https://launchpad.net/ubuntu/+source/nautilus-admin]("https://launchpad.net/ubuntu/+source/nautilus-admin")

---

### Post by meetdilip on 2017-01-04
Thanks @deadflowr . I just filed a bug report

[https://bugs.launchpad.net/ubuntu/+source/nautilus-admin/+bug/1653954](https://bugs.launchpad.net/ubuntu/+source/nautilus-admin/+bug/1653954)

---

