---
title: "Mouse cursor wraps from right to left side of screen"
date: 2012-11-13
forum: General Help
---

### Post by dmwyatt on 2012-11-13
I installed [FONT="Courier New"]fglrx-updates[/FONT] package and this issue started occuring:

When I move the mouse cursor to the right edge of the screen, it "wraps" over and appears on the left side of the screen.  If I have my second monitor (which is on the left of my main monitor) enabled, it moves from the right side of the right screen to the left side of the left screen.

I purge removed [FONT="Courier New"]fglrx-updates[/FONT] and went back to [FONT="Courier New"]fglrx[/FONT] and the issue has persisted.

I have two Radeon HD 6950's in Crossfire.

How do I stop this from occuring?  It's becoming quite frustrating.

---

### Post by Impavidus on 2012-11-14
It's a feature: when you move your cursor to the edge of the desktop it moves on to the next, wrapping around to the first after reaching the last. You should be able to switch it off somewhere in your window manager settings (settings>window manager>advanced>wrap workspaces when the cursor reaches the edge of the screen (in xfce, I don't know about unity though, but the option should be there)).

---

### Post by dmwyatt on 2012-11-14
> **Impavidus said:**
> It's a feature: when you move your cursor to the edge of the desktop it moves on to the next, wrapping around to the first after reaching the last. You should be able to switch it off somewhere in your window manager settings (settings>window manager>advanced>wrap workspaces when the cursor reaches the edge of the screen (in xfce, I don't know about unity though, but the option should be there)).

There are no settings for workspaces in Unity...at least not in 12.10.

---

### Post by dmwyatt on 2012-11-18
So, I purged fglrx as described [here]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx").

Mouse wrap problem gone.  Yay.

Re-install fglrx and the problem comes back.  Boo.

Some sort of configuration is persisting, but I don't know where to find it.

---

