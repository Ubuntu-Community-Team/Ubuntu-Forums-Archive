---
title: "How to uninstall just flash player on 16.04?"
date: 2016-05-21
forum: General Help
---

### Post by davetempleton on 2016-05-21
When I installed 16.04, I checked the box to install the restricted packages: mp3 codecs, flash, and other non-free stuff.

I would like to uninstall flash from my system, while still keeping the rest of the restricted/non-free stuff that was installed. Is there a way to just remove flash? And if I remove it, Chrome would still work with it's own internal flash plugin right? Thank yuo.

---

### Post by SeijiSensei on 2016-05-21
If you're talking about the Flash plugin for Firefox, you can remove that via Tools > Add-ons > Plugins.

---

### Post by davetempleton on 2016-05-22
I may or may not be talking about that. It seems to be a system-level thing, as I see a package flashplugin-installer that gets updated occasionally I think.

---

### Post by Impavidus on 2016-05-22
You can uninstall flashplugin-installer:```
sudo apt remove flashplugin-installer
```It's only a recommended package of ubuntu-restricted-addons, so it shouldn't force uninstallation of that metapackage, which in turn wouldn't make the other restricted packages autoremovable.

If I'm wrong, ubuntu-restricted-addons may get removed and the other restricted packages become autoremovable, but then you can mark them as manually installed:```
# To see which packages are affected
apt -s autoremove

# To mark them as manually installed
sudo apt-mark manual <package>
```

Chrome should still work with its build-in flash player.

---

### Post by davetempleton on 2016-05-25
This worked thank you. Didn't need to apt-mark anything.

---

### Post by Impavidus on 2016-05-25
Splendid. Could you mark this thread as solved? (Top of page, click thread tools, mark as solved)

---

