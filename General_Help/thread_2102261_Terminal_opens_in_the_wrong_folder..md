---
title: "Terminal opens in the wrong folder."
date: 2013-01-06
forum: General Help
---

### Post by Paddy Landau on 2013-01-06
For as long as I have used Ubuntu, when I open the terminal (using the menu, Dash or [FONT=Lucida Console]Ctrl+Alt+T[/FONT]), by default it opens in my home folder, i.e. [FONT=Lucida Console]/home/paddy[/FONT].

Just recently, it has started to open in my Desktop, i.e. /home/paddy/Desktop. I don't want this new behaviour, and I don't know why it has changed.

Putting debug statements into my [FONT=Lucida Console].bashrc[/FONT], it seems that the folder has already been changed to [FONT=Lucida Console]Desktop[/FONT] before [FONT=Lucida Console].bashrc[/FONT] starts.

Any idea how to diagnose and fix this?

I am running 12.04 64-bit fully updated.

---

### Post by Impavidus on 2013-01-06
Well, my terminal (xfce4-terminal, so it's a different one) still behaves correctly.

When I start a new terminal from an old one it's in the same directory as the old one, when I start one from the launcher it starts in my home directory.

Just an idea: I'm sure there must be an option to select the directory of a terminal in the command that opens it. Have you checked which command is stored in your menu (although that doesn't explain the directory when opening from the dash or ctrl+alt+t, but that keyboard shortcut too must be defined somewhere)?

---

### Post by Paddy Landau on 2013-01-07
Thanks for your reply.

Quite bizarrely, today it is working correctly again. :confused:

I'll mark this as solved, but I do wish I knew how it had become confused in the first place.

---

