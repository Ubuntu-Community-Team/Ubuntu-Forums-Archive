---
title: "What does &quot;only on this workspace&quot; do?"
date: 2013-03-08
forum: General Help
---

### Post by bogdarnet on 2013-03-08
I keep getting applications that want to jump to another workspace.  (GIMP is the one I'm noticing at the moment, but I've seen in others as well.)  I just checked, and "only on this workspace" is checked.

Why, then, is it jumping around?

---

### Post by ManamiVixen on 2013-03-08
The option only appiles on per window basis. If you want all of gimp's windows on one workspace, all gimp windows must have the "Only on this workspace" checked and all windows have to be on the desired workspace before being checked.

---

### Post by tgalati4 on 2013-03-08
Depending on what version of Ubuntu you are running and what desktop environment you are running, when you have an application that extends slightly into the next workspace, it will sometimes want to migrate to that next workspace.  I'm not sure what this behavior is called--perhaps "sticky window" or tiling.  You might look at what options you have set for application window behavior in your environment.

---

### Post by opethfan89 on 2013-03-08
tgalati4 is right.  "Sticky window" is a setting in some of the window managers to allow windows to be easily dragged in between workspaces.  In the Cinnamon desktop of Linux Mint, its a Cinnamon-specific setting, but I don't know if that conveys over to Ubuntu as well (I'd imagine as much, since Mint is an Ubuntu derivative.

---

### Post by bogdarnet on 2013-03-08
Okay, looking in CCSM, the advanced search found "sticky" in three places: Desktop Wall, Window Rules, and Workarounds...  I don't have Window Rules on, so it's one of the other two?  Under Desktop Wall > Viewport Switching > Non Sliding Windows, I see:

type=Dock|type=Desktop|state=Sticky

Under Workarounds, I see two choices under "Window stickyness":

Make "on all desktops" windows "sticky (which is NOT checked) - sticky_alldesktops
"On all desktops" sticky match _any_ (which is checked) - alldesktop_sticky_match

This is all gobbledy-gook to me though...

P.S. I tried ManamiVixen's suggestion first, since it sounded nice and easy, but it unfortunately didn't bear fruit... the GIMP windows were all too happy to jump away even so.

---

### Post by tgalati4 on 2013-03-08
I could never figure it out either, so I just kept turning things off until the annoying behavior went away.  If you have dual or quad monitors set up, then some of those sticky options might be neat, but it's definitely annoying on a single screen.

---

### Post by bogdarnet on 2013-03-08
Found this definition:

 Sticky: These windows are visible on every desktop/workspace/viewport at once. 

Here:

[http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching)

So I wonder if Compiz's "sticky" equates to "Always on Visible Workspace"...

---

### Post by bogdarnet on 2013-03-09
So, it seems to me, "only on this workspace" actually means "only on one workspace which may or may not be this one" ... (but that was too long to fit in the context menu)... no?

---

