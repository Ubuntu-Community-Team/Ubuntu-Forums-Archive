---
title: "nomachine issues"
date: 2008-05-06
forum: General Help
---

### Post by fmpdmb on 2008-05-06
I recently updated to the latest distro and things aren't good.  I can no longer connect to my box from my WinXP box using nxserver (nomachine.com).  I'm getting the following error:
"Cannot find the KDE environment. Please contact your system administrator."
Any thoughts?

---

### Post by argentum on 2008-05-06
I have exactly the same problem and would appreciate help too...

---

### Post by petrpilar on 2008-05-06
Hi,

I had the same problem after upgrade to Kubuntu 8.04 (Hardy Heron).

I have in the '/usr/NX/etc/node.cfg' following command for the KDE launch: 
CommandStartKDE="/usr/bin/dbus-launch --exit-with-session startkde"

The dbus-lauch was missing.

I ran:

sudo apt-get install dbus-x11

and it works.

---

