---
title: "How to remove Landscape Service and Online Accounts from 13.04 Control Center"
date: 2013-08-04
forum: General Help
---

### Post by elundmark on 2013-08-04
Running this command removes the package that shows the little button. If you're like me and didn't even know **what** "Landscape Service" was before, it's worth saving the space, especially since the Control Center gnome-control-center can grow **too tall** on smaller screens.
```
$ sudo apt-get remove landscape-client-ui-install
```

If you want to remove "Online Accounts" (just the icon, not the functionallity), run this command to save even more space:
```
$ sudo mv /usr/share/applications/gnome-credentials-panel.desktop /usr/share/applications/gnome-credentials-panel.desktop-inactive
```

To reverse the effects of these 2 commands, run this:
```
$ sudo mv  /usr/share/applications/gnome-credentials-panel.desktop-inactive /usr/share/applications/gnome-credentials-panel.desktop; sudo apt-get install landscape-client-ui-install
```

---

