---
title: "Making a deb file with debuild -i -us -uc -b explained"
date: 2020-05-20
forum: General Help
---

### Post by Achilles124 on 2020-05-20
In order to make a deb file with debuild, you will have to give the command: 
```
debuild -us -uc -b
```
I tried to figure out what these options are, but I can't find them on the man page of this command. This command is in the examples section of the man page.
But what are these options: -us, -uc and -b?

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.6 LTS
Release:	        16.04
Codename:	xenial

---

### Post by &amp;KyT$0P# on 2020-05-20
Does [FONT=Courier New]man dpkg-buildpackage[/FONT] help you?

---

### Post by Achilles124 on 2020-05-20
Thank you, halogen2.

---

### Post by &amp;KyT$0P# on 2020-05-20
You're welcome :KS

---

