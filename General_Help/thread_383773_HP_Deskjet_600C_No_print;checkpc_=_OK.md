---
title: "HP Deskjet 600C No print;checkpc = OK"
date: 2007-03-13
forum: General Help
---

### Post by christedhe on 2007-03-13
I am working with [[www.linux-foundation.org]](www.linux-foundation.org])
I installed hpijs fom the Debian site; along with foomatic-rip.
As per this site's suggestion:
I changed my printcap to:

lp|HP Deskjet 600C:\
:lp=/dev/lp0:\
:force_localhost:\
:if=/usr/bin/foomatic-rip:\
:ppdfile=/etc/foomatic/lpd/lp.ppd:\
:sd=/var/spool/lpd/lp:\
:mx#0:\
:sh:

and then tried their examples for lpd and lprng:

edward@robe:~$ lpr -Plp -Jdocs /proc/cpuinfo
lp: nothing to print
edward@robe:~$ lpr -Plp -Z docs /proc/cpuinfo
lp: nothing to print
edward@robe:~$ sudo checkpc
Any suggestions?

---

### Post by 11hjpphty76lkjj on 2007-03-23
Please use HPLIP.

[http://hplip.sf.net](http://hplip.sf.net)

The DeskJet 600c is supported..

---

