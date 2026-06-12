---
title: "[SOLVED] How to get my printer working?"
date: 2008-03-29
forum: General Help
---

### Post by barnowl13 on 2008-03-29
Okay I can now do most things with Ubuntu that I want but the only thing that is doing my head is I can't get my printer working?
I have a canon pixma ip 3000, it is connected to a USB 2.0 port, but when I go into printer configuration it shows printer connected to parallel port?

I have looked through the forums and have found info on drivers and have download them but they do not seem to install. I think I must be doing something wrong? Or is it that Ubuntu does not see my USB ports?

Can anyone help me with this problem?:confused:

---

### Post by spec-chum on 2008-03-29
Canon are notorious for not providing Linux support.

I've got a Pixma MP 500 and I bought TurboPrint which supports it fine.  It looks like it supports your printer too, so that's a possibility for you.

You can get TurboPrint here:
[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

---

### Post by luceerose on 2008-03-29
Open synaptic and install the following;

cupsys-driver-gutenprint
foomatic-db-gutenprint
ijsgutenprint
libgutenprint2
libgutenprintui2-1
hal-cups-utils

then reboot computer

If your printer isn't installed after that, your pretty much screwed.

---

### Post by barnowl13 on 2008-03-29
Thanks for that I have just got my printer working by connecting to my USB 1.5 port and have using Turoboprint free addition. So of course I now wish to purchase as key to take off the logo. But don't laugh as I said in the my first post it has been doing my head in and I deleted the The configuration tool xtpconfig of my desktop any idea how to get this back so I can enter my key?

---

### Post by luceerose on 2008-03-29
It was the gutenprint drivers & hals-cups-utils
mentioned in my earlier post that got everything working for me.
I have a Canon Pixma MP780

---

### Post by barnowl13 on 2008-03-29
Thanks for your help all is working okay now!!!:)

---

