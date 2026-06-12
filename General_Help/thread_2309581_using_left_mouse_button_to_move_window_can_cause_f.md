---
title: "using left mouse button to move window can cause freeze (XFCE4/Ubuntu 15.10)"
date: 2016-01-11
forum: General Help
---

### Post by dnarnold2 on 2016-01-11
I use xfce4 under Ubuntu 15.10. Fairly often some action with my mouse causes the cursor to change into the closed hand icon and my session freezes in a useless state. When this happens the cursor continues to track the mouse, and certain keystroke combinations work (like Alt-Tab or CTRL-ALT-Fn) but I cannot type to a terminal, click a button, close a window, or otherwise do anything useful. I generally am forced to use CTRL-ALT-BACKSPACE to kill the X session, or use CTRL-ALT-Fn to get a terminal window from which I can kill the X session, either way losing all unsaved work.

I can reliably repeat this behavior by opening okular, moving the cursor just to the left of the page selection widget on the bar at the bottom of the window, and moving the window by clicking the left mouse button and dragging. (If I move the window by holding Alt while dragging, I don't have trigger this behavior.)

Other applications cause the behavior as well. For example, if I drag to move a clementine window near the player controls near the bottom of the window.

The biggest problem is that it seems easily to inadvertently trigger this behavior, and I'm finding that I am forced to restart/crash my X session a few times a day.

It seems that others have reported similar problems (but I haven't found any solution):

[http://unix.stackexchange.com/questions/50426/xfce-hangs-with-hand-cursor](http://unix.stackexchange.com/questions/50426/xfce-hangs-with-hand-cursor)

[https://bbs.archlinux.org/viewtopic.php?id=196415](https://bbs.archlinux.org/viewtopic.php?id=196415)

[http://ubuntuforums.org/showthread.php?t=2000507](http://ubuntuforums.org/showthread.php?t=2000507)

 Any solutions for this very troublesome behavior?

---

