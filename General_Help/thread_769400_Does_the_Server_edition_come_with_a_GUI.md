---
title: "Does the Server edition come with a GUI?"
date: 2008-04-26
forum: General Help
---

### Post by denzilla on 2008-04-26
Just wondering how the Server edition is presented after installation? Is it CLI from the get go or does it include Gnome?

---

### Post by Monicker on 2008-04-26
Its cli. No gui.

---

### Post by scragar on 2008-04-26
nope, it is possible to install it though:
```
apt-get install ubuntu-desktop
```

I wouldn't recommend it though, since the whole advantage of server versions are that they are minimal installs.

---

### Post by denzilla on 2008-04-26
Anyway to just install Gnome and some apps that I choose?

---

### Post by scragar on 2008-04-26
```
sudo apt-get install ubuntu-minimal
``` then, that's the absolute minimal install you can have.

---

### Post by MobiusNZ on 2008-04-26
afaik there isn't much difference between "server" and "desktop" installs - they both use the same repositories to install their software, and install the same verisons of said software. They just come with different initial package selection; most servers don't have monitors, so gui's are pointless. Conversely, most desktops don't run DNS servers.

With that in mind, if you really want a gui, you can install the desktop edition and then install the server packages you need over the top.

Or, you can install the gui on top of the server edition. Rather than gnome, I'd suggest something like xfce - its much more lightweight. Be aware you'll probably have to do a lot of tinkering, as there is no "server with gui" package.

---

