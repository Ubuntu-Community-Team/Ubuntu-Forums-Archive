---
title: "A few gusty problems (fresh install)"
date: 2007-10-20
forum: General Help
---

### Post by Ludford on 2007-10-20
I have a few problems with gusty after a fresh install.

1. I can't access compiz settings, theres no button in the menu for it.

2. No boot splash even after changing usplash.conf settings to my resolution

3. add/remove dosn't work, when trying to install a program it tells me I need to reload the list and I should have an active internet connection. 


Any ideas?

---

### Post by ddrichardson on 2007-10-20
> **Ludford said:**
> 3. add/remove dosn't work, when trying to install a program it tells me I need to reload the list and I should have an active internet connection.
Check System->Administration->Software Sources and make sure the Downloadable from Internet options are ticked.

I had the same problem in Gutsy, for some reason if there is no active internet connection during installation it disables the online sources.

---

### Post by Stemp on 2007-10-20
> **Ludford said:**
> 1. I can't access compiz settings, theres no button in the menu for it.

install compizconfig-settings-manager

---

### Post by rainwalker on 2007-10-20
[quote1. I can't access compiz settings, theres no button in the menu for it.[/quote]
If you're referring to CompizConfig Settings Manager (CCSM), you have to install it through Synaptic (search for "compizconfig-settings-manager")

---

### Post by Toddy on 2007-10-20
After changing your usplash.conf settings, ensure that you update with:

```
sudo update-usplash-theme usplash-theme-ubuntu
```

---

