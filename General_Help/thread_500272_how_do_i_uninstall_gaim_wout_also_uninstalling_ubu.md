---
title: "how do i uninstall gaim w/out also uninstalling ubuntu desktop"
date: 2007-07-13
forum: General Help
---

### Post by ireblue on 2007-07-13
i want to install pidgin, but was told i should uninstall gaim first..but when i try this it also selects ubuntu desktop to be removed also. how do i get around this.

thx

---

### Post by firebadger on 2007-07-13
sudo apt-get remove gaim

...is one way.

---

### Post by Motoxrdude on 2007-07-13
Ubuntu desktop is a meta-package. It is not a package itself. So if you do "sudo apt-get install ubuntu-deskto" it will install all the packages for a normal ubuntu install, but since you are going to remove gaim, not all the packages in the meta-package are installed so it will say that you will no longer have the ubuntu-desktop meta-package.

In short, go ahead and remove gaim, nothing else will be removed.

---

### Post by stchman on 2007-07-13
> **ireblue said:**
> i want to install pidgin, but was told i should uninstall gaim first..but when i try this it also selects ubuntu desktop to be removed also. how do i get around this.

thx

Let me know how Pidgin works.  I have been curious.  I wonder what features it has over Gaim?  Gaim seems to work very well.

---

