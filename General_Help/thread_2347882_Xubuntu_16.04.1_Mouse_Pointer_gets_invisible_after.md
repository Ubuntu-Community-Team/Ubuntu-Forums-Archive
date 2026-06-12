---
title: "Xubuntu 16.04.1 Mouse Pointer gets invisible after waking from suspend"
date: 2016-12-29
forum: General Help
---

### Post by arashk on 2016-12-29
[SIZE=3]Hello
On Xubuntu 16.04.1 after waking up from suspend mode, mouse pointer gets invisible although the mouse itself works.
Do you know of any effective solution?[/SIZE]

---

### Post by Impavidus on 2016-12-29
That was a known bug for those using intel graphics, but it should have been fixed a short while after 16.04.1 was released. Hitting ctrl-alt-F1 followed by ctrl-alt-F7 would bring it back. Have you installed all updates?

---

### Post by arashk on 2016-12-29
> **Impavidus said:**
> That was a known bug for those using intel graphics, but it should have been fixed a short while after 16.04.1 was released. Hitting ctrl-alt-F1 followed by ctrl-alt-F7 would bring it back. Have you installed all updates?

[SIZE=3]I had tried ctrl-alt-F1 followed by ctrl-alt-F7, but nothing happened. [/SIZE]

[SIZE=3]I do not have enough internet traffic to install all updates. How can **only the update for this bug** be downloaded?

It looks as if the following links are related to this bug and to the needed update:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604)
[https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/2:2.99.917+git20160325-1ubuntu1.2](https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/2:2.99.917+git20160325-1ubuntu1.2)
[/SIZE][SIZE=3]1. How can the update be downloaded?
2. How can it be installed?[/SIZE]

---

### Post by Impavidus on 2016-12-30
The best tool to install only the updates you want is synaptic. You may want to install that. There you reload the package database, look at the available upgrades and mark the ones you want for upgrade. I recommend you install at least all security upgrades. For this particular bug (and I'm not 100% sure this is your problem), it means upgrading xserver-xorg-video-intel. This could in turn require other upgrades. Click Apply and wait for the upgraded packages to download and install.

---

