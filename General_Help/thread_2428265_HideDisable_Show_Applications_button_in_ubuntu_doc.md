---
title: "Hide/Disable Show Applications button in ubuntu dock"
date: 2019-10-01
forum: General Help
---

### Post by rCXer on 2019-10-01
Is there a way to disable or hide the "Show Applications" (nine dots icon) button in the Dock?

---

### Post by deadflowr on 2019-10-02
You can set it to off with this gsettings command
```
gsettings set org.gnome.shell.extensions.dash-to-dock show-show-apps-button false
```

Graphically you can toggle it off in dconf editor.

Alternatively there's probably a gnome shell extension that does it too.

---

