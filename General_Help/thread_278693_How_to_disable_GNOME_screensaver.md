---
title: "How to disable GNOME screensaver?"
date: 2006-10-16
forum: General Help
---

### Post by CaptSammy on 2006-10-16
Every time my screensaver kicks off I get logged out to the gdm. I am running Dapper with gnome and of course the screensaver that I cant get rid of (when I try to uninstall it, it uninstalls Gnome also). When I start the graphical interface to the screensaver it logs me out immediately as well as soon as it starts to open. Probably a driver issue with my NVidia card, but is there a way to turn off the screensaver from a .conf file or some such so I can use my system?

---

### Post by Sef on 2006-10-16
Try this:

System > Preferences > Screensaver

then unclick the box that says 'Activate the screensaver when session is idle.'

---

### Post by qntgeek on 2006-10-16
> **CaptSammy said:**
> Every time my screensaver kicks off I get logged out to the gdm. I am running Dapper with gnome and of course the screensaver that I cant get rid of (when I try to uninstall it, it uninstalls Gnome also). When I start the graphical interface to the screensaver it logs me out immediately as well as soon as it starts to open. Probably a driver issue with my NVidia card, but is there a way to turn off the screensaver from a .conf file or some such so I can use my system?


Default location of configuration file:
/etc/X11/app-defaults/XScreenSaver

---

### Post by CaptSammy on 2006-10-17
Well I cant use the first recommendation, because as I stated in the initial problem I cant access the graphical screensaver interface without getting emmediately logged out.
The second method actually turned out to be a soft link file that points to XScreenSaver-gl, I deleted and recreated a soft link to XScreenSaver-nogl, same problems.
So I figured I would update the system, which updated the kernel. The new kernel wont boot at all, just a bunch of gibberish and error codes, probably because that kernel isnt configured for the NVidia drivers?
This is REALLY frustrating me, UBUNTU seems to be trying it's best to mimic Microsoft, and in so doing building a system that the user cant configure, altho Mr Torvald I think has blamed this on GNOME general. Anyone know a work around for this? Do I need to switch to K?
Thanks, and sorry for sounding so grumped out, but a thing as simple as removing the screensaver is turning out to be a nightmare.

---

### Post by 23meg on 2006-10-17
[QUOTE=CaptSammy]This is REALLY frustrating me, UBUNTU seems to be trying it's best to mimic Microsoft, and in so doing building a system that the user cant configure, altho Mr Torvald I think has blamed this on GNOME general.[/QUOTE]In your case neither Ubuntu nor GNOME is to blame; if you get logged out when a screensaver starts, there's something obviously very wrong with your configuration to begin with; this is not a normal use case. To fix it temporarily you can easily disable gnome-screensaver:```
sudo killall gnome-screensaver
gconftool-2 --type boolean -s /apps/gnome_settings_daemon/screensaver/start_screensaver false
```
or if that doesn't work, a less elegant one:
```
sudo chmod -x /usr/bin/gnome-screensaver
```

---

### Post by CatKiller on 2006-10-17
> **CaptSammy said:**
> Every time my screensaver kicks off I get logged out to the gdm. I am running Dapper with gnome and of course the screensaver that I cant get rid of (when I try to uninstall it, it uninstalls Gnome also). When I start the graphical interface to the screensaver it logs me out immediately as well as soon as it starts to open. Probably a driver issue with my NVidia card, but is there a way to turn off the screensaver from a .conf file or some such so I can use my system?

```
gconf-editor
```
/apps/gnome-screensaver
uncheck idle_activation_enabled

Other things that you could do for a more permanent fix, in no particular order:
Uninstall the 3D screensavers through Synaptic
Use gconf-editor to try a different screensaver each time to see which one causes the logout, and disable that one by removing it from the list
Switch from using gnome-screensaver to using xscreensaver, in case it's a problem with the program rather than any particular screensaver.

Hope this helps.

---

### Post by CaptSammy on 2006-10-17
gconf-editor did the trick, you guys rock! Wish I had known of that little tool a long time ago.
Thanks again

---

### Post by CatKiller on 2006-10-17
> **CaptSammy said:**
> gconf-editor did the trick, you guys rock! Wish I had known of that little tool a long time ago.
Thanks again

No worries. It's actually called "Configuration Editor" on the menu, but it's hidden by default I believe. If you right-click on the menu and select Edit Menus, you can put a tick next to Configuration Editor in the System Tools sub-menu.

I find it quicker to do Alt-F2 gconf-ed<right><Enter> though.

---

### Post by 23meg on 2006-10-18
As my post illustrates, you can also use gconftool-2 to tweak gconf entries from the command line (useful for such emergencies) or in a bash script.

---

