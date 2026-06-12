---
title: "Desktop and file manager not refreshing after adding new files"
date: 2007-12-06
forum: General Help
---

### Post by bmeyer on 2007-12-06
I've seen others on here with this problem, but haven't seen many answers.

My desktop does not seem to be refreshing automatically as it once did.  When I save something to the desktop (Firefox, text file, anything!), it does not show up unless I use the terminal or file manager.  The file manager does not seem to show new files either, even if the manager is a new instance.  You have to manually refresh it.

I'm on Gutsy.  It seems to have started after a recent gnome update.

Any ideas why?  Restarting X everytime isn't an answer ;)

---

### Post by bmeyer on 2007-12-06
Update:

I downloaded some zip files and they saved to the desktop.  But, I had to use Nautilus to manually refresh ~/Desktop before they'd actually appear.  Also, dragging/exporting files from the zips would not show up either until manually refreshed.  What's going on?

---

### Post by braacken on 2007-12-07
I had these problems on feisty.  Never really corrected them, but they seemed to appear after installing and mixing kde/gnome applications.

F5 should refresh.

have you tried using gconf-editor?

Can modify options that you normally have to find terminal codes for.

---

