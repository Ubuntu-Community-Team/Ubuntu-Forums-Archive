---
title: "Gaim/Pidgin encryption problem"
date: 2007-09-03
forum: General Help
---

### Post by GreenDevil on 2007-09-03
Today I made the jump from Gaim to Pidgin, all was going well until I went to make sure the encryption plugin was working, and it wasn't even showing up in the list.

After various reinstalls, and manual installs of the plugin itself, I am left without it still.

Running pidgin in debug mode, I get the following error with the encryption plugin:

(18:02:26) plugins: /usr/lib/purple-2/encrypt.so is not loadable: undefined symbol: gaim_core_get_version
(18:02:26) plugins: /usr/lib/purple-2/encrypt.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?


I'm running Ubuntu 7.10.

Does anyone have any ideas as to how to get this working?

Much appreciated :)

---

### Post by anjilslaire on 2007-10-13
I've been wanting this, too. Any resolution to get encryption into pidgin?

---

### Post by GreenDevil on 2007-10-13
Yes, actually I found a solution and forgot to post it here.

There's an installable package found at:
[http://packages.ubuntu.com/gutsy/net/pidgin-encryption](http://packages.ubuntu.com/gutsy/net/pidgin-encryption)

Just download the .deb for your architecture and install. There may be one or two dependencies it needs, but those are easy to find in synaptic.

---

### Post by anjilslaire on 2007-10-13
Cool, thanks!

---

