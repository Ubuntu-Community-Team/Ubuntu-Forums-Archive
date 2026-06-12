---
title: "icon errors after upgrade"
date: 2012-10-20
forum: General Help
---

### Post by Stauricus on 2012-10-20
hello everybody
after upgrading lubuntu from 12.04 to 12.10, i'm having some strange issues with icons visualization.
in the desktop, some icons are transparent:
[IMG]http://img12.imageshack.us/img12/3066/201210201355131024x768s.png[/IMG]

in file manager, some icons simply don't appear
[IMG]http://img33.imageshack.us/img33/3711/201210201356111024x768s.png[/IMG]

this happens at any place where icons should appear (including the start menu)
[IMG]http://img822.imageshack.us/img822/6554/201210201403181024x768s.png[/IMG]

i tried changing icon themes, with no success :(
i'm really unlucky with Linux... #-o

any help is apreciated. thanks in advance.

---

### Post by Stauricus on 2012-10-21
is there any way to reinstall pcmanfm? i think it is the problem.
some icons blink when i put the mouse cursor over them...

---

### Post by Rex Bouwense on 2012-10-21
Try relaunching it:
  ```
 pcmanfm --desktop --profile=LXDE
```

---

### Post by Stauricus on 2012-10-21
tried it. same thing :/

---

### Post by Stauricus on 2012-10-22
i completely reinstalled PCManFM and LXDE with these comands (after switching to virtual console):

```
sudo apt-get --purge remove pcmanfm
sudo apt-get install lubuntu-desktop lubuntu-default-settings lxde
```

and i still have this problem. no one has similar bugs?
it's the third issue i have with a Linux Distro, and also the third i'm giving up :(

---

