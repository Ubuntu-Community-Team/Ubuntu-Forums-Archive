---
title: "Gnome add/remove problem"
date: 2007-02-10
forum: General Help
---

### Post by HippyVanMan on 2007-02-10
Whenever I go - Applications > Add/Remove it starts up fine, and the window is visible (but greyed out) as well as a smaller window which is "checking available and installed applications" this window goes through all the different sets of application but when it rechessystem tools, it closes the whole program. I tried to google for help on this, but there wasn't anything of any help. I typed "sudo apt-get install gnome-app-install" into the terminal too, to try and reinstall the program, but it said the latest version was already installed so nothing was changed. I'm a linux newbie, but I'm out to learn and I'm not that stupid, so if the only solution is complex, it's still a solution, and I'll do it.

---

### Post by dcstar on 2007-02-10
> **HippyVanMan said:**
> Whenever I go - Applications > Add/Remove it starts up fine, and the window is visible (but greyed out) as well as a smaller window which is "checking available and installed applications" this window goes through all the different sets of application but when it rechessystem tools, it closes the whole program. I tried to google for help on this, but there wasn't anything of any help. I typed "sudo apt-get install gnome-app-install" into the terminal too, to try and reinstall the program, but it said the latest version was already installed so nothing was changed. I'm a linux newbie, but I'm out to learn and I'm not that stupid, so if the only solution is complex, it's still a solution, and I'll do it.

System-Administration-Synaptic Package Manager, search out the package and mark it for re-installation, then "Apply".

---

### Post by HippyVanMan on 2007-02-11
Reinstalling the package is not an option, only uninstillation and "complete uninstillation", but if I do this I have to delete gnome too. 
But I just uninstalled it, and then clicked install in teh package manager, but this failed because:

Package gnome-app-install is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source. Package gnome-app-install has no installation candidate.

I then completely removed it, and ran: sudo apt-get install gnome-app-install but it said exactly the same thing.

update: Now the terminal will not work, nor a program I downloaded called automatix, and firefox closes constantly. Is their anyway to repair my ubuntu instillation?

---

