---
title: "Hidden Trash icon"
date: 2007-10-24
forum: General Help
---

### Post by spacemarc on 2007-10-24
Hi guys
I want to show the trash icon on my desktop... I've checked this key:
/apps/nautilus/desktop/trash_icon_visible
but the icon is still hidden.

How can I do view it?

---

### Post by rsambuca on 2007-10-24
Strange.  That definitely should put it on the desktop.

---

### Post by spacemarc on 2007-10-24
strange yes.

I've seen all items "trash" in gconf-editor and	they seem good.

Where i can see to resolve this issue?

---

### Post by drs305 on 2007-10-24
Try running the following two commands from terminal. The second is the equivalent of what you did with the GUI. The first is required because it overrides other individual settings.

```

gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop "true"
gconftool-2 --type bool --set /apps/nautilus/desktop/trash_icon_visible "true"

```

If that doesn't work, here'e some background.

I tried doing what you tried. Didn't get it to work. I ran the above commands and they didn't work initially either.

Next I looked at Gutsy's System, Preferences, Appearance settings since I hadn't played with those settings yet. I just use the 'basic' setting. I couldn't find anything that would show the trash icon there, but I did get around to installing a proprietary nvidia driver to try the 'Normal' video effects. I didn't like it and uninstalled it. Afterword, I again ran the two commands above and the trash icon appeared.

---

### Post by spacemarc on 2007-10-25
> **drs305 said:**
> Try running the following two commands from terminal. The second is the equivalent of what you did with the GUI. The first is required because it overrides other individual settings.

```

gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop "true"
gconftool-2 --type bool --set /apps/nautilus/desktop/trash_icon_visible "true"

```

If that doesn't work, here'e some background.

I tried doing what you tried. Didn't get it to work. I ran the above commands and they didn't work initially either.

Next I looked at Gutsy's System, Preferences, Appearance settings since I hadn't played with those settings yet. I just use the 'basic' setting. I couldn't find anything that would show the trash icon there, but I did get around to installing a proprietary nvidia driver to try the 'Normal' video effects. I didn't like it and uninstalled it. Afterword, I again ran the two commands above and the trash icon appeared.

i've running those keys but the trash doesn't appears again and i do not use the nvidia driver (i have Ati) nor desktop effects.

---

### Post by spacemarc on 2007-10-25
there is some workaround?

---

### Post by Absorbed on 2007-10-25
You could try this:

```
killall nautilus
nautilus &
```

You might need to add a sudo before those commands.

---

### Post by spacemarc on 2007-10-25
> **Absorbed said:**
> You could try this:

```
killall nautilus
nautilus &
```

You might need to add a sudo before those commands.

sorry, it not works.... The Trash icon is always hidden..

---

