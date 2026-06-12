---
title: "kmail opens links in quanta+ instead of firefox"
date: 2007-02-20
forum: General Help
---

### Post by nandasunu on 2007-02-20
For some reason kmail opens links from within emails with quanta+ instead of firefox, I can't figure out why or how to fix it, it never used to do this. 

Any help would be appreciated, thanks.

btw I am running kmail inside of gnome mostly, I do have kde installed, but hardly use it these days.

---

### Post by nandasunu on 2007-02-21
*bump*

---

### Post by nievo on 2008-01-17
I'm having the same problem, anyone have any ideas?
I'm running kubuntu, but I seem to remember having a similar problem with evolution opening links in quanta, so I'm thinking maybe it's a problem with quanta setting default file associations when it is installed?

---

### Post by Tari Narmolanya on 2008-01-23
I have the same problem, but in my case it opens any links in Bluefish (which means a similar cause, i guess).

Some background info: Using Ubuntu 7.10 with gnome and Kmail (from the repo's Version 1.2.4 (enterprise 0.20070907.709405)) And Firefox 2.0.11. All updates installed.  
If that makes any sense here is the part from about plugins in Firefox
```
network.protocol-handler.app.mailto (...) /usr/bin/kmail
and:
network.protocol-handler.external.mailto (...) Bolean true 
```
It might be interesting that when I click 'File > send Link' within Firefox, in fact my kmail open a new Mail but the link do not appear.

I hope someone may help...

---

