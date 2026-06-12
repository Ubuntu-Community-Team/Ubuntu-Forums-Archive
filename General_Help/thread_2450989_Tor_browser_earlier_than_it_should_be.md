---
title: "Tor browser earlier than it should be"
date: 2020-09-24
forum: General Help
---

### Post by klundermann on 2020-09-24
When attempting to install a routine update of the Tor browser, I get an error box reading "The version of Tor Browser you have installed is earlier than it should be, which could be a sign of an attack!"  The installation seems never to finish.

I've waited 24 hours and tried again, hoping there was some problem with the updated package that would be resolved.  No luck.

In Synaptic, I've uninstalled all tor packages and tried to re-install.  No change.

Any ideas?

---

### Post by dinkidonk on 2020-09-24
It is not recommended to install Tor browser from repos, [download Tor as an archive]("https://www.torproject.org/download/") from the Tor project instead and follow the [installation instructions]("https://tb-manual.torproject.org/installation/").

---

### Post by klundermann on 2020-09-25
I should have been clearer.  I am trying to install the Ubuntu package which, as I understand it, downloads Tor from the Tor project, installs and creates a quick-launch button.  The description is:

[COLOR=#008000]Tor Browser Launcher is intended to make the Tor Browser Bundle (TBB) easier to maintain and use for GNU/Linux users. torbrowser-launcher handles downloading the most recent version of TBB for you, in your language and for your architecture. It also adds a "Tor Browser" application launcher to your operating system's menu.

When you first launch Tor Browser Launcher, it will download TBB from [https://www.torproject.org/](https://www.torproject.org/) and extract it to ~/.local/share/torbrowser, and then execute it. Cache and configuration files will be stored in ~/.cache/torbrowser and ~/.config/torbrowser. Each subsequent execution after installation will simply launch the most recent TBB, which is updated using Tor Browser's own update feature.[/COLOR]

---

