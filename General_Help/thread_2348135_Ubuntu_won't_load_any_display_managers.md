---
title: "Ubuntu won't load any display managers"
date: 2017-01-01
forum: General Help
---

### Post by tsjswimmer on 2017-01-01
[CENTER][COLOR=#3F005E]
  [/COLOR][/CENTER]

Hello, good Ubuntu people.

I'm having a problem with a new installation of 16.04 Xenial Xerus (x64), which I installed from the Ubuntu-Minimal CD. For some reason, my default display manager (currently MDM) refuses to load automatically. I can start it manually with **systemctl start mdm**, but I can't get it to load automatically. My computer doesn't give my any errors, it just stops showing the plymouth splash screen, and instead shows a static screen of daemons that have been started until I manually switch to a TTY screen. I suspect the reason is that there's no **/etc/systemd/system/display-manager.service** file. IDK why this file doesn't exist, I certainly didn't delete it. Is it included in some package that somehow didn't get installed?

So, if anyone can tell me how to get my system's default display manager running automatically, I would appreciate it.

PS: I could enable MDM with **systemctl enable mdm**, but I would rather not, since I might switch back to LightDM in the future (I installed MDM from a nightly/development PPA, so there might be unrelated bugs), and would rather be able to use **dpkg-reconfigure** to do so (I'm so used to 14.04, I'd probably forget to disable MDM and enable LightDM. I would then spend an embarrassing amount of time trying to figure out why MDM is running instead of LightDM). I've previously tried making LightDM the default manager, but that didn't help at all.

---

