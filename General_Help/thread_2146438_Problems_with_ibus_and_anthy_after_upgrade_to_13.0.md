---
title: "Problems with ibus and anthy after upgrade to 13.04"
date: 2013-05-18
forum: General Help
---

### Post by Ertai87 on 2013-05-18
Hi all!  I use Japanese often on my computer, and I've been having a bit of a problem with ibus and anthy after upgrading from 12.10 to 13.04.  Previously, on 12.10, the ibus-daemon service started up (most of the time) when I booted my computer; I seldom had to manually start it to get it working.  Even when it didn't show in the taskbar, it would be running in the background, and starting it from the terminal would simply make the icon show.  However, on upgrade to 13.04, ibus does not even start on boot; I have to manually start it always.  Furthermore, when I start ibus, I have to reset my anthy settings each time; the settings are remembered, but are not loaded into ibus manually.  To fix this I have to open the ibus Preferences pane, have it load the list of non-default languages, and then it will work.

This is a bit of a pain.  Is there a fix for this out there to make ibus and anthy "just work" like they did on 12.10?  Thanks.

---

### Post by Popaul on 2013-06-18
You can have a look here:
[https://wiki.archlinux.org/index.php/IBus](https://wiki.archlinux.org/index.php/IBus)

---

### Post by Ertai87 on 2013-06-18
Oops.  Forgot I fixed this myself.  I forgot exactly how it did it, I think it involved messing with the startup settings in some fashion or other.  Anyway, closing this.

EDIT: Erm...Where's the "Mark as solved" button?

---

