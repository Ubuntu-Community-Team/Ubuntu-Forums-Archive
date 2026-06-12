---
title: "dragging windows between workspaces broken by update?"
date: 2008-06-13
forum: General Help
---

### Post by revdrace on 2008-06-13
Yesterday I noticed that I could no longer drag windows between workspaces.  It worked just a few days ago.  The only thing I can think of that might have affected it is the system updates.  Unfortunately, I don't know precisely which updates were installed when it broke.  It has to be one of the updates of the last 3 or 4 days though, as I run system updates fairly frequently.  I recall that immediately after the update two of my workspaces disappeared, and I had to go into the workspace preferences and restore them (I normally work with four workspaces).

I was able to get it working again -- but only by reenabling a proprietary video driver that I had disabled a couple of weeks ago.  Disabling this driver did not cause the problem, as the problem did not start until a couple of weeks later.  After reenabling the driver I had to switch "Visual Effects" from "none" to "normal" in the "Appearance preferences."  If I switch back to "none" then the problem returns, and I cannot drag windows between workspaces.

I am running 8.04 (Hardy) on an AMD laptop, with an ATI video card.  I found lots of stuff about compiz related to edge flip problems, and when I investigated I found that compiz does not seem to be able to run on this laptop - I think it is running metacity instead.  Perhaps that has something do to with it... but what I found perturbing is that it *did* work, and then suddenly quit.

Hope this helps if anyone is having the same problem.  If anyone has a guess which update caused the problem, please forward the report on to the developers.

- ace

---

### Post by stek79 on 2008-08-13
Hi have the same problem here, running basic desktop effects (metacity).

I've just noticed that the dragging doesn't work.

Did you eventually sorted out this issue?

---

### Post by stek79 on 2008-08-13
Are you sure that the window dragging was possible with metacity?

Actually I was using it back when I enabled compiz.

BTW I've found that an handy way to move windows to different workspaces is using the relevant shortcuts:

CTRL+SHIFT+ALT+LEFT -> move window to left workspace

You can find them in System->Pref->Keyboard Shortcuts.

---

