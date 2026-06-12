---
title: "Question about workspaces"
date: 2008-04-19
forum: General Help
---

### Post by bash on 2008-04-19
I have 3 different workspaces atm. Now what bugs me is that no matter on what workspace I open a programm it always starts on the workspace I am currently on. Is there a way to set it that if I start a program on workspace 2 for example, that the program also opens on workspace 2, no matter what workspace I am currently on?

---

### Post by angry_johnnie on 2008-04-19
devilspie can do it, and is available in your repositories.

[This]("http://ubuntuforums.org/showthread.php?t=75749&highlight=devilspie") howto is a little old, but you might want to dig into it for a more complete understanding of how devilspie works.

But, it's not too complicated to change a couple of things from [this]("http://ubuntuforums.org/showthread.php?t=202249&highlight=devilspie") other one to do what you want (removing everything except the **set_workspace** line does exactly what you want).

Edit:  ok you don't want to remove everything... just these lines:

                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "+50+50")
                (geometry "924x668")

Everything else should be the same, except the part where it says  **(matches (window_name) "DesktopConsole")**.  Just replace DesktopConsole with what you want, whether its aMSN, Firefox, or whatever. :-)

---

