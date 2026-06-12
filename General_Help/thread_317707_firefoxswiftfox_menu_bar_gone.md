---
title: "firefox/swiftfox menu bar gone"
date: 2006-12-12
forum: General Help
---

### Post by dbbolton on 2006-12-12
my firefox menu bar is gone. i just upgraded from dapper to edgy, and it automatically upgraded firefox to 2.0; one extension that i used, called MenuX, isn't compatibile. 

i used it to replace the menubar with a button that had the menubar in a dropdown format as well as in the context menu, but now the entire menubar is gone.

what am i supposed to do now ?

---

### Post by altonbr on 2006-12-12
I've never used that add-on before, but can you right-click the very top bar (the one containing _F_ile  _E_dit  _V_iew  _H_istory, etc.) and you will see (at least) 2 options come up.

"Navigation Toolbar"
"Bookmarks Toolbar"

Your "Navigation Toolbar" is probably unchecked, so make sure to turn it back on. If that doesn't work, you'll have to wait for someone else to reply, sorry.

---

### Post by dbbolton on 2006-12-12
the bar that you told me to click is the one that's gone.


but thanks for the help anyhow.

---

### Post by dbbolton on 2006-12-12
edit.

i went to the addons site and installed a new one to get the addons box to pop up. i uninstalled menux, and i still dont have a menubar. thumbnail attatched.

---

### Post by dbbolton on 2006-12-12
i found an add on to take care of it 

compact menu

---

### Post by altonbr on 2006-12-12
Fixing an add-on problem with another add-on problem. Hmm, sounds like an old Operating System I used to use.

What about right click on whatever toolbar you have, and instead of click on

"Navigation Toolbar" or
"Bookmarks Toolbar", you click on
"Customize..."

Then select at the bottom right-hand corner, "Restore Default Set". Does that help?

---

### Post by dbbolton on 2006-12-13
i tried that earlier, to no avail.

---

### Post by altonbr on 2006-12-13
Do a "Mark for Complete Remove" in Synaptic Package Manager on Firefox. Then apply it. Then search for it again and tell it to "Mark for Installation" and then apply it (this is different from "Mark for Reinstallation" because it removes your configuration files). 

Then, of course, you will have to install and configure all your settings again, but this is the ONLY method I can think of.

Sorry that's it's such a dirty hack. Hopefully a Firefox zealot will come by shortly. If not, try my method :S.

---

### Post by dbbolton on 2006-12-13
i already thought of that, but a bunch of packages are dependent on firefox, like ubuntu-desktop

---

### Post by dbbolton on 2006-12-13
i actually prefer it like this, with the "drop down" menu, so it really isn't a problem. just a wry phenomenon.

---

### Post by altonbr on 2006-12-15
Actually ubuntu-desktop can be safely removed with no problem. I've been asked to get rid of it on several occations and everything worked out fine. If ubuntu-desktop was a dependancy of Firefox, wouldn't you think that would be a major problem (and a big no-no on the developers side?)? Not everyone uses Firefox.

---

### Post by altonbr on 2006-12-15
Um.. you might want to ignore what I just said, because it's purely anecdotal.

This is what Synaptic says about "ubuntu-desktop"
> The Ubuntu desktop system
This package depends on all of the packages in the Ubuntu desktop system

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.

Seriously though. I always remove it on a clean install of Ubuntu :|

---

