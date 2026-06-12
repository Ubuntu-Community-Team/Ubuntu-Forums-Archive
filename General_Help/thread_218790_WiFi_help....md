---
title: "WiFi help..."
date: 2006-07-19
forum: General Help
---

### Post by foxmxrcer on 2006-07-19
hey guys,
I recently downloaded Ubuntu onto my laptop. It used to have XP, and i used a Dlink AirPlus DWL-650+.  I searched almost everywhere for a driver for it to use on Ubuntu, but found nothing.  Anyone know where i can get one? or how to load it on?

thanks, jake

---

### Post by Sendervictorius on 2006-07-19
It looks like the DWL-650+ uses an ACX100 chipset.

To make sure, from terminal command line, please type: lspci
to identify your chipset, and post the results here.

There is tons of info available.

This link: [http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)
links to the acx100 driver project.

This is helpful for Dapper etc.:
[http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu)

---

### Post by Sendervictorius on 2006-07-19
First take a look at this link: It explains how to get the DWL-650+ going on Dapper.

[https://help.ubuntu.com/community/WifiDocs/Driver/acx100](https://help.ubuntu.com/community/WifiDocs/Driver/acx100)

---

### Post by foxmxrcer on 2006-07-19
thanks,
but uhhmmmm... im a bit of a dunce when it comes to linux, I assume you type all that into the terminal?  But when i did only 1 thing worked then the rest was "command not found".](*,)   after the first command it says  that it would not find the package build essentials

---

