---
title: "dpkg: configuration error: unknown option log: Success"
date: 2005-08-02
forum: General Help
---

### Post by kismet-sl on 2005-08-02
Hi all,
   I tryed to downgrade from breezy to ubuntu and now I'm looked. The command 
**dpkg** always return
dpkg: configuration error: unknown option log: Success
but other command like **dpk-query,apt,etc.** works.

Anyone can give my any tips?

I have tryed to boot with knoppix and downgrade (hoary version) of dpkg with
dpkg --root=/mnt/hda3/ -i pkg<version>.deb
but even if I get no error after rebooting I sill get the same error

Thank you

---

### Post by lol on 2005-08-04
comment the line starting with "log" in /etc/dpkg/dpkg.cfg ...

I am not 100% sure about the filename (I deleted it), but it is something like this.

---

