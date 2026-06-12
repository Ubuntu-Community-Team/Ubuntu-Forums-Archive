---
title: "Uninstall software"
date: 2007-09-22
forum: General Help
---

### Post by thhjimmy on 2007-09-22
Hi,
just want to find out is there something like uninstall software in Ubuntu?
My problem, I install the Opera browser. Halted half way as there are missing
lib. So the icon and services are already installed,  any way to remove those?
:popcorn::confused:

---

### Post by treis on 2007-09-22
sudo apt-get remove opera

---

### Post by thhjimmy on 2007-09-23
Thanks for the reply.

I can't use 'sudo apt-get remove opera' due Opera browser was manually download and install.

:KS:KS:KS

---

### Post by Maestro23 on 2007-09-23
> **thhjimmy said:**
> Thanks for the reply.

I can't use 'sudo apt-get remove opera' due Opera browser was manually download and install.

:KS:KS:KS

Was it a .deb?

> sudo dpkg -P packagename

*This will delete the config files as well.

---

### Post by corevette on 2007-09-23
maybe if you reinstall manually and finish it, it might be easier to uninstall

---

### Post by Martje_001 on 2007-09-23
Go to synaptic and search for 'opera'. But if libs are missing, Opera is not installed.

---

### Post by trippinnik on 2007-09-23
How did you install Opera?  Did you click on the link from the opera website?  If you did you installed from the deb, and as mentioned before you should use the 
sudo dpkg -r <packagename> 
command

---

### Post by thhjimmy on 2007-09-23
Will try it out. Thanks.
you guys rocks :guitar:

---

### Post by mcduck on 2007-09-23
> **thhjimmy said:**
> Thanks for the reply.

I can't use 'sudo apt-get remove opera' due Opera browser was manually download and install.

:KS:KS:KS

If it was installed from a .deb package you can use apt-get (or Synaptic) to remove it.

---

