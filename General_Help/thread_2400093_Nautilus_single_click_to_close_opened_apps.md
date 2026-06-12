---
title: "Nautilus single click to close opened apps"
date: 2018-09-02
forum: General Help
---

### Post by michaelbr on 2018-09-02
I'm using Ubuntu 18.04, if I have an opened apps, it'll place an icon on the Nautilus side bar, if I make a single click on the icon, it'll become active and show up on my desktop, is there a way to make another single click to close it (just like in Windows)? TIA

---

### Post by deadflowr on 2018-09-02
Nautilus is the file manager, and I'm not sure you can put running apps in the sidebar.

I think you mean the dock on the desktop, which is Ubuntu Dock, or also known as dash-to-dock.
While there is a way to do it graphically,
(You need to install the dash-to-dock gnome-shell extension and then use the extension's settings feature; 
Ubuntu Dock, while based on dash-to-dock does not come with the settings feature, so you need to add the actual dash-to-dock app to get the feature)

You need to install two things, dash-to-dock and a program called Gnome Tweaks, which is installable through the software store.

Once you install both open Tweaks (what Gnome Tweaks will be called in Ubuntu's menu, then go to the sub section within Tweaks and then locate the dash-to-dock entry.

First things first, double check that dash-to-dock is turned off Ubuntu Dock would already be running and enabling the dash-to-dock entry will make two instances run,
so no need to do that. All you really need of the dash-to-dock extension is the settings feature.

To access the settings just click on the cog icon to the left of the on/off switch for the extension.
The setting for single click to minimize windows in somewhere in here.

Or,
you can use dconf/gsettings commands to set it like
```
gsettings set org.gnome.shell.extensions.dash-to-dock activate-single-window true
```
and optionally to dconf commands you can use dconf editor to do it as well,
just follow the same path laid out in the command above and you end at a toggle switch to turn the feature on or off.

Hope it helps

---

### Post by michaelbr on 2018-09-03
Thanks deadflowr for your answer, I'm sorry, I'm new to Linux, you're right, it's dock. I read [here]("https://askubuntu.com/questions/1031496/how-can-i-replace-default-ubuntu-dock-with-dash-to-dock-gnome-extension") that installing dash-to-dock, I'll have two docks, is it right? Do I have to delete the original one as stated in the post?

---

### Post by michaelbr on 2018-09-03
Thanks so much for your detailed explanation, it's working now.

---

