---
title: "Adept-Unable to access"
date: 2007-02-12
forum: General Help
---

### Post by Clive_ on 2007-02-12
****

I've just attempted to install clamav & klam.(I'm running Kubuntu edgy) Adept seemed to crash midway thru' and now I get this message when I attempt to run Adept.
 
"You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one."

I've got no idea how to fix this. I've tried  sudo apt-get install -f. but I get a message about manual configuration of dpkg. Help please!

---

### Post by an.echte.trilingue on 2007-02-12
When adept crashed it did not remove the LOCK file.  If you reboot it should go away on its own.

---

### Post by Jucato on 2007-02-12
Try

```
sudo dpkg --configure -a
```

---

