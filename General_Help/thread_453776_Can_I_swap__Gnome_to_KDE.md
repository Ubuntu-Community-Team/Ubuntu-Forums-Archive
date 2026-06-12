---
title: "Can I swap  Gnome to KDE?"
date: 2007-05-24
forum: General Help
---

### Post by the lemming on 2007-05-24
I have ubuntu with XP on my laptop.  At the moment I am using Gnome and would like to know if it is possible to swap this bit for KDE?

Cheers

---

### Post by atoponce on 2007-05-24
Pull up a terminal, and type:

```
sudo aptitude install kubuntu-desktop
```

or

```
sudo aptitude install kde
```

The only difference is the package 'kubuntu-desktop' is KDE with software that Ubuntu thinks you should use with Ubuntu branding, while the 'kde' package installs software that KDE thinks you should use without Ubuntu branding.

If you want to remove Gnome completely, then at the terminal, type:

```
sudo apt-get remove ubuntu-desktop
sudo apt-get autoremove
```

---

### Post by darklemming54 on 2007-05-24
Just open up the terminal and type
```

sudo apt-get install kubuntu-desktop

```



edit: beaten to it

---

### Post by bobplano on 2007-05-24
yea and once you do that you can change to kde before you log in by going to options>sessions>kde.

---

### Post by fragos on 2007-05-24
You can install the KDE destop and even have both installed at the same time.

---

### Post by the lemming on 2007-05-25
> **atoponce said:**
> Pull up a terminal, and type:

```
sudo aptitude install kubuntu-desktop
```

or

```
sudo aptitude install kde
```

The only difference is the package 'kubuntu-desktop' is KDE with software that Ubuntu thinks you should use with Ubuntu branding, while the 'kde' package installs software that KDE thinks you should use without Ubuntu branding.

If you want to remove Gnome completely, then at the terminal, type:

```
sudo apt-get remove ubuntu-desktop
sudo apt-get autoremove
```


I tried your instructions and re-booted my laptop in case this would help but as far as I can see there is no difference between KDE and Gnome.  Should I have seen a difference?

---

### Post by Boztech on 2007-05-25
Log Out
Click Sessions
Choose KDE
Log In

It will ask you if you want to make KDE the default for your login sessions.

---

### Post by the lemming on 2007-05-25
> **Boztech said:**
> Log Out
Click Sessions
Choose KDE
Log In

It will ask you if you want to make KDE the default for your login sessions.


Me no like it.

Now that I've had a play I can't always close the windows by clicking on the close tab.  I have to right click and then choose close.

Too much faff.

How do I change back to gnome please?

---

### Post by bobplano on 2007-05-25
do the same thing except choose gnome

---

