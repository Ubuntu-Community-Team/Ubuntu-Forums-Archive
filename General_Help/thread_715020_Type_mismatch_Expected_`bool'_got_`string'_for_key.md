---
title: "Type mismatch: Expected `bool' got `string' for key /apps/gnome-terminal/profiles(..."
date: 2008-03-04
forum: General Help
---

### Post by Mr.Johnny on 2008-03-04
Hi!

I'm getting this error everytime I open the gnome-terminal:

"Type mismatch: Expected `bool' got `string' for key /apps/gnome-terminal/profiles/Default/use_theme_colors"

I can find the path/file it refers to, what can I do?

thanks.

---

### Post by spec-chum on 2008-03-04
Try this.

Run the command gconf-editor either via ALT-F2 or from a terminal and navigate to apps->gnome-terminal->profiles->Default in there.

You should see a checkbox for use_theme_colors in there.  Try either ticking or unticking it and then open a terminal.

Does that sort it?

---

### Post by Mr.Johnny on 2008-03-04
Yes, it did! Thanks!!

Btw, isn't there a way of doing this thru the terminal only?

---

### Post by Mr.Johnny on 2008-03-09
oops... without gui, I mean.

---

