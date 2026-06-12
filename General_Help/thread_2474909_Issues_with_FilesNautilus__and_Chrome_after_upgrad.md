---
title: "Issues with Files/Nautilus  and Chrome after upgrade to 22.04"
date: 2022-05-11
forum: General Help
---

### Post by lordpuppet on 2022-05-11
Im not sure if the problem lies with Files/Nautilus (which I am on v 42.0) but here are some stuff I found out just after upgrading from Ubuntu 21:

[LIST]
[*]When I try to download something from Chrome and it opens a Files/Nautilus window to select where to put the file, it works only if I leave it on the default folder. If I try to move it elsewhere, it doesn't save the file at all.
[*]When I want to upload a picture, it won't show me a thumbnail as it did before 22.04. 
[*]This Files/Nautilus window fills the whole screen by default
[*]Sometimes the shift+delete key shortcut won't work (this unrelated to file dialog, just Nautilus in particular).
[/LIST]

Are people aware of this or it's just me?

---

### Post by vanadium on 2022-05-11
This is not nautilus. It is a GTK4 file dialog.

1) Explain how you try to move it elsewhere. Provide instructions that someone can follow to reproduce your issue
2) Yes, GTK4 dialogs do not show any preview at all anymore
3) Yes, strange things also there. After resizing, I sometimes see that window automatically changing size in steps, up to a point it is not reponsive anymore
4) I never delete while in a file dialog, so cannot confirm here.

---

