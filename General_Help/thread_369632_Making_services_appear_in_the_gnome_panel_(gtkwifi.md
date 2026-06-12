---
title: "Making services appear in the gnome panel (gtkwifi specifically)"
date: 2007-02-24
forum: General Help
---

### Post by Splat on 2007-02-24
Like the title says, I'm trying to embed gtkwifi into the gnome panel (aka systray). I installed it as part of my effort to get wireless working on my laptop after Network Manager appeared in the panel as intended but failed to see any wireless networks.

GTKwifi does work without any problems when it comes to listing networks and connecting when I start it with "gtkwifi run-in-window". But, as that option implies, it appears in a small window that floats around on one of the desktops that way instead of neatly getting tucked away in the gnome panel.

I also tried adding it to System -> Preferences -> Sessions / Startup Programs, but didn't have much more luck their either. Maybe I'm using the wrong options?

Any ideas appreciated, thanks in advance :)


Edit:

Figured it out by searching these forums some more...

1. Right-click on the gray area on the panel and uncheck "Lock to Panel" (optional)
2. Use the gray area to expand the panel to make some room (optional)
3. Right-click on the empty space in the panel
4. Select "Add to Panel"
5. Under **Internet**, select "Wireless Connection Manager" (this is in fact gtkwifi)
6. Click "Add" and then "Close"

It should appear where you right-clicked now, and if you want to can further adjust the size of the panel and then lock it again. Leaving this here as reference if someone stumbles on this little step too.

---

### Post by tgalati4 on 2007-02-24
Lock-to-panel is important, because if you mess around with screen resolution, your panel apps will get messed up when you go back to native resolution.

Thanks for the tip.  I was looking for the wifi app myself.

---

