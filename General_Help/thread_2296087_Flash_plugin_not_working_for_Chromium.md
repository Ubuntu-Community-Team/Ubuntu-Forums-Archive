---
title: "Flash plugin not working for Chromium"
date: 2015-09-23
forum: General Help
---

### Post by fangorn2 on 2015-09-23
Hi,

I have Ubuntu 14.04 (64-bit) LTS and Chromium [COLOR=#303942][FONT=Ubuntu]Version 45.0.2454.85[/FONT][/COLOR].
Adobe flash plugin is installed and working fine with Firefox but not with Chromium.

I read at the following address that pepperflashplugin is deprecated and flash plugin should work with both browsers: [https://wiki.ubuntu.com/Chromium/Getting-Flash](https://wiki.ubuntu.com/Chromium/Getting-Flash)

Options for Canonical Partners software source is checked in Software Center.
flash plugin is not listed among Chromium plugins after typing about:plugins in Cromium address bar

What would you suggest to do?

Many thanks in advance for your help

---

### Post by kerry_s on 2015-09-23
in terminal:
sudo apt-get install pepperflashplugin-nonfree

i find chrome is much faster than chromium & flash is built in. also now chrome can run in the background & can also be preloaded to startup, so when you launch it, it opens instantly.

---

