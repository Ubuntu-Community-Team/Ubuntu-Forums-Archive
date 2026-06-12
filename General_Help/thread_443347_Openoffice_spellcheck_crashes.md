---
title: "Openoffice spellcheck crashes"
date: 2007-05-14
forum: General Help
---

### Post by markoloka on 2007-05-14
I need to use in OpenOffice spellcheck. I go to Tools-> Spellcheck and OO instantly crashes. If i go from Tools-> Options -> Language Settings and it crashes immediatily. No matter if i use Word, spreadsheet or what, it crashes everytime. I tried w/ 2 different users and everytime same thing happens. 
I found this on system log aeverytime OO crashes: 
05/14/2007 07:04:14 PM	ubuntu	gconfd (root-11085)	Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
05/14/2007 07:04:14 PM	ubuntu	gconfd (root-11085)	Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
05/14/2007 07:04:14 PM	ubuntu	gconfd (root-11085)	Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
05/14/2007 07:04:14 PM	ubuntu	gconfd (root-11085)	Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
05/14/2007 07:04:14 PM	ubuntu	gconfd (root-11085)	Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
05/14/2007 07:04:14 PM	ubuntu	gconfd (root-11085)	GConf server is not in use, shutting down.

I using Kubuntu Feisty w/ default OO 2.2.

---

