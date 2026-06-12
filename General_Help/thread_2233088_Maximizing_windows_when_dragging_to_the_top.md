---
title: "Maximizing windows when dragging to the top"
date: 2014-07-06
forum: General Help
---

### Post by markodd on 2014-07-06
Hey there,

I'm currently using Xubuntu 14.04 and I'd like a way to enable maximizing windows when dragged to the top (also maximize-right/left when dragged to the right/left)

How would I go about doing that?

---

### Post by mooreted on 2014-07-06
This feature can be enabled or disabled in the settings of the XFCE window manager.

Settings => Window Manager Tweaks => Accessibility => Automatically tile windows when moving toward the screen edge

---

### Post by markodd on 2014-07-06
> **mooreted said:**
> This feature can be enabled or disabled in the settings of the XFCE window manager.

Settings => Window Manager Tweaks => Accessibility => Automatically tile windows when moving toward the screen edge

It doesn't maximize the window when moving to the top, which is what I want.

---

### Post by mooreted on 2014-07-06
It's supposed to. I'll install Xfce and see if I can find it. I've been meaning to set it up anyway.

---

### Post by Dennis N on 2014-07-06
Dragging to top will maximize width but not height as default behavior - this behavior can be turned off. Does not apply to windows that cannot be maximized (some dialogs, for example - these lack a maximize button.)

I don't believe maximizing when dragging to the top can't be set anywhere as a user option, probably because there are several other simple actions to do this. 

Some suggestions:

Besides the maximize button, double clicking on the title bar will maximize the window (the default action- other actions possible). 

These are keyboard toggles for the following actions (repeat to reverse). 

Alt+F5 = Expand width to maximum
Alt+F6 = Expand height to maximum

I am unaware of a user configuration setting that drag to left, right or bottom edge will maximize anything. 

Edit: Now I am aware. See post #15 for settings.

That's it.

---

### Post by Toz on 2014-07-06
Unfortunately, Xfce doesn't currently support maximizing windows when dragging to the top. The tiling feature just 1/2 screen maximizes. There are enhancement requests for this. See: [https://bugzilla.xfce.org/show_bug.cgi?id=9927]("https://bugzilla.xfce.org/show_bug.cgi?id=9927").

Out of curiosity, why not just double-click the title bar (or press the maximize button) if you want to maximize the window?

Edit: ninja'd.

---

### Post by mooreted on 2014-07-06
> **Toz said:**
> Unfortunately, Xfce doesn't currently support maximizing windows when dragging to the top. The tiling feature just 1/2 screen maximizes. There are enhancement requests for this. See: [https://bugzilla.xfce.org/show_bug.cgi?id=9927]("https://bugzilla.xfce.org/show_bug.cgi?id=9927").

Out of curiosity, why not just double-click the title bar (or press the maximize button) if you want to maximize the window?

Edit: ninja'd.

Beat me to it. Apparently people have suggested that. Mine does the same: drag window to top edge, get half a window. Drag to the bottom, get half a window.

---

### Post by Dennis N on 2014-07-06
> Drag to the bottom, get half a window.

I don't have this behavior - only on the top. Possibly because there is a panel on the bottom?

Edit: See post #15 for settings to get them to maximize height or width on all edges.

---

### Post by Toz on 2014-07-06
Push the mouse beyond the panel border to the screen edge - it should tile.

---

### Post by Dennis N on 2014-07-06
> **Toz said:**
> Push the mouse beyond the panel border to the screen edge - it should tile.

The expanded width effect works only at the top edge. On the bottom, right, or left edges, window is set to snap to the edge, but if you push further, it just slips off the screen - that doesn't happen at the top. I have the main panel on the bottom (plus another autohide panel on the left used a launcher) which as I said may affect this. Will test to see.

---

### Post by Dennis N on 2014-07-06
> Will test to see. 

Moved panel to top. No change seen in window behavior: Still won't expand width at bottom edge.  Expands width at top when you hit the panel.

---

### Post by Dennis N on 2014-07-06
I decided to check this window behavior at the edges on another machine also with Xubuntu 14.04. I observe the same exact behavior - windows expand to full width at the top edge only. 

Edit: See post #15 for how to fix this.

Another observation:

If I move two windows to the top edge, they do not tile, but the second is superimposed on the first (both expanded full width). I was taught that tiling means "non-overlaping" (like ceramic tiles on a floor) and that is not the case here. So the setting "Automatically tile windows when moving toward the screen edge" (which is checked) seems not to work with the customary meaning of tiled windows.

---

### Post by mooreted on 2014-07-06
It is some odd tiling behavior. About all you can do is add yourself to the bug report and hope the developers get around to fixing it. I just double-click the window border for maximize.

---

### Post by Toz on 2014-07-06
> **Dennis N said:**
> The expanded width effect works only at the top edge. On the bottom, right, or left edges, window is set to snap to the edge, but if you push further, it just slips off the screen - that doesn't happen at the top. I have the main panel on the bottom (plus another autohide panel on the left used a launcher) which as I said may affect this. Will test to see.

Do you have "Wrap Workspaces" enabled? It needs to be disabled. Settings Manager >> Window Manager >> Advanced tab.

---

### Post by Dennis N on 2014-07-06
> **Toz said:**
> Do you have "Wrap Workspaces" enabled? It needs to be disabled. Settings Manager >> Window Manager >> Advanced tab.
In Settings > Window Manager > Advanced Tab > deselected "Wrap workspaces when reaching the edge > with a dragged window"

Some Changes!
After log out and in, a window now maximizes in width or height as you drag it across the screen edges. On the bottom I had to shove it off the screen entirely then it pops up maximized width. 

Since the tiling happens at the top edge without wrap workspaces deselected, I think many users would assume the other edges should behave the same way. They don't - to make them tile as well, you have to deselect wrap workspaces. Even after doing that, at the top the window maximimizes as soon as you hit the panel or edge and will not move past it. A user might reasonably expect the other edges to act the same way. They don't. You need to drag them far past the edge.

I can now see someone using this to tile two windows horizontally or vertically if you drag them across opposite edges. It is true that if you drag two windows across the same edge, one covers the other completely instead of sharing the edge.

Anyway, thanks for the "wrap workspaces" tip. It may help others who want the correct settings to tile the windows.

---

