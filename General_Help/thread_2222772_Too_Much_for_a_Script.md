---
title: "Too Much for a Script?"
date: 2014-05-08
forum: General Help
---

### Post by Quarkrad on 2014-05-08
I have a neighbour who I've suggested moves to Ubuntu (12.04) from win7.  One issue is they use an ms publishing product called Home Publishing 2000 and I have not got this to work via wine.  So, another option is to install winXP within virtualbox and then install Home Publishing. (This winxp environment does not have to be connected to the internet as it is used purely as the platform for Home Publishing).  Is it possible to put an icon on the Ubuntu desktop that when clicked will launch a script in the background that will fire up Home Publishing rather than the user having to manually launch virtualbox, winxp guest, Home Publishing?

---

### Post by sotiris2 on 2014-05-08
```
virtualbox --startvm [name]
```
This will launch the virtual machine named *name*

[This]("http://www.virtualbox.org/manual/ch08.html#idp55479184") is vbox's command line manager manual, which is what you can use in a script. Now I don't know if its possible to *feed* a script to the guest system.

EDIT: Ofcourse since you just want a program to run on windows start you don't need a script. One thing windows is effective at is running things at startup! :p

---

### Post by dragonfly41 on 2014-05-08
Suggestion to your neighbour .. look at [www.scribus.net](www.scribus.net) as an alternative to Publisher.

No need for windows installation.

---

