---
title: "unable to gksudo gedit????"
date: 2007-01-04
forum: General Help
---

### Post by strabes on 2007-01-04
~$ gksudo gedit /etc/fstab

(gedit:27970): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


The gedit window opens and then hangs immediately. Any idea on how to fix this? I am comfortable with using nano so it's not that big of a deal, it just bothers me that it's not working.

---

### Post by Ramses de Norre on 2007-01-04
Does it work with sudo and without any of those? That error message is normal, its a known bug that doesn't cause any harm (other then the message).

---

### Post by kane77 on 2007-01-05
I ran into the same problem...
It doeasnt work neither with "sudo gedit" nor switching to root and then trying gedit....

I would like to solve it... anybody knows?

---

### Post by kvonb on 2007-01-05
This happens to me sometimes, try "gksu gedit" instead of gksudo!

I type that into the "ALT-F2" run box and it works.

Don't know why, I'm permanently baffled :rolleyes:.

---

### Post by yopnono on 2007-01-05
Is it maybe related to this?
[https://launchpad.net/bugs/75524](https://launchpad.net/bugs/75524)

---

