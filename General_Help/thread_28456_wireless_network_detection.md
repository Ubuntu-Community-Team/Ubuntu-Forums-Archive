---
title: "wireless network detection"
date: 2005-04-20
forum: General Help
---

### Post by blu.gecko on 2005-04-20
I am lookingn for a wireless network detection application, can anyone suggest a program that will scan B/A/G wireless networks?

I tried to install Kismet but I could not locate the dependency "libgmp3" and I would like something with a more graphical interface. :roll:

---

### Post by ghost on 2005-04-20
[QUOTE=blu.gecko]I am lookingn for a wireless network detection application, can anyone suggest a program that will scan B/A/G wireless networks?

I tried to install Kismet but I could not locate the dependency "libgmp3" and I would like something with a more graphical interface. :roll:[/QUOTE]

Try [http://gkismet.sourceforge.net/](http://gkismet.sourceforge.net/)

Otherwise run vmware and install netstumbler.  :grin:

---

### Post by Juergen on 2005-04-20
I have no problems to install Kismet via Synaptic, but to just detect networks you can do
```
iwlist ath0 scan
```iwlist is part of the package 'wireless-tools'  - it's just not so graphical ;-)

---

### Post by blu.gecko on 2005-04-21
iwlist ath0 scan or iwlist scanning= wlan0 Failed to read scan data : Operation not supported.

So here I am still looking for a application...Does anyone have a url to the file libgmp3.ubuntu.deb?

---

### Post by thechitowncubs on 2005-04-21
[http://gtkwifi.sourceforge.net/](http://gtkwifi.sourceforge.net/)

very good piece of work

---

### Post by blu.gecko on 2005-04-22
I have been using linux for 2 weeks now, I got my wireless working, but im not sure how to install a tar.bz file, some of the packages require a package called a dependency, does this require any other applications to run? is there a ubuntu.deb file I can download instead

======> learning linux day to day  :roll:

---

