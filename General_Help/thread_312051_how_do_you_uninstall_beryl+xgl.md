---
title: "how do you uninstall beryl+xgl"
date: 2006-12-03
forum: General Help
---

### Post by mark076h on 2006-12-03
i dont get this i installed beryl and xgl and it worked great but then i restarted my computer and it stopped working gives me some crap about "NO MANAGEABLE SCREENS FOUND ON DISPLAY"

i want to completely delete all the beryl and xgl stuff and startover how do i do this?

---

### Post by xopher on 2006-12-03
Well you could find the guide you followed when installing Beryl/XGL -- then follow it, backwards. That should do it. ;)

---

### Post by syxbit on 2006-12-03
i had this problem
i booted into the terminal "hit CTRL-ALT-F1"
```
sudo aptitude remove beryl beryl-manager emerald-themes beryl-settings
```

---

### Post by blindmist on 2006-12-03
^^^ i did that once and it removed my xserver for some reason.

---

### Post by strabes on 2006-12-03
you'll also have to delete the xsession & startxgl script that you made in the process. also remove the entries in the startup programs tab of gnome-session-properties.

might I recommend #ubuntu-xgl for support? It's a great resource.

---

### Post by Rodneyck on 2006-12-03
You can also use Synaptic and uninstall there.

---

