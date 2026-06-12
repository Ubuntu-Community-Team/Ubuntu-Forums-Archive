---
title: "Root Password Being Requested for Some Applications"
date: 2012-11-12
forum: General Help
---

### Post by Dennis N on 2012-11-12
I am working with a new install of Lubuntu 12.10 installed with Alternate Installer. I am finding some applications are asking for a root password to start rather than my password (which does not work) - examples I notice so far are gdebi, galternatives, pcmanfm (to open folder as root).

Synaptic still works with my password. Terminal commands requiring authentication work fine with sudo and my password, as in 'sudo apt-get install'

I am in the adm and sudo groups.

How can I get these applications to work with my password?

---

### Post by papibe on 2012-11-12
Hi Dennis N.

It happened to me once in Lubuntu. It was a case of misconfigured gksudo (the graphical sudo). Go into a terminal and run:
```
gksu-properties
```
It'll open a window. Under Behavior there's a field called 'Authentication mode'. If it says 'su', change it to 'sudo'.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Dennis N on 2012-11-12
@papibe

Thanks, that did it. I really appreciate your help.

---

