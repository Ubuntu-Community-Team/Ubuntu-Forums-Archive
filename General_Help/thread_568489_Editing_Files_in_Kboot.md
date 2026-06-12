---
title: "Editing Files in Kboot"
date: 2007-10-05
forum: General Help
---

### Post by Black Mage on 2007-10-05
How do I edit the kboot file in the kboot command line before I actually boot the system and log in? I can the the /etc/kboot.config but I can't edit it because nano and gedit doesn't work.  Help please. And this is kboot on my ps3.

---

### Post by p_quarles on 2007-10-05
You need to invoke root privileges to edit files outside of your own home directory. Either:
```
sudo nano /etc/kboot.config
```
or
```
gksudo gedit /etc/kboot.config
```

---

### Post by Black Mage on 2007-10-05
I've tried those and is says in kboot that the library cannot be accessed. Is there a more basic or different editor besides nano and gedit?

---

### Post by p_quarles on 2007-10-05
I have no idea, since I've never used kboot. According to the [documentation]("http://kboot.sourceforge.net/doc/kboot-lk2005.ps.gz"), however, the config file is named "/etc/kboot.conf" (not .config).

---

