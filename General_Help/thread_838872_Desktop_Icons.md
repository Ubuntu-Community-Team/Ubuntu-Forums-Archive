---
title: "Desktop Icons"
date: 2008-06-23
forum: General Help
---

### Post by mishathegoat on 2008-06-23
Hey everyone,

I just install a fresh copy of Ubuntu Desktop 7.10
I opened gconf-editor, navigated to apps>nautilus>desktop, and unchecked volumes_visible. But they're still visible (and functional) on my desktop!

Does anyone have any advice to offer?

Any help is appreciated..

---

### Post by fooman on 2008-06-23
have you tried logging out (alt-ctrl-backspace) and back in again?

---

### Post by mishathegoat on 2008-06-23
Yes, I even rebooted and it does the same thing..

---

### Post by molotov00 on 2008-06-23
Are you opening the editor as sudo/root? Maybe your changes aren't saving bc you don't have permission. I'm not entirely sure as I'm not using Gnome.

---

### Post by mishathegoat on 2008-06-23
Yep.. I've tried (in the terminal):

```
sudo gconf-editor
```

```
gksudo gconf-editor
```

and neither worked..

---

### Post by ad_267 on 2008-06-23
Don't use sudo!

Just "gconf-editor"

If you use sudo then it is changing the settings for root, not for you.

---

### Post by fooman on 2008-06-23
what icons are you referring to?

are these the mounted drives? ...or just the desktop icons (firefox, etc...)?

or both?

---

### Post by mishathegoat on 2008-06-23
> **ad_267 said:**
> Don't use sudo!

Just "gconf-editor"

If you use sudo then it is changing the settings for root, not for you.

This did the trick. Thank you.

---

### Post by molotov00 on 2008-06-23
> **ad_267 said:**
> Don't use sudo!

Just "gconf-editor"

If you use sudo then it is changing the settings for root, not for you.

oops. I should have realized that. sorry mishathegoat for the misdirection.

---

