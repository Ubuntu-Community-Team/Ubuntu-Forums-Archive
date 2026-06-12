---
title: "Installing a package while excluding some of it's dependencies"
date: 2013-06-28
forum: General Help
---

### Post by Ranko Kohime on 2013-06-28
Here is an interesting little thing I've run across.  These days, since I don't use the majority of the software in the default desktop image, I've taken to building my install from the ground up using the Minimal ISO.  Which means I end up doing a lot of apt-get'ing.

When installing Byobu, for example, it pulls in both Screen and Tmux, though I only use Tmux now.  Screen can then be purged, without removing Byobu, and without it being broken.

The same behaviour is present with Network Manager and system-config-printer-*, these are dragged in with NM, and can be removed without penalty at a later time.

What's more, the latter show up in the Synaptic category "Installed (auto removable)", meaning they were never even in use.

Yeah, I'm a little OCD.  :P

---

### Post by Cheesemill on 2013-06-28
They're not dependencies but recommends. By default Ubuntu installs all recommended packages as well as dependencies.
[http://packages.ubuntu.com/raring/byobu](http://packages.ubuntu.com/raring/byobu)

If you don't want to install these then you can use the following command to install packages...
```
sudo apt-get install --no-install-recommends byobu
```

---

### Post by Ranko Kohime on 2013-06-29
Ah, I wasn't aware that apt-get installed recommends by default.  Thanks.  :)

ETA: to be clear, the behaviour I'm used to when using apt-get is that it shows recommends, but does not automatically install them, when installing packages with fewer dependencies, and only 1 or 2 recommends.

---

