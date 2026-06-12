---
title: "Annoying behavior with multiple instances of an application"
date: 2023-05-31
forum: General Help
---

### Post by lava2 on 2023-05-31
Using Ubuntu 22.04. It used to be that if you had multiple instances of an application open, you could simply left click on the application icon in the launcher and all the instances would pop up and you could pick the one you wanted. Now if you have multiple app instances, clicking on it brings up the last one you viewed, and to see the others you have to right-click to get a menu and then left click "all windows" which is completely annoying. Does anyone know how to switch the behavior back to a single left click to see all instances?

---

### Post by dragonfly41 on 2023-05-31
Is Alt+Tab not enough to tab through all sessions?
Or are you looking for equivalent of Alt+Tab .. but for a particular app?
If so I would try sume UI automation. I use different tools for that purpose
to create a custom script. I can offer ideas if Alt+Tab is not enough.

Actually, adding a note. My app launchers are seen in docky panels. when I have multiple app sessions open there are red dots against each launcher icon. I can right click, popup shows list of open app sessions.

---

### Post by deadflowr on 2023-05-31
Old default behavior was cycle-windows new default looks like focus-or-previews.
Try resetting it to the old defaults
```
gsettings set org.gnome.shell.extensions.dash-to-dock click-action cycle-windows
```

i thought this was a setting in Settings > Ubuntu Desktop, but I guess not, or maybe I simply did not look hard enough.

If that isn't what you want use the range option to see what other options it has
```
gsettings range org.gnome.shell.extensions.dash-to-dock click-action
```
and replace cycle-windows with which ever other option you want to look at.

Use reset to set it all back to the defaults
```
gsettings reset org.gnome.shell.extensions.dash-to-dock click-action
```
if you want to start over.

---

### Post by lava2 on 2023-05-31
> **deadflowr said:**
> Old default behavior was cycle-windows new default looks like focus-or-previews.
Try resetting it to the old defaults
```
gsettings set org.gnome.shell.extensions.dash-to-dock click-action cycle-windows
```

i thought this was a setting in Settings > Ubuntu Desktop, but I guess not, or maybe I simply did not look hard enough.

If that isn't what you want use the range option to see what other options it has
```
gsettings range org.gnome.shell.extensions.dash-to-dock click-action
```
and replace cycle-windows with which ever other option you want to look at.

Use reset to set it all back to the defaults
```
gsettings reset org.gnome.shell.extensions.dash-to-dock click-action
```
if you want to start over.

Ah, thank you! The answer I was looking for is:

```
 gsettings set org.gnome.shell.extensions.dash-to-dock click-action previews
```

---

### Post by mcshedden on 2024-03-12
Thank you so much for this! This has been playing havock with my ADHD. What a bizarre choice of default behaviour though!

---

