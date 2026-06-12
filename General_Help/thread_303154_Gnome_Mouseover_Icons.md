---
title: "Gnome Mouseover Icons"
date: 2006-11-19
forum: General Help
---

### Post by mrcanard on 2006-11-19
Ubuntu 6.10 Edgy
When the mouse hovers over an icon a small, yellow, information box pops up.
I've been searching for a way to disable this feature.
My search terms must be lacking.
Would someone point me in the right direction.

Regards,
Charlie

---

### Post by mrcanard on 2006-11-20
Never mind.
They're called tooltips.

---

### Post by gejr on 2006-11-20
I knew they were called tooltips, but did you figure out a way to disable them?:)

---

### Post by gejr on 2006-11-20
I still haven't figured out how to disable them, but I found a way to change their colors. Probably old news for everyone, but I'll post it for those who're searching for this: 

```

sudo pico /usr/share/themes/<yourtheme>/gtk-2.0/gtkrc

```

Search the file for "tooltip" and insert the RGB-values you like.

then: ctrl+alt+backspace

Might be better options, but at least this works :)

---

### Post by CatKiller on 2006-11-20
**gconf-editor**
/apps/panel/global/tooltips_enabled

---

### Post by mrcanard on 2006-11-21
> I knew they were called tooltips, but did you figure out a way to disable them?

Sorry, I should have posted the link.

I did what CatKiller said to do.

Here's one you might like for Fire Fox,

about:config
browser.chrome.toolbar_tips

change to "false"

Regards,

---

