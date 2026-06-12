---
title: "Isolating the installation of Firefox 3 Alpha 1 [Resolved]"
date: 2007-01-15
forum: General Help
---

### Post by Quillz on 2007-01-15
I have Alpha 1 of Firefox 3.0 that I want to install, but I don't want it to overwrite the bundled Firefox 2.0.0.1. Is there a simple way to set up the installation so it doesn't affect the original files?

---

### Post by aysiu on 2007-01-15
Yes. Follow these directions:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

Afterwards, the command ```
firefox
``` will launch Alpha 3 and the command ```
firefox.ubuntu
``` will launch 2.0.0.1

---

### Post by Quillz on 2007-01-15
Those instructions are for installing Firefox 2, though? Will the same steps work with Firefox 3 Alpha 1?

---

### Post by aysiu on 2007-01-15
> **Quillz said:**
> Those instructions are for installing Firefox 2, though? Will the same steps work with Firefox 3 Alpha 1?
Should. You'd have to modify the instructions to target the appropriate .tar.gz name, of course.

---

### Post by Quillz on 2007-01-15
> **aysiu said:**
> Should. You'd have to modify the instructions to target the appropriate .tar.gz name, of course.
Thanks, those instructions worked fine. I stopped short of backing up the 2.x profile and modifying the system shortcuts, though. Simply installing Firefox 3 Alpha 1 to /opt is enough, as I can just browse to that folder to launch Firefox quickly and easily, not to mention it uses its own profile, making the backup unnecessary.

---

### Post by aysiu on 2007-01-15
> **Quillz said:**
> Thanks, those instructions worked fine. I stopped short of backing up the 2.x profile and modifying the system shortcuts, though. Simply installing Firefox 3 Alpha 1 to /opt is enough, as I can just browse to that folder to launch Firefox quickly and easily, not to mention it uses its own profile, making the backup unnecessary.
It uses its own profile?

---

### Post by Quillz on 2007-01-15
> **aysiu said:**
> It uses its own profile?
Actually, on a reboot, it loaded up my 2.x profile, but said profile works fine with 3.0 Alpha 1.

---

