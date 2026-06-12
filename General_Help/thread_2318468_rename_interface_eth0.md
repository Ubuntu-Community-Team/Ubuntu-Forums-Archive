---
title: "rename interface eth0"
date: 2016-03-26
forum: General Help
---

### Post by daemoncesar on 2016-03-26
[COLOR=#212121][FONT=arial]I changed parameters in grub to change the name of the network interface (eth0)..

[/FONT][/COLOR]

[COLOR=#212121][FONT=arial]I have a future problem doing is changing ?[/FONT][/COLOR]

---

### Post by QDR06VV9 on 2016-03-26
> **daemoncesar said:**
> [COLOR=#212121][FONT=arial]I changed parameters in grub to change the name of the network interface (eth0)..

[/FONT][/COLOR]

[COLOR=#212121][FONT=arial]I have a future problem doing is changing ?[/FONT][/COLOR]
Not sure i fully understand? But renaming your network is possible.
```
gksudo gedit /etc/udev/rules.d/70-persistent-net.rules 
```

For Example:
Swap eth0 and eth1. Proofread carefully, save and close gedit. Use any other text editor if you don't have gedit. Reboot immediately and you should be all set.
Credit to chili555

---

### Post by daemoncesar on 2016-03-26
[COLOR=#212121][FONT=arial]Rename the interface may not cause bad for the system?[/FONT][/COLOR]

---

### Post by QDR06VV9 on 2016-03-26
Not the way I showed you...but through Grub i have to plead Ignorance I just don' know.

---

### Post by HermanAB on 2016-03-26
See this:
[http://www.aeronetworks.ca/2014/04/fedora-linux-eth0.html](http://www.aeronetworks.ca/2014/04/fedora-linux-eth0.html)

---

### Post by QDR06VV9 on 2016-03-26
> **HermanAB said:**
> See this:
[http://www.aeronetworks.ca/2014/04/fedora-linux-eth0.html](http://www.aeronetworks.ca/2014/04/fedora-linux-eth0.html)

Thank You Sir nice share..and now I am less ignorant.:D

---

### Post by daemoncesar on 2016-03-26
[COLOR=#212121][FONT=arial]my fear is that it's change may affect my system in the future.[/FONT][/COLOR]

---

### Post by QDR06VV9 on 2016-03-26
Sigh...Then don't change it.

---

### Post by daemoncesar on 2016-03-26
[COLOR=#212121][FONT=arial]OK. I also think it can happen any problem in a future update .[/FONT][/COLOR]

---

