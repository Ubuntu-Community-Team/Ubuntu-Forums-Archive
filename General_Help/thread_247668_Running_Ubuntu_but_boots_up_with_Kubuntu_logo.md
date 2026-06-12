---
title: "Running Ubuntu but boots up with Kubuntu logo"
date: 2006-08-31
forum: General Help
---

### Post by Melcar on 2006-08-31
This is a weird request but here goes.  I'm running Ubuntu with Gnome but the boot screen (where all the initializations are displayed) shows the blue Kubuntu logo instead of the browm Ubuntu one.  I recenty installed KDE and after a few days uninstalled it.  Still that blue logo shows up every time I boot up my laptop:confused: .  It's trivial I know, but I want to revert to the Ubuntu logo.

---

### Post by frodon on 2006-08-31
Open a terminal and type : ```
sudo update-alternatives --config usplash-artwork.so
```Select the usplash you want (ubuntu or kubuntu) and press enter then type : ```
sudo dpkg-reconfigure linux-image-`uname -r`
```That's all.

---

### Post by jmeadows111 on 2006-08-31
Is there a missing back tick on the second command?

i.e. 

sudo dpkg-reconfigure linux-image-`uname -r

should be

sudo dpkg-reconfigure linux-image-`uname -r`

---

### Post by frodon on 2006-08-31
You're right, i made a typo

corrected

---

### Post by Melcar on 2006-08-31
Worked perfectly.  Thanks guys:D

---

### Post by ÄlveKatt on 2006-09-08
Had the problem described here. Your solution did not work, however. 

sudo update-alternatives --config usplash-artwork.so returned:
There is only 1 program which provides usplash-artwork.so (/usr/lib/usplash/usplash-default.so). Nothing to configure.

So I am scratching my head. Any ideas?

---

### Post by clarkth on 2006-09-08
I have the same problem, only with the Xubuntu splash screen.  Doesn't really make any difference, but it's sometimes annoying.

I'll try the fix listed tonight.

---

### Post by Jussi01 on 2006-12-04
> **ÄlveKatt said:**
> Had the problem described here. Your solution did not work, however. 

sudo update-alternatives --config usplash-artwork.so returned:
There is only 1 program which provides usplash-artwork.so (/usr/lib/usplash/usplash-default.so). Nothing to configure.

So I am scratching my head. Any ideas?

I have the same problem - did anyone manage to sort this out?

---

