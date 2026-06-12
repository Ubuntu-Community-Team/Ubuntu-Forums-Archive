---
title: "BUG in my menu bar"
date: 2008-06-09
forum: General Help
---

### Post by bravemenrun333 on 2008-06-09
I am customizing my desktop environment and I ran into a bug:

[IMG]http://img392.imageshack.us/img392/8489/screenshotnk9.jpg[/IMG]

This fading effect on the menu (Applications/Places/System)! I cant get rid of it. Dont want it! Want it to be just grey, like on the right side of the bar!

Is this bug known?

:confused:

---

### Post by attari on 2008-06-09
> **bravemenrun333 said:**
> I am customizing my desktop environment and I ran into a bug:

[IMG]http://img392.imageshack.us/img392/8489/screenshotnk9.jpg[/IMG]

This fading effect on the menu (Applications/Places/System)! I cant get rid of it. Dont want it! Want it to be just grey, like on the right side of the bar!

Is this bug known?

:confused:


I am guessing that's the panel form the theme. Right click panel, then properties, then Background tab, select solid colour instead of none.

---

### Post by bravemenrun333 on 2008-06-09
no, its solid color already...
any more ideas?

---

### Post by Het Irv on 2008-06-09
Have you tried deleting and then readding he menus?  If that doesn't work you can try deleting and readding the entire panel.

---

### Post by bravemenrun333 on 2008-06-09
got it!
deleting/adding it again solved the problem.
thanks!

---

### Post by attari on 2008-06-09
> **bravemenrun333 said:**
> no, its solid color already...
any more ideas?

I am a noob as far as linux is concerned... but I am guessing it has to do with Configuration Editor (Go to terminal, NOT Root terminal... then write gconf-editor).

You will need to navigate to apps/panel/objects/ and choose object_xxx whose object_type is "menu-bar". You may need to tweek that around to get what you want.... I use that to change my menu icon...

---

### Post by Het Irv on 2008-06-09
No Problem,
Hey where did your name come from?  I know of a book by that name and I was wonder if the two were related.


Also, Please mark your post as solved (in the drop down box labeled Thread Tools)

---

