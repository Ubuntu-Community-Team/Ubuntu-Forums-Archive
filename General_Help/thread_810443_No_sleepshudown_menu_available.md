---
title: "No sleep/shudown menu available"
date: 2008-05-28
forum: General Help
---

### Post by bobatomik on 2008-05-28
I currently work on Ubuntu 8.04 Hardy Heron (Gnome)
It appears that my close/quit button in the upper right does not behave normally. 

When I click on it, it somehow restart X (or logout if you prefer).
Moreover, in the System menu, there is only Quit avaible.

I recently had a problem saying that the default configuration for the gnome-power-manager did not load correctly; so I dpkg-reconfigure it, which solve that problem. I know the sleep / quit / etc. it somehow linked to the acpi, so that power manager, but I even totally reinstalled it (apt-get install --reinstall) and it still doesn't work.

By the way, it is not the sleep function that is unavailable, because when I set in power preferences to map my shutdown button as the Sleep button, it sleep/wake wonderfully. I also tried to replace the applet thingy. 

Any ideas?

---

### Post by LeoSolaris on 2008-05-28
I know this is a strange place to put this, but it is in Computer->Administrations->Login Window. Go to the local tab, then check "Show Actions Menu" and "Include Hostname chooser (XDMCP) menu item".

See if that does it. I had unchecked them once to see what they did and it took me a long time to realize that all it did was remove functions from my shutdown menu.

I wish you luck, and if that doesn't solve it, I am not sure what the answer will be. That's the only solution I know to a problem even remotely similar to your's.

Maybe a sudo apt-get install --reinstall ubuntu-desktop  ?

Leo

---

### Post by bobatomik on 2008-05-28
Non, ni un ni l'autre
Il était déjà coché, jai essayé de le cocher/décocher, sans succès.

En passant, je ne crois pas que reinstall ubuntu desktop puisse changer qqch, ce paquet ne contient pas de configuration (à ce que je sache), c'est plutôt un paquet installeur (comme openoffice) qui ne fait que inclure les autres en dépendances

---

### Post by LeoSolaris on 2008-05-28
French class was a long time back for me friend, sorry. At least I do still recognize the language, and a few of the words.

---

### Post by LeoSolaris on 2008-05-28
After looking it over, it appears that what you're saying is that neither solution I proposed worked and it had to do with the strange update of openoffice.org. I ran into a few oddities myself. My system simply would not let me use the Update Manager to do the updating, so I went to Synaptic and did an update from there. I did connect to the main server first, then did the update. It removed a few things relating to Openoffice, and I had to reinstall openoffice-core, but it didn't cause me to lose my power buttons. It's still not all there, because it will not let me install a part of OOo dealing with Java due to unresolved dependancies.

Try using synaptic to purgel the gnome-power-manager package, then re-install it. This may cause it to be unstable, but for a short time it should be running in memory. Just don't shut it off with that package uninstalled. It could cause some serious issues.

---

