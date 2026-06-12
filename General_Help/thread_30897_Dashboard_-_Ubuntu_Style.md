---
title: "Dashboard - Ubuntu Style"
date: 2005-04-30
forum: General Help
---

### Post by oars on 2005-04-30
OK, Folks, here's the deal.

I think Dashboard is way cool and want something similar in Ubuntu.

Here's what I have been doing.  

1.  I set up  new workspace and titled it dashboard.
2.  System-->Preferences-->Keyboard Shortcuts and changed swtching to that workspace to he F12 key.
3.  Now I am at the point where if I had widgets to run, I could asily swtch to them without having them clutter my desktop by hitting F12.
4.  As far as widgets go, I am trying to find the best way to implement something similar, and right nw am working with gDesklets.  HERE IS WHERE I AM LOOKING FOR OTHER OPTIONS.  gDesklets is cool and all, except it displays on all of my workspaces and is limited by the senso/display issue in the latest version.  Are there anyways to resolve these issues?

Can Desklets be displayed on only one workspace?
Is there another way to set up a widget sstem on an individual desktop?
Is there an option that is better than either of these?

Hopefully, there is a way to make a Dashboard-like system in Ubuntu.

---

### Post by Psquared on 2005-05-02
I don't know about Dashboard, but I have played around with Gkrellm and gDesklets and the latter is much more usable. I run the Weather sensor and email notification.

As far as I can tell there is no way to make it not run on all desktops. I have not had a "sensor" problem yet -- but I don't run the temp, network and hddrive monitors.

---

### Post by tube013 on 2005-05-02
I don't know if you read planet.gnome.org or not, but there was a recent post by Miguel de Icaza in which he briefly talks about web applets and references dashboard.  I don't know the specifics but if you click through on one of his links, it looks and then follow that a bit, it looks to me like all dashboard is is a full screen html rendering engine, and the widgets are written in a new tag of html called canvas.  I'm not sure it's that simple but anyway, I wonder if with some work the dashboard widgets could be used on other platforms.  Seems to be what Miguel was hinting at.

---

