---
title: "Japanese Input - using uim-anthy instead of Scim"
date: 2006-10-30
forum: General Help
---

### Post by Grimmy on 2006-10-30
Just installed a fresh install of Edgy and am trying to get Japanese Input working.   My girlfriend is used to using UIM-Anthy via the Gnome Applet for Japanese input, she doesn't like the Scim interface that seems to be enabled by default (it works differently apparently?)

I installed Uim, Uim-anthy and the gnome applet and it works fine when I try to use it in my account (GB-English) and it works ok in her account (in GB-English) but I can't get it to work when she logs in with Japanese set as the language?

How can I disable Scim... I've tried fiddling with the options, but I still just get an "X" in the Gnome Applet.

I've tried using "im-switch uim_anthy" but it says there is no uim_anthy config file.

Any suggestions?

---

### Post by Grimmy on 2006-10-30
I logged off and back in, and now it seems to be working. (Not sure what has changed)

It works fine in Firefox and Open Office, but if you hit ctrl+space in Gedit it crashes.

---

### Post by kaffekopp on 2006-12-01
I couldn't get used to scim either, so what I did was I uninstalled the following in synaptic:
scim
scim-gtk2-immodule
And then install the following packages:
uim
uim-anthy
uim-applet-gnome

Afterwards, I added the uim applet by right-clicking one of the gnome panels and selecting "add to panel" -> "Uim applet"

I'm not sure if this is what you meant by "disabling scim", but it does disable it, for sure... 

Anyway, this has worked perfectly for me.

(edited)
oops, just realised that after I installed edgy, I didn't actually uninstall scim, so I guess that's not it, then...

---

### Post by legolas on 2006-12-01
What don't you guys like about scim?

---

