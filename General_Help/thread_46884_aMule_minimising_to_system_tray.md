---
title: "aMule minimising to system tray?"
date: 2005-07-06
forum: General Help
---

### Post by gammyhand on 2005-07-06
I can't get aMule to minimise to the system tray properly...any ideas why? If I choose gnome 2.x as the desktop it just disappears on minimisation and occasionally appears again if I press the show/hide desktop button.

I am definitely using gnome 2.x desktop by the way.

---

### Post by jeremy on 2005-07-07
Which version of amule are you using?

---

### Post by gammyhand on 2005-07-07
[QUOTE=jeremy]Which version of amule are you using?[/QUOTE]
 2.0.0

---

### Post by Zhukov on 2005-07-07
There is a thread in the forums (here) about aMule. You can find in the last page a link for some debs.
Install the with sudo dpkg -i.
Those debs are from aMule 2.0.3, use them.

---

### Post by gammyhand on 2005-07-07
[QUOTE=Zhukov]There is a thread in the forums (here) about aMule. You can find in the last page a link for some debs.
Install the with sudo dpkg -i.
Those debs are from aMule 2.0.3, use them.[/QUOTE]
 Can I not get the package through synaptic then?

---

### Post by jeremy on 2005-07-07
not that one, but it works beautifully (in my case, anyway).

---

### Post by Zhukov on 2005-07-07
Here's the link:
[http://koti.mbnet.fi/ots/linux/hoary/](http://koti.mbnet.fi/ots/linux/hoary/)

You can safely install the latest CVS. It works like a charm.

So far the only problem is with the remote GUI. I managed to use it once or twice and suddently it stopped working.

But the rest is fine and probably my remote GUI problem is my fault :P

You can relax and install those packages. Although some people reported that one of the version give them some errors installing. Try the latest first, and the the second latest. That will work for sure.

By the way, anyone has an updated ipfilter.dat for Portugal? :D

---

### Post by gammyhand on 2005-07-07
OK, I downloaded the latest CVS deb and this is what happened :(

ralph@ralph:~$ sudo dpkg -i $HOME/Desktop/amule_2.0.3+CVS20050616-1~ots_i386.debPassword:
Selecting previously deselected package amule.
(Reading database ... 88794 files and directories currently installed.)
Unpacking amule (from .../amule_2.0.3+CVS20050616-1~ots_i386.deb) ...
Adding `diversion of /usr/bin/ed2k to /usr/bin/ed2k.xmule by amule'
dpkg: dependency problems prevent configuration of amule:
 amule depends on libwxgtk2.5.3 (>= 2.5.3.2ubuntu4); however:
  Package libwxgtk2.5.3 is not installed.
dpkg: error processing amule (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amule
ralph@ralph:~$

---

### Post by Zhukov on 2005-07-07
Did you tried other cvs? Try them please, and install the package they depend on.

---

### Post by gammyhand on 2005-07-07
[QUOTE=Zhukov]Did you tried other cvs? Try them please, and install the package they depend on.[/QUOTE]
 Doh, I missed the dependancy :) Got it installed now.

---

### Post by Zhukov on 2005-07-07
:) Nice

---

