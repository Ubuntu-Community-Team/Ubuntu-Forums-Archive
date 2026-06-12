---
title: "[SOLVED] Initial positioning of windows"
date: 2007-10-20
forum: General Help
---

### Post by c.nosal on 2007-10-20
I have a clean gutsy install on my laptop, using compiz. Video card is an ATI radeon mobility x1400 with the restricted driver. The problem is that when I open some windows/programs (eg Synaptics/console), they open too far up, so that their menu bar is hidden under ubuntu's task bar. Of course it's easy to just select 'move' from right clicking on the program name at the bottom, but it becomes incredibly annoying.

Any ideas?

Thanks in advance.

---

### Post by Jorinn on 2007-10-22
I have the same problem except I can't move the windows at all. They'll max and minimise fine but not move. Titlebar is hidden by the top panel. I tried turning off expand for the panel. This only resulted in me being able to see the titlebar and select the window by clicking on it but for some reason I still can't move the windows.

More Info:
Compiz and emerald from gutsy repos.
Intel integrated graphics.

Never had this problem with feisty.

---

### Post by dondad on 2007-10-22
> **c.nosal said:**
> I have a clean gutsy install on my laptop, using compiz. Video card is an ATI radeon mobility x1400 with the restricted driver. The problem is that when I open some windows/programs (eg Synaptics/console), they open too far up, so that their menu bar is hidden under ubuntu's task bar. Of course it's easy to just select 'move' from right clicking on the program name at the bottom, but it becomes incredibly annoying.

Any ideas?

Thanks in advance.

You should be able to hold the alt key and click anywhere in the window to drag it to where you want. as long as it is not maximized.

---

### Post by Perpetual on 2007-10-22
I am not at my Ubuntu machine at the moment but if you go to Advanced Desktop Settings and play with the 'Place', 'Put' and 'Window Snapping' you can set windows to open centered.  I also disable the edge friction and a couple other misc. options regarding window placement.

Might help...

---

### Post by Jorinn on 2007-10-22
> **Perpetual said:**
> I am not at my Ubuntu machine at the moment but if you go to Advanced Desktop Settings and play with the 'Place', 'Put' and 'Window Snapping' you can set windows to open centered.  I also disable the edge friction and a couple other misc. options regarding window placement.

Might help...Seems to have half solved my problem, they no longer appear underneath the top panel but I still can't move them. Will play around a bit more with those advanced settings. 

Oh and dondad, alt key method doesn't work either.

---

### Post by Jorinn on 2007-10-22
Ok, sorted it and feel like a bit of an idiot. 

Why don't the windows move? Because the "Move Window" plugin wasn't enabled.

Having said that I would of thought that it would be enabled by default.

---

### Post by Perpetual on 2007-10-22
> **Jorinn said:**
> Ok, sorted it and feel like a bit of an idiot. 

Why don't the windows move? Because the "Move Window" plugin wasn't enabled.

Having said that I would of thought that it would be enabled by default.

Good, good.  As I said, not at my machine but I thought my 'Move Window' option was enabled by default.  I can't say 100% though.  Will check later as I *know* I haven't changed it's default setting.  However, I do not use Emerald.

---

### Post by Jorinn on 2007-10-22
> **Perpetual said:**
> Good, good.  As I said, not at my machine but I thought my 'Move Window' option was enabled by default.  I can't say 100% though.  Will check later as I *know* I haven't changed it's default setting.  However, I do not use Emerald.

Well it also might have to do with the fact that I had to uninstall compiz and reinstall it because I had Trevino's (sp?) packages installed.

---

### Post by c.nosal on 2007-10-23
> **Perpetual said:**
> I am not at my Ubuntu machine at the moment but if you go to Advanced Desktop Settings and play with the 'Place', 'Put' and 'Window Snapping' you can set windows to open centered.  I also disable the edge friction and a couple other misc. options regarding window placement.

Might help...

Thanks, I enabled 'smart' window placement, and so far things seem good.

---

