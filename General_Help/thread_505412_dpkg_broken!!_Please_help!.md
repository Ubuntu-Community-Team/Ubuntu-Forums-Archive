---
title: "dpkg broken!! Please help!"
date: 2007-07-20
forum: General Help
---

### Post by benbooth on 2007-07-20
When I run:

**sudo aptitude upgrade**

I get the following message.
[I]
Writing extended state information... Done
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `        ' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 field name `        ' must be followed by colon[/I]

Please help!

---

### Post by Seisen on 2007-07-20
Put this in the terminal

```
gksudo gedit /var//lib/dpkg/available 
``` and then post what it says.

---

