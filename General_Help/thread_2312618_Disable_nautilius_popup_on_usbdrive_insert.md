---
title: "Disable nautilius popup on usbdrive insert"
date: 2016-02-05
forum: General Help
---

### Post by fugu2 on 2016-02-05
How can I disable nautilius from poping up when I insert a usbdrive, but I want to keep the auto-mounting feature for the usbdrive.

---

### Post by mc4man on 2016-02-06
graphically - 
Install dconf-editor
open dconf-editor, navigate to org > gnome > desktop > media-handling & set automount-open to off (screenshot
or in a terminal
```
gsettings set org.gnome.desktop.media-handling automount-open false
```

---

### Post by fugu2 on 2016-02-07
> **mc4man said:**
> ```
gsettings set org.gnome.desktop.media-handling automount-open false
```Yeah that was exactly what I was looking for. Thank you.

---

