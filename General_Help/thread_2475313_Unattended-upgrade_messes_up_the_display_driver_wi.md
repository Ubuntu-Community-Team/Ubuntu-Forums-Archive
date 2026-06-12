---
title: "Unattended-upgrade messes up the display driver without asking."
date: 2022-05-22
forum: General Help
---

### Post by mixuser on 2022-05-22
Imagine my surprise when I log in to my ubuntu desktop (20.04) and the resolution is set to 1024x768 (usually 4K). I go the display settings and there I find only this one resolution present. 

I never specifically enabled this update, nor I clicked allow etc when asked (as far as I remember).

However, I looked in apt history and presto: a bunch of "unattended upgrade with nvidia package this or that". What? I remember this kind of stuff from windows in the 90s - messing up a user's display with an "upgrade" no one asked for, but I digress.

So naturally I thought that perhaps it upgraded the nvidia driver (I use cuda on my machine and I use proprietary drivers). Nope, it switched to noveau driver too. 

This is unacceptable.

A modern OS should either not do this at all unless a user specifically ENABLES this kind of updates, or display a big fat warning "This update may mess up your system".

I expected better from ubuntu

Edit: To add to that. After I reenabled Nvidia driver I'm faced with "Sorry ubuntu has experienced and internal error" in Xorg. How do I revert this "unattended-upgrade" and more importantly disable it?

Regards,
L.

---

### Post by TheFu on 2022-05-24
If you enable unattended upgrades, you've tacitly approved them all.  YOU AGREED. 

If you just want automatic security upgrades, there's a different option for that.

I used to allow automatic upgrades ... then one removed the DBMS from a production system and people were really unhappy.  That was about a decade ago.  I manually run patches on Saturday mornings now.  Of course, even with manual patching, it is still up to me to actually read the package list to be upgraded and decide if I want that or not.

There is a GUI tool to disable automatic upgrades.  Sorry, I don't use the GUI for this.  Look in the _Ubuntu Desktop Guide_ for more. The guide you should find is dependent on the flavor of Ubuntu installed.  Google finds then all easily, at least for the LTS releases.

---

### Post by oldfred on 2022-05-24
How did you install nVidia drivers?
If you installed directly from nVidia, you have to, in effect, reinstall them with every kernel update.
It sounds like you got a new kernel, but not the nVidia drivers were not installed.

Ubuntu has permission from nVidia to add the drivers to its repository, so they automatically work with Ubuntu.
Then there are not normally issues with updates.

---

