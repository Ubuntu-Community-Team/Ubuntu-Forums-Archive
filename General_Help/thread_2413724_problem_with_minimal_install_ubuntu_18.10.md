---
title: "problem with minimal install ubuntu 18.10"
date: 2019-03-01
forum: General Help
---

### Post by jepide on 2019-03-01
Hello !

I had problem with zoneminder  installed on ubuntu 18.10, Ubuntu was hard frozing randomly.

So I now made a fresh minimal install of ubuntu 18.10 without anything else. 
For test I loaded gnome-system-monitor 
System-monitor looks to work well but I have plenty ot messages in dmesg and in syslog as follow:

Mar  1 10:32:50 barebone kernel: [ 2176.799647] audit: type=1400 audit(1551432770.350:124569): apparmor="DENIED" operation="open" profile="snap.gnome-system-monitor.gnome-system-monitor" name="/proc/1/cgroup" pid=2693 comm="gnome-system-mo" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Mar  1 10:32:50 barebone kernel: [ 2176.799769] audit: type=1400 audit(1551432770.350:124570): apparmor="DENIED" operation="open" profile="snap.gnome-system-monitor.gnome-system-monitor" name="/proc/1/cgroup" pid=2693 comm="gnome-system-mo" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Mar  1 10:32:50 barebone kernel: [ 2176.799873] audit: type=1400 audit(1551432770.350:124571): apparmor="DENIED" operation="open" profile="snap.gnome-system-monitor.gnome-system-monitor" name="/proc/801/wchan" pid=2693 comm="gnome-system-mo" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Mar  1 10:32:50 barebone kernel: [ 2176.800239] audit: type=1400 audit(1551432770.350:124572): apparmor="DENIED" operation="open" profile="snap.gnome-system-monitor.gnome-system-monitor" name="/proc/801/cgroup" pid=2693 comm="gnome-system-mo" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Ma

And so on. it does not stop.
I am affraid that may be a reason why ubuntu frozes. 

Anyway I would like a solution (or a way to search / try) to not have these warnings happen.

May somebody help me ?

Thanks

---

### Post by jepide on 2019-03-01
from [http://forum.ubuntu-fr.org/](http://forum.ubuntu-fr.org/)   I received

Ces messages semblent provenir du fait que *gnome-system-monitor* est installé en [snap]("http://doc.ubuntu-fr.org/snap").

Tu peux installer la version *.deb* avec :
sudo apt install gnome-system-monitor
Puis supprimer le Snap avec :
snap remove gnome-system-monitor
A+

this works
problem solved

---

