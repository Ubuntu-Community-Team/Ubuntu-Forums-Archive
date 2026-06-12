---
title: "Gnucash causes Unity panel and title bars to disappear"
date: 2013-09-05
forum: General Help
---

### Post by raydar on 2013-09-05
On a machine running straight Ubuntu 12.04, most times when I run Gnucash the Unity panel and the title bars for all open windows disappear as soon as the program finishes loading. Sometimes only the title bar of the Gnucash window itself disappears, leaving other windows intact and the Unity panel intact.

Regarding the Unity panel: It acts as if it's still there but auto-hidden, because its icon tooltips appear when I run my mouse pointer along the left side of the screen; but Unity panel auto-hiding was and is turned off in System Settings-->Behavior.

Regarding the title bars for all windows: The menu bar remains, but the title bar is absent.

When I try ```
unity --reset
``` as suggested in threads like [http://ubuntuforums.org/showthread.php?t=1493083&page=3&highlight=unity+title+disappear](http://ubuntuforums.org/showthread.php?t=1493083&page=3&highlight=unity+title+disappear) the Unity panel comes back, but not the title bars. (This also resulted in the menu bar of one window I had open suddenly overlapping the top panel, the menu bar being its highest-up part since its title bar was nonexistent.)

Any ideas what about Gnucash might be causing this, and how to fix it for good?

---

### Post by raydar on 2013-09-10
I'd wondered if it was not GnuCash in particular but QT apps in general, but VLC, another QT app, doesn't cause this problem.

Some threads addressing a general problem of disappearing unity panel and title bars, such as [http://ubuntuforums.org/showthread.php?t=938241](http://ubuntuforums.org/showthread.php?t=938241) , find that Compiz was causing the problem, but the Ubuntu 12.04 machine I'm having this trouble on does not have the ~/.compiz directory that link mentions.

Please, could someone help me get on the right path for troubleshooting this?

---

### Post by raydar on 2013-09-11
Well, the problem went away after I installed compizconfig-settings-manager, ran it ("ccsm"), and unchecked "Window Decoration," waited a moment, then re-checked it and closed, logged out and logged back in, as gleaned from [http://ubuntuforums.org/showthread.php?t=1493083&page=3&highlight=unity+title+disappear](http://ubuntuforums.org/showthread.php?t=1493083&page=3&highlight=unity+title+disappear) and [http://askubuntu.com/questions/127240/missing-launcher-after-12-04-upgrade](http://askubuntu.com/questions/127240/missing-launcher-after-12-04-upgrade) .

I still don't understand why the problem started or why this fixes it, unfortunately.

---

