---
title: "Ubuntu + LXDE = auto login headaches?"
date: 2013-01-14
forum: General Help
---

### Post by Roasted on 2013-01-14
I installed Ubuntu 12.04 along with LXDE. I'm having some trouble getting it to auto login. I edited /etc/lightdm/lightdm.conf according to the documentation I read but nothing is happening... it still just goes to Unity as it wishes. Some folks I spoke to gave the impression that what I'm doing *is* correct for Lubuntu, which makes me wonder why it's not flying here with using LXDE on top of Ubuntu. Any ideas?

EDIT - I just noticed if I log in to Unity, go to User Accounts, set my user to auto log in, log out, log in to Lubuntu, then reboot, it'll auto login. It seems as if Unity somehow has a higher power over auto login features than LXDE does. Is this typical behavior?

EDIT II - I'm not really sure what would have been different, but I was sitting here on my laptop thinking I had to have missed something. I installed Ubuntu 12.04 in a VM and then Lubuntu-desktop on top of it. I did the same steps I did before and it now works. All I did was edit /etc/lightdm/lightdm.conf and add:

autologin-user=jason
autologin-user-timeout=0

Then save and reboot. I thought perhaps I forgot the timeout line on the regular system I was working on when I posted this, so for kicks I removed it, saved, rebooted... but no difference. Either way, it auto logs in just fine, but I'm not sure what I did wrong. I've since formatted it to a regular instance of Lubuntu since that was kind of my original plan anyway.

---

