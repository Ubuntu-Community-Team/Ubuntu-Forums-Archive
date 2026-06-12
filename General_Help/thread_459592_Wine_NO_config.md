---
title: "Wine NO config"
date: 2007-05-30
forum: General Help
---

### Post by mouseboyx on 2007-05-30
Wine does not save my config when i reboot xubuntu. wine version 9.33 there was nothing that signaled this change it just started happening one day.

---

### Post by MoLE on 2007-06-07
Are you using the winecfg tool to configure wine?  Don't forget you can actually set different windows versions for different programs, and this may be confusing the issue?

First try running ```
wineprefixcreate
```, as this should repair the wine configuration so that it is sane.

If that doesn't work, then a quick solution is to delete your .wine directory and reconfigure wine with winecfg.

---

