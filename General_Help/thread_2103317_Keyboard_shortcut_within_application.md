---
title: "Keyboard shortcut within application"
date: 2013-01-09
forum: General Help
---

### Post by caughran on 2013-01-09
Hi. Two or three years ago, I could add shortcuts to menu items within an application. For example, if I am in a gnucash account ledger and put the cursor on a posting to a different account, then press control+j, gnucash opens the other account and finds the transaction in that account. This simply executes the Actions/Jump menu item.

But I've lost the ability.... I think I turned an Ubuntu switch somewhere, opened the menu and selected the item, and pressed the new shortcut key. Then I would forget to reset the switch and ... never mind.

How does one create a shortcut within an application for a menu item? I've got 12.10.

-- 
jim

A computer and a cat Are somewhat alike--they both purr and like to be stroked and spend a lot of the day motionless.  They also have secrets they don't necessarily share.
~ John Updike in The New Yorker.

---

### Post by llamabr on 2013-01-09
[http://superuser.com/questions/121673/how-do-i-remap-ctrl-j-to-ctrl-c-on-ubuntu](http://superuser.com/questions/121673/how-do-i-remap-ctrl-j-to-ctrl-c-on-ubuntu)

---

### Post by stinkeye on 2013-01-10
Firstly enable **can-change-accels**.
Terminal...
```
gsettings set org.gnome.desktop.interface can-change-accels true
```

Changing accelerators doesn't work with the global menu.
So you need to start your application with the global menu disabled.
(For others reading this and want to change accelerators in nautilus, kill nautilus first... ie run **nautilus -q** then **UBUNTU_MENUPROXY=0 nautilus**)
eg
_Method 1_```
UBUNTU_MENUPROXY=0 **gnucash**
```


[SIZE="3"]**or**[/SIZE]
_Method 2_ 
disable the global menu altogether  (need to logout to take affect)
can then start your application normally....
```
sudo su
echo "export UBUNTU_MENUPROXY=" > /etc/X11/Xsession.d/81ubuntu-menu-proxy
```


Should now be able to hover over menu shortcuts and press your desired shortcut keys.
After changing accelerators if you used the second method...
Re-enable the global menu (then logout)...
```
sudo rm /etc/X11/Xsession.d/81ubuntu-menu-proxy
```

and for both methods,
disable can-change-accels so you don't accidently change...
```
gsettings reset org.gnome.desktop.interface can-change-accels
```


P.S If you have the Gnome Classic session installed you could skip the global menu disabling methods
and log in to that session to change accelerators.

---

### Post by caughran on 2013-01-10
Thanks!

jim



Did a lightbulb appear over Edison's head just before he invented the lightbulb?~ Mike Lester, 2012

---

### Post by caughran on 2013-04-22
I finally got around to doing this. Worked like a charm. 

Thank you, Stinkeye from down under.

---

