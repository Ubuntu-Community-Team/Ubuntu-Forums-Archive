---
title: "Removing stuff youv'e apt-get"
date: 2007-05-08
forum: General Help
---

### Post by matty13 on 2007-05-08
Ok i installed this ntfs-config to try get ntfs write/readable but i don't want it now how can i remove it?

I checked add/remove and it didn't come up, how can i remove stuff i have apt-get, and i mean remove fully.

---

### Post by taurus on 2007-05-08
```
sudo apt-get --purge remove **package_name**
```

---

### Post by matty13 on 2007-05-08
Thanks.

---

### Post by LuisGMarine on 2007-05-08
I always like doing it from Synaptics.  Although I'm not sure how completely it would remove it. But its   a start:
[B][SIZE="2"]
( Start ) > System > Administration > Synaptics Package Manager
[/SIZE][/B]
From there on the top of the window there is a button that says " Search ", hit that button and type in the packaged that you installed.  

Once the package comes up in the list, right-click on it, and selced " Mark for Complete Removal "  I think it might give you a little warning dialog that the configuration files are also going to be deleted, just say 'OK'

After you have that done, just hit the 'Apply' button at the top, and you are ready to go.

Good Luck

---

### Post by Nythain on 2007-05-08
does synaptic give the --purge option... i've never actually used it to install or remove software but i might consider it when im feeling lazy from now on if i know i can --purge with it too

---

### Post by mcduck on 2007-05-08
> **Nythain said:**
> does synaptic give the --purge option... i've never actually used it to install or remove software but i might consider it when im feeling lazy from now on if i know i can --purge with it too

yes, that's the 'Mark for Complete Removal'. The normal remove is 'Mark For Removal'

---

