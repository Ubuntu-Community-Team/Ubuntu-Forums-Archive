---
title: "Uninstall Tex"
date: 2007-02-24
forum: General Help
---

### Post by ali780 on 2007-02-24
Hello
How can I uninstall tex and kile in UBUNTU. I want upgrade then to texlive 2007 and kile 1.9.3. I will appreciate if somebody guide me.
Thank you
I am waiting for your fast reply!!

---

### Post by Maestro23 on 2007-02-24
First, how were both these programs installed?  Synaptic, apt-get, aptitude, .tar, .deb, or. rpm?

---

### Post by ali780 on 2007-02-24
I don't know. When I install ububtu I guess tex installed automatically. But I install kile myself. But I can not remember how. I found the method of installation in this forum.

---

### Post by ali780 on 2007-02-24
I think it was apt get fo kile

---

### Post by Maestro23 on 2007-02-24
> **ali780 said:**
> I don't know. When I install ububtu I guess tex installed automatically. But I install kile myself. But I can not remember how. I found the method of installation in this forum.

For tex: Uninstall via Synaptic(GUI).  Search for the package, then mark for uninstall.

For kile, try the same method. or Open a terminal and type:

> sudo apt-get --purge remove kile

sudo apt-get update


*The command line methods should work for both if they were installed via apt-get or Synaptic.

---

### Post by ali780 on 2007-02-24
how can I search for the package. I am very biginer in ubuntu.

---

### Post by Maestro23 on 2007-02-24
> **ali780 said:**
> how can I search for the package. I am very biginer in ubuntu.

Open up the Synaptic package manager.  Hit the search key.  Input the program name. Mark for uninstall.

Apps...System...Synaptic

*Some links you should read/bookmark:

How to Install in Ubuntu: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)
                                    [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by JohnPhys on 2007-02-24
The packages you want to uninstall are 

tetex-base, tetex-extra, tetex-bin, and tex-common.  That should get most everything.

For kile, just 

```
sudo apt-get uninstall kile
```

---

### Post by ali780 on 2007-02-24
What do I do for install kile again?

---

