---
title: "cgdw, changing window opacity for a single application"
date: 2006-08-10
forum: General Help
---

### Post by rianquinn on 2006-08-10
I noticed that you can change the Window Opacity of say the Gnome Ternimal by holding the Alt Key, and scrolling your mouse, or using the right click menu and selecting an opacity level.

What I want to do is on the command line, tell an application (like the Gnome Terminal) to start with an opacity of my choice.

This way I tell the terminal to always come up with the same opacity (75%), but all other applications come up with (100%) opcaity

Thanks,
Rian

---

### Post by kbuel on 2006-08-10
I think you can do that with the state plugin.  For example, I have all windows associated with GIMP to always start and maintain a brightness of 100% so that they are not affected by trailfocus.  I'm not on my Ubuntu box right now, but i believe this is what  you have to do. You should be able to do this easily through the Gset compiz program.

---

### Post by hanzomon4 on 2006-08-10
Go to [compiz forums]("http://www.compiz.net"). Their is a ton of compiz information, and their very friendly.
Also Gset compiz is outdated I believe.

---

### Post by mcduck on 2006-08-11
the solution is the 'State' plugin. Open gconf-editor, browse to apps/compiz/plugins/state/ and add 'c:Gnome-terminal:75' to the Opacity list :)

Note, that even when gset-compiz allows you to select window types for state plugin, it doesn't allow you to select application types.. Besides, gset-compiz is now seriously behind the compiz development and lacks many of the features available, and also handles some wrongly. You should use gconf-editor instead, at least until gset-compiz is updated.

---

### Post by rianquinn on 2006-08-12
it worked like a charm. Thanks for your replies.

Strange how you can't add this setting via "gset-compiz". Maybe this is something that they should add.

---

