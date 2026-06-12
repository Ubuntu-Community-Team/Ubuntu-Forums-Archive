---
title: "Keyboard Malfunction"
date: 2015-12-12
forum: General Help
---

### Post by shane_faulkinbury2 on 2015-12-12
I don't think this is related to my OS, but just thought I'd ask!  Anyway my keyboard was working fine and after a couple of days the 'prt srcn' button stopped working.  So I went and bought a new wireless keyboard and I have the same problem on the new one.  Every other key is working.  Anyone have any ideas?

---

### Post by tgalati4 on 2015-12-12
Open a terminal, and run:

```
xinput --list
```  

What version of Ubuntu and what desktop environment are you running?  PrtSc is normally mapped to the screenshot command, typically *gnome-screenshot* or *mate-screenshot* located in /usr/bin.  If that definition becomes broken, then the PrtSc key won't do anything.

```
apropos screenshot
```

---

### Post by shane_faulkinbury2 on 2015-12-13
Thanks, that did the trick! I just ran a "sudo apt-get install gnome-screenshot" and everything is back to normal now!

---

