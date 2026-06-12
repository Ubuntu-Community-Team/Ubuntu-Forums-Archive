---
title: "save to x configuration file - nvidia settings"
date: 2008-03-31
forum: General Help
---

### Post by J. Baker on 2008-03-31
I'm trying to save my nvidia settings using the "save to x configuration file" button in the "nvidia x server settings" but I get the following error...

"Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'."

Currently running ubuntu 8.04

---

### Post by forestpixie on 2008-03-31
open it from terminal with gksudo nvidia-settings then it will work

---

### Post by process91 on 2008-03-31
Hmm... it seems like you're not running this as root so you probably will not be able to overwrite the standard xorg.conf file either, but running the following command won't hurt anything either.

This command will move your current backup file and get you past that error

```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf.backup-OLD
```

EDIT: The post above is correct, in that you should run

```
gksudo nvidia-settings
```

---

### Post by J. Baker on 2008-03-31
Thanks! I think that did it. ;)

---

