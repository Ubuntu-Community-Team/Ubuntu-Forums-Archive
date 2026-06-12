---
title: "Where do program install, in other words, where is &quot;program files&quot;"
date: 2007-11-15
forum: General Help
---

### Post by mike868y on 2007-11-15
I am working on perfecting my install on fluxbox. I want to modify my menu and the only way to launch the programm is via the path. Where do programs by default install in ubuntu? what path would i have to use to launch this app? Thanks for the help

---

### Post by HermanAB on 2007-11-15
System schtuff are in /sbin and /lib
Application schtuff compiled by your distribution house (Canonical in this case), goes into /usr/bin and /usr/lib
Application schtuff you compile yourself, goes into /usr/local/bin and /usr/local/lib

There is something called the Linux Standards Base that defines these things.

---

### Post by mike868y on 2007-11-15
thank you very, very much lol i've been wondering this for a long time

---

### Post by aysiu on 2007-11-15
I don't think you need to know the path.

Most applications can be launched by just the name of the application. Both ```
firefox
``` and ```
/usr/bin/firefox
``` should work.

---

### Post by jviscosi on 2007-11-15
.... and if you're wondering where a particular program is going to be launched from, you can use **which**, e.g.:

> 
(1) $which fluxbox
/usr/bin/fluxbox


---

### Post by ramjet_1953 on 2007-11-16
Two tips that help you find applications that disappear into the 'Black Hole'.

1. If you have an application named 'fred' , open a terminal and type in:

>  [COLOR="Red"]whereis fred[/COLOR]

2. Open up [COLOR="Blue"]Synaptic Package Manager[/COLOR], click on [COLOR="Blue"]Settings>Preferences[/COLOR]. Now , when the window opens, click on the [COLOR="Blue"]General Tab[/COLOR]. Under the [COLOR="Blue"]Properties[/COLOR] heading, put a tick in the option S[COLOR="Blue"]how Properties in the Main Window.[/COLOR]
Now when you search for an installed package, you can view all of the files installed and their locations.

Regards,
Roger :cool:

---

