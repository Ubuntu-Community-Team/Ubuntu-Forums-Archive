---
title: "Minimal gnome desktop for ubuntu server?"
date: 2008-04-10
forum: General Help
---

### Post by njparton on 2008-04-10
Once Hardy is released, I'm going to do a fresh server install on my home NAS (originally set up using Gutsy desktop).
 
With my current setup I've managed to get away without a desktop for a while now and I've turned off gdm from starting automatically on reboot.
 
However, some tasks are easier with a desktop and I'd like to be able to start it up if needs be.
 
What packages would I need to install on top of the server installation to give me a gnome desktop, synaptic, and vino (or the hardy updated equivalent).
 
I connect to my NAS remotely using putty > ssh, or if needs be xming > vino on the rare occasion I need the desktop.
 
I _don't_ want anything else such as firefox, evolution, OOo etc etc. Just the real basics, hence I'm staying away from the ubuntu-desktop metapackage.

---

### Post by ramjet_1953 on 2008-04-10
I've heard some good things about this lightweight desktop.

[http://lxde.sourceforge.net/](http://lxde.sourceforge.net/)

Regards,
Roger :cool:

---

### Post by njparton on 2008-04-10
Thanks for the link.
 
I'm not really worried about it being particularly lightweight as 99% of the time it won't be running.
 
I'm basically looking for ubnutu desktop without 99% of the baggage but i'm not sure what the essential/minimum packages are.

---

### Post by njparton on 2008-04-10
Would the following be sufficient to get a working minimal gnome desktop?
 
```
sudo apt-get install xorg gdm gnome-core
```

---

