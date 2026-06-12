---
title: "Problems with Update Manager wanting me to downgrade OOo packages"
date: 2008-02-04
forum: General Help
---

### Post by Frijolie on 2008-02-04
I've recently uninstalled the Ubuntu branded OOo 2.3.0 using Synaptic. After verifying that it was completely gone, I then downloaded and installed the OOo v 2.3.1 .debs from the Open Office Website. Since then Update Manager has been saying that I have updates to download which are the older OOo packages (version 2.3.0). Why would Update Manager want me to downgrade? Is there a way to fix this annoying problem? When you install manually from .debs does it not register in the package manager?

---

### Post by zvacet on 2008-02-04
In synaptic find your version of package and highlight it>package>lock version.

---

### Post by Frijolie on 2008-02-04
Yes! That did it, Thank You. What does "locking the version" do? Force Synaptic to accept the newer version? Why would it continually want me to downgrade? Does Synaptic prefer an Ubuntu certified package over a newer downloaded version?

---

### Post by Frijolie on 2008-02-04
Wait, I may have spoken too fast. That fixed the Update Manger's nagging however, I'm receiving this error message when trying to install packages from the terminal:

```

The following packages have been kept back:
  openoffice.org-base openoffice.org-calc openoffice.org-draw 
  openoffice.org-headless openoffice.org-impress openoffice.org-math 
  openoffice.org-writer 

```

How do I fix that one?

---

### Post by Xalar on 2008-02-08
I was just getting that error message as well, but somehow fixed it by simply typing:

```
sudo apt-get install ubuntu-desktop
```

It is now upgrading OpenOffice and also removing packages I formerly thought I'd remove completely.

---

