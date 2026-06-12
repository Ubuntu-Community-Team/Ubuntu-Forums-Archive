---
title: "Other Compiz Fusion plugins vs. Unity"
date: 2013-05-28
forum: General Help
---

### Post by retroquark on 2013-05-28
Hi and Ubuntu to you as well.. or something like that. :)

Not initially a huge fan of the Unity layout choice in Ubuntu, and missing some options to scale UI. But gave it a try for a while. I've used Gnome3 on other distros as well - and had no problems with adding other compiz fusion plugins to that. However in Ubuntu 13.04, the plugin trigger hotspots are initially overridden, and therefore not responsive.

I.e., adding scale and expo works perfectly fine, and you can assign a trigger to it that hasn't been used, and the entire thing works great. But any screen-corners seem to be overridden by another, invisible plugin.

Initially, I thought it was the ubuntu workarounds, or one of the handler scripts on the plugin lists. But simply moving any of the plugins in the list up, or down, (which makes compiz fusion overlay restart?), makes it work as expected.

So question: what is stealing the screen corner triggers at boot-time, that can then be replaced by compiz without issue when the plugin list is reloaded?

I.. seem to remember having the identical issue with Ubuntu in version 9, or something like that >_< And that turned out to be some mysterious problem with nautilus and some gtk overlay not in use being loaded after the window manager. 

Any ideas what's going on here? And I don't seem to be able to actually trace what's catching or overriding the screen triggers.. Anyone know how I can do that..?

---

### Post by mcduck on 2013-05-28
Nothing hidden, nothing stealing things at boot time,  just the "Grid" Compiz plugin responsible of resizing & maximizing windows when you drag them to screen edges or corners... ;)

---

### Post by retroquark on 2013-05-28
That makes no sense to me at all, but disabling "Grid" fixed the problem :) 

Still. .....?

---

### Post by zombifier25 on 2013-05-28
When you drag a window to the left edge, it's resized to fit the left half of the screen. Same with right edge. When you drag it to the top edge, it maximizes. That's what the Grid plugin does.
Savvy?

---

### Post by retroquark on 2013-05-30
Yes, I understand that :) But why would it stop the edge detection triggers from working?

I guess there's the possibility that the "maximizing" window manager, with putting the status bar on the upper layer, makes it take precedence over the layer that would have picked up the pointer on the edges. But then why does it work after reloading any compiz fusion plugin (even with "grid" still active)?

..it just seems a bit random.

---

### Post by Frogs Hair on 2013-05-30
Is the desktop wall enabled ? Some plug-ins such as the cube disable the wall by default so the open application moves to a new cube face if dragged far enough.

---

### Post by retroquark on 2013-06-15
Mm. No, the wall (simple wall, cube disabled), expo and scale are enabled. And they all work and can be triggered by keyboard shortcuts.

What happens is that the screen corner triggers are caught by something else.. And I can't seem to find out if disabling or enabling (or moving the order in the plugin list) some specific plugin changes that. Instead, it seems that just having compiz restart "fixes" it. Suggesting that there's something else launching earlier that is catching the events that compiz isn't aware of, I guess.. 

..Is there a way to find out exactly what is trying to catch the screen triggers?

---

### Post by retroquark on 2013-06-22
And since the update earlier this week, ...something.. changed, and things now work as expected. Hmmh!

Thank you, lovely magical Ubuntu fairy!

---

