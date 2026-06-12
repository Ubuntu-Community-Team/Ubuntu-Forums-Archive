---
title: "Partial administration rights"
date: 2007-10-01
forum: General Help
---

### Post by TomMK on 2007-10-01
Is there a way to allow a user to install/uninstall only certain types of packages? I would like to allow one user to install games/educational packages from "add/remove" but don't want them to have any other "sudoer" rights. Is it possible?

Thanks.

---

### Post by bodhi.zazen on 2007-10-01
Well, that is the general idea with sudo.

See man sudoers ...

But, in terms of what they are installing, you would have to do that by limiting access to repositories ... like setting up a local repository for example ...

---

### Post by TomMK on 2007-10-01
Creating my own repo is a bit over the top for this instance I think. I've looked into sudoers and I don't think that allows me the control I want. Maybe this could be a future feature of Ubuntu? :)

---

