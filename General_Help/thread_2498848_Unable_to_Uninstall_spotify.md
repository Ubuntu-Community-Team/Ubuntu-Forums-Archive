---
title: "Unable to Uninstall spotify"
date: 2024-07-01
forum: General Help
---

### Post by furrypaws on 2024-07-01
Hi guys I can't seem to Uninstall spotify using the snap store any other ways come to mind?

---

### Post by guiverc on 2024-07-01
You haven't provided your Ubuntu product (Core? Server? Desktop?), nor release, nor critically how it was installed as that dictates the best method of removal.

If you installed the *snap* package, ie. a search here finds 

```

guiverc@d7050-next:/de2900/ubuntu_64$   snap search spotify
Name           Version               Publisher               Notes  Summary
spotify        1.2.37.701.ge66eb7bc  spotify&#10003;                -      Music for everyone
...

```

I'd remove it with a  (`sudo` isn't required for this; but I'd use it anyway)

```

sudo snap remove spotify

```

If however you installed a *deb*, *appimage*, *flatpak* or compiled from source, the method will differ.

---

