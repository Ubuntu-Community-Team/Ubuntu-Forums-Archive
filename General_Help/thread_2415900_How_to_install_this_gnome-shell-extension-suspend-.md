---
title: "How to install this: gnome-shell-extension-suspend-button"
date: 2019-04-02
forum: General Help
---

### Post by swarup on 2019-04-02
Using 18.04. [Here]("https://www.linuxuprising.com/2018/06/how-to-access-suspend-button-in-ubuntu.html") is a nice, short article on How To Access The Suspend Button In Ubuntu 18.04 (Gnome Shell). There they also provide a link to a program which adds a permanently visible Suspend button in the Gnome Shell user menu. But I cannot seem to figure out how to get it installed. I downloaded the folder, opened a terminal window, changed directory (cd) to the folder, and gave the requested commands of make, and make install. But the terminal window did not accept the commands. [Here]("https://github.com/laserb/gnome-shell-extension-suspend-button") is the page for this GNOME Shell Extension Suspend-Button. Should be so simple. Please help! Thanks.

---

### Post by deadflowr on 2019-04-02
Install the package chrome-gnome-shell then check that that your browser has the Extension/Addon: "Gnome Shell Integration" enabled,
and then you'll get an on/off toggle on the extension's web page.
Toggling it to on will prompt an Install or cancel box.

The addon works in Firefox and Chrome/Chromium.
Not sure what others is works in though.

The extension installs locally to ~/.local/share/gnome-shell/extensions.

---

### Post by swarup on 2019-04-02
I installed the package chrome-gnome-shell and confirmed that my browser has the Extension/Addon: "Gnome Shell Integration" enabled. Up to there it is fine.

But I don't see any on/off toggle on the extension's web page. I went to the web page, but no on/off toggle that I can see there...

---

### Post by deadflowr on 2019-04-02
You don't see this?
[ATTACH=CONFIG]282925[/ATTACH]

Edit: on this page
[https://extensions.gnome.org/extension/826/suspend-button/]("https://extensions.gnome.org/extension/826/suspend-button/")

---

### Post by swarup on 2019-04-02
Wow, that is great. Worked like a charm.
But when you said to go to their web page, I went here: [https://github.com/laserb/gnome-shell-extension-suspend-button](https://github.com/laserb/gnome-shell-extension-suspend-button)
The page you've given me a link to is the web page of extensions.gnome.org.

---

