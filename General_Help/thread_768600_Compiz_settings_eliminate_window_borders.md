---
title: "Compiz settings eliminate window borders"
date: 2008-04-26
forum: General Help
---

### Post by cybertron3000 on 2008-04-26
Upon upgrade from Gutsy to Hardy, when I try to use "normal" or "extra setting" in Appearance (in other words, Compiz useage), it eliminates my window borders/titlebar.

Any solutions?  By the way, can't even apply my Emerald program to changes either.

---

### Post by Zorael on 2008-04-26
Missing window titlebars generally means missing window decorator. What happens if you start emerald from a terminal? Any error output?
```
$ emerald --replace &
```

---

### Post by cybertron3000 on 2008-04-26
$ emerald --replace &

Terminal did not apply this command line - is there a typo?

---

### Post by damis648 on 2008-04-26
Type
$ emerald --replace
(no & sign)
and if that works just add it to System<preferences>session

---

### Post by cybertron3000 on 2008-04-26
I forgot to add the Terminal output was this:

[1] 7587

---

### Post by cybertron3000 on 2008-04-26
I reinstalled Emerald from the command in Terminal.  I may be totally ignorant of its use - how do I actually apply a theme?  It seemed to work in Gutsy, but I may have had to have done some extra configuration that I forgot about.

---

### Post by Zorael on 2008-04-26
You should omit the dollar sign, it's just standard syntax when detailing terminal commands. Naturally, you can run it in a run box as the above poster mentioned. The ampersand (&) is there to let you keep control of the terminal, making emerald a child process of it. If you close the terminal program with the x button, emerald will close too, but if you enter 'exit' it will stay running in the background.

As for configuring Emerald, you should have a theme manager someplace in the panel menus. Else just run emerald-theme-manager. Just picking themes in that manager won't apply them unless you're already running Emerald; normally, Compiz launches it by default, provided you have it installed and that the Window Decorations plugin is enabled.

---

