---
title: "gnome crashing at boot"
date: 2007-03-27
forum: General Help
---

### Post by mpooley on 2007-03-27
Hi
I have been using Ubunto for about a week now and I love it.
I certainly am NOT going back to windows ever!

Unfortunately i could resist installing the KDE desktop to satisfy my curiosity and I was very impressed! it makes it very hard to choose between them.
So I decided to switch sessions back to Gnome to compare.

well all hell broke loose -- Bug Buddy kept popping up for network  - gnome panel etc etc etc - Opera crashed - all before i'd had a chance to do anything.

I've reported the bugs but i've had to boot back to Kubuntu now to get a working machine.

I did reboot and try a couple more times but it looks like KDE has mucked up my Gnome?

any suggestions

Mike

---

### Post by zvacet on 2007-03-27
```
sudo gedit var/log/gdm
```
you can also chek **var/log/Xorg.0.lo**g and **var/log/syslog**

---

### Post by mpooley on 2007-03-27
> **zvacet said:**
> ```
sudo gedit var/log/gdm
```
you can also chek **var/log/Xorg.0.lo**g and **var/log/syslog**

thanks
I dont know what was supposed to happen but this is what i got

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by mpooley on 2007-03-27
Ah I am stupid!      i didnt notice that gedit opened with the log files.
all of them were empty though?

thanks

Mike

---

