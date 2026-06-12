---
title: "VMWare Server Uninstallation"
date: 2007-07-12
forum: General Help
---

### Post by Vendetta_NZ on 2007-07-12
When I try to uninstall VMWare Server, which I installed using Automatix a while ago, I get this error. I'm fairly sure I uninstalled it fully because its available in Automatix again in the install section, not the uninstall section. I need to reinstall it again now, but it won't let me because it thinks its still installed, this is the error I get:

```
A previous installation of a VMware product has been detected.

If you installed it from the VMware website, please remove it by running vmware-uninstall.pl before proceeding. 

If it was installed through Ubuntu, you must purge (completely remove) the old package.
```

This happens when i do sudo apt-get install vmware-server

Any ideas? Really need to sort this out.

---

### Post by HermanAB on 2007-07-12
Hunt it down with 'find' and delete it.  Something like this:
$ cd /
$ find / -name *vmware*

---

### Post by Vendetta_NZ on 2007-07-12
Oh okay, totally noob question but how do you delete files in console?

---

### Post by kcsdman on 2007-07-20
Just had this exact problem.  You can remove them all automagically by adding an exec to the end of the find :)

sudo find ./ -name "*vmware* -exec rm {} \;

worked great for me

---

