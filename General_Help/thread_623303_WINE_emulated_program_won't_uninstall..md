---
title: "WINE emulated program won't uninstall."
date: 2007-11-25
forum: General Help
---

### Post by m15hun on 2007-11-25
Hi folks,

I recently installed a trial version of MagicISO in wine which I needed to handle a file. I did what I needed to do and I now no longer need MagicISO but I can't seem to uninstall it. 

I tried Applications>Other>MagicISO Uninstall and a wizard opened and asked for an INSTALL.LOG which wasn't present and without which I can't seem to complete the uninstall. 

I also tried using the 'Uninstall' function within WINE itself but that doesn't even show MagicISO as installed any longer. The program won't run any longer either.

Does anyone know what's causing this problem?

Thanks,

=)

---

### Post by PeterJS on 2007-11-25
Wine is good, but it's not windows (yet). Which means that occasionally things like this don't work, but the fact that wine isn't windows also has a helpful advantage in cases like this, a clean un-install isn't required. Just go and hunt down the files that it installed and delete them. The program itself should be in ~/.wine/drive_c/<where_ever_you_put_it> and the menu entries in ~/.local/share/applications/wine/Programs.

---

### Post by m15hun on 2007-11-25
You, sir are a legend.

That did the trick immediately.

Thanks a million.

---

