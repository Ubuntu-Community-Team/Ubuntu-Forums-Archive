---
title: "update-alternatives x-cursor-theme question"
date: 2007-02-03
forum: General Help
---

### Post by dagnabit dang doohickey on 2007-02-03
I recently tried changing my cursor theme by using update-alternatives. One of the steps I did to get the new cursor theme working was:

update-alternatives --install [genname] x-cursor-theme [path/to/theme]

When doing this, I had no idea what the genname for x-cursor-theme should be, so I took some pointers (mostly conflicting pointers) from whatever Google could dig up for me. But, in the end I'm pretty sure I bonked the genname for x-cursor-theme, as it's now set to /etc/X11/cursors/x-cursor-theme and I think that may be wrong.

Does anyone know the correct update-alternatives genname path for x-cursor-theme?

Something that may help is if someone could post the output of a x-cursor-theme file search:
```
slocate x-cursor-theme
```
If the above command returns nothing, you will need to run the following command, then the above command.
```
sudo slocate -u
```

Thanks

---

### Post by dagnabit dang doohickey on 2007-02-03
*bump*

Please, if anyone could post the output of:
```
slocate x-cursor-theme
```
I think it would be a great help.

The result I get from slocate x-cursor-theme is:

/var/lib/dpkg/alternatives/x-cursor-theme
/etc/alternatives/x-cursor-theme

which is correct, but I'm pretty sure there should be a third x-cursor-theme somewhere.

*BTW, if you don't know what slocate is, it's Secure Locate. It's a "Find" tool you can use to search your system. It's good stuff. Use it once and you'll find that it surely deserves a place in your bag of tricks.*

---

### Post by dagnabit dang doohickey on 2007-02-03
After digging through some cursor theme sources, I'm 99.9% sure the the genname (generic name) to use with update-alternatives for x-cursor-theme is:

```
/usr/X11R6/lib/X11/icons/default/index.theme
```

Confirmation from a guru would be appreciated.

---

### Post by johnmarkschofield on 2008-06-28
The way the alternatives system works, there is a symlink somewhere on the system pointing to a symlink in /etc/alternatives, which points to the actual file selected by update-alternatives.

I did a find on my system for any files that are symlinked to /etc/alternatives/x-cursor-theme. Here's the command (so you can replicate on your system) and the result:

find / -lname /etc/alternatives/x-cursor-theme 2>/dev/null
/usr/share/icons/default/index.theme

So /usr/share/icons/default/index.theme is what you should use.


John

---

