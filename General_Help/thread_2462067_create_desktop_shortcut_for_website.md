---
title: "create desktop shortcut for website"
date: 2021-05-12
forum: General Help
---

### Post by T6&amp;sfpER35% on 2021-05-12
i'm trying to create a desktop shortcut to a certain website that needs to open in chrome.
i have done it before by just dragging the bookmark to the desktop,but if i do it now ,the site opens in brave which is my default browser.
how can i go about to let the shortcut open chrome?

xubuntu , so XFCE desktop

thanks

---

### Post by Holger_Gehrke on 2021-05-12
When you drag an URL to the desktop you're creating a .desktop file with 'Type=Link'. Those always open in your default browser. If you want to open a link in a specific, non-default browser you have to create a .desktop file that starts that browser with that URL, so you need a .desktop file with 'Type=Application' and an 'Exec=' line starting your browser with the URL. The easiest way I can think of of doing this is to copy the menu item for this browser to the desktop by dragging it from the menu to the desktop then right clicking on the desktop item you just created, choosing 'Edit Launcher' (or something like that; I'm retranslating from German to English ...) from the context menu, adding the URL to the command in the form and saving.

Holger

---

