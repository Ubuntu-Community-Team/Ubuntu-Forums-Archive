---
title: "GNOME Panel issues"
date: 2007-05-25
forum: General Help
---

### Post by booljayj on 2007-05-25
The GNOME Panel and Beryl are not getting along well. They used to, but something changed. Don't get me wrong, Beryl works fine, but it's not well integrated.

The Workspace-switcher applet used to change to a beryl-oriented one when I turned on beryl. Now, however, it stays the same. This means that all four side on my desktop cube appear as one workspace, and clicking on the applet changes to an entirely different cube. This also creates problems with the window menus. They also fail to recognize the switch to beryl, and I am able to move them between the two workspaces without being able to move them around the cube (save for dragging).

This creates a whole score of little problems, and is downright annoying for sure. I tried removing beryl completely using synaptic, but that actually created problems for metacity. It wouldn't load up at the start of each session, so I had to manually type it into a terminal to start it.

---

### Post by supreme_geek_overlord on 2007-05-26
Have you checked the Beryl Settings Manager under the General Options section to see what the "Horizontal Virtual Size" and "Number of Desktops" are set to? On mine, they are 4 and 1, respectively. Perhaps the second setting was somehow set to greater than one, confusing the Gnome pager.

Just a guess.

---

