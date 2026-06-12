---
title: "Was going to fix ATI Driver"
date: 2007-02-27
forum: General Help
---

### Post by Jphenow on 2007-02-27
Was about to fix my ATI driver after a long day of fixing stuff and was about to go into adept, adept thinks i have something open preventing updates, installs or removals, which i dont, and along with that when i try to do a *sudo dpkg-reconfigure xserver-xorg* it comes up with this output 
[I]dpkg-query: parse error, in file `/var/lib/dpkg/updates/0040' near line 1:
 newline in field name `padding'
/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed
tsphenow@tsphenow-desktop:~$ sudo dpkg-reconfigure xserver-xorg
dpkg-query: parse error, in file `/var/lib/dpkg/updates/0040' near line 1:
 newline in field name `padding'
/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed[/I]

---

