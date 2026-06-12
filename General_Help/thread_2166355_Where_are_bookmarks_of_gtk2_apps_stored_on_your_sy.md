---
title: "Where are bookmarks of gtk2 apps stored on your system?"
date: 2013-08-08
forum: General Help
---

### Post by vasa1 on 2013-08-08
On my system, Lubuntu 13.04, I have two bookmark files:
[FONT=Courier New]~/.gtk-bookmarks
[/FONT]and
[FONT=Courier New]~/.config/gtk-3.0/bookmarks[/FONT].

I get the impression that bookmarks created by the file manager, when PCManFM is the file manager and controls the desktop environment or when Thunar is  the file manager and Xfce is the desktop environment, are created in [FONT=Courier New]~/.gtk-bookmarks[/FONT].

However, the bookmarks created by dragging folders to the side-pane in the File, Save (As), window in other applications, be they **gtk2 or gtk3**, go into [FONT=Courier New]~/.config/gtk-3.0/bookmarks[/FONT].

Is this saving of bookmarks of gtk**2** apps to  [FONT=Courier New]~/.config/gtk-**3**.0/bookmarks[/FONT] intended behavior? Is such behavior present in Xubuntu (on which Nautilus hasn't taken over as file manager and manager of the desktop)?

---

### Post by vasa1 on 2013-08-09
See:
[https://bugs.freedesktop.org/show_bug.cgi?id=59527](https://bugs.freedesktop.org/show_bug.cgi?id=59527)
and
[https://bugs.freedesktop.org/attachment.cgi?id=73386](https://bugs.freedesktop.org/attachment.cgi?id=73386)

---

