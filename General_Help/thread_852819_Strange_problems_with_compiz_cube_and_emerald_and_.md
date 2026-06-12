---
title: "Strange problems with compiz cube and emerald and panel in Ubuntu 8.04"
date: 2008-07-08
forum: General Help
---

### Post by gluonman on 2008-07-08
Greetings.
I recently installed 8.04 on my friend's desktop (she was miserable with her Windows Vista). But there are problems. I spent quite a bit of time doing things like enabling compiz cube and using emerald, etc. She liked what I did with my Ubuntu desktop and its effects and wanted me to customize her computer in a similar way. However, I'm running into some interesting problems that I didn't seem to have with my own desktop, and I'm failing to understand.

The following is a list of the specific issues that I need guidance with:

1) I'm not sure how to have Emerald automatically enabled without having to press Alt-F2 and then type 'emerald --replace', which I have to do after each restart.

2) Whether Emerald is enabled or not, the minimize, maximize, and close buttons on all windows have disappeared entirely (the only way to close windows is Alt-F4).

3) All windows that I open automatically open on all 4 workspaces on my cube, except for the embedded terminal I tried to make (like the one I configured on my other computer), which only opens on one workspace. I cannot figure out how to make non-embedded windows open only on one workspace, and I cannot figure out how to get the embedded terminal to open on all workspaces instead of just one.

4) The Alt-Tab function, or alternatively the <super>-Tab function, is completely disabled, or just doesn't function at all.

5) I have replaced the Gnome panel with Avant-Window-Navigator. The new MAC OSX like panel is working fine, but Gnome cannot delete the main panel (which I understand is normal), so I just moved the Gnome panel to the top and used it for just a couple of things that AWN can't support. However, every time I restart, the Gnome panel automatically appears right in the middle of the workspace instead of at the top. I have to open the panel properties and select expand in order for it to move back to the top.

6) 3D Windows is enabled in the compiz settings manager, but doesn't actually seem to work. The windows aren't 3D at all. Can't seem to correct this.

Other than these 6 annoying problems, the rest is simple. Help soon would be much appreciated.

---

### Post by isaacj87 on 2008-07-08
> **gluonman said:**
> Greetings.
I recently installed 8.04 on my friend's desktop (she was miserable with her Windows Vista). But there are problems. I spent quite a bit of time doing things like enabling compiz cube and using emerald, etc. She liked what I did with my Ubuntu desktop and its effects and wanted me to customize her computer in a similar way. However, I'm running into some interesting problems that I didn't seem to have with my own desktop, and I'm failing to understand.

The following is a list of the specific issues that I need guidance with:

1) I'm not sure how to have Emerald automatically enabled without having to press Alt-F2 and then type 'emerald --replace', which I have to do after each restart.

2) Whether Emerald is enabled or not, the minimize, maximize, and close buttons on all windows have disappeared entirely (the only way to close windows is Alt-F4).

3) All windows that I open automatically open on all 4 workspaces on my cube, except for the embedded terminal I tried to make (like the one I configured on my other computer), which only opens on one workspace. I cannot figure out how to make non-embedded windows open only on one workspace, and I cannot figure out how to get the embedded terminal to open on all workspaces instead of just one.

4) The Alt-Tab function, or alternatively the Win-Tab function, is completely disabled, or just doesn't function at all.

5) I have replaced the Gnome panel with Avant-Window-Navigator. The new MAC OSX like panel is working fine, but Gnome cannot delete the main panel (which I understand is normal), so I just moved the Gnome panel to the top and used it for just a couple of things that AWN can't support. However, every time I restart, the Gnome panel automatically appears right in the middle of the workspace instead of at the top. I have to open the panel properties and select expand in order for it to move back to the top.

Other than these 5 annoying problems, the rest is simple. Help soon would be much appreciated.

1) The simplest solution, would be to install fusion-icon and use that to set the window decorations. However, you can go into CCSM, go into the "Window Decoration" plugin and where it says "Command" put:

```
emerald --replace
```

That will take care of Emerald and you won't have to keep on initiating it. :)

2) I can't tell whether or not it's just a theme that doesn't have the buttons, or if Emerald is not running correctly...If you could post a picture, I could be a little more helpful with this problem.

3) Sorry, I don't deal much with embedded windows :) As far as I know, Compiz will automatically open a window within the current workspace. I'll poke around in CCSM and see if there's a way to disable this.

4) The Alt+tab combo is the default key mapping for the "Application Switcher" plugin and the Superkey+tab (Windows key) is for the "Shift Switcher." More than likely, these plugins are currently turned off. Go in to CCSM and turn them on.

5) I don't quite understand this situation. Did you delete the bottom panel and leave the top one? I guess I need a little bit more clarification on this one. Screenshot would be nice ;)

6) 3D windows only work with the Cube. The user can only see the "3D Windows" when the cube is rotating. If the windows appear too flat, there are settings to adjust the depth of the windows.

---

### Post by gluonman on 2008-07-09
Thank you very much for your response and your help. I ended up fixing each of the problems that I listed. Things are running smoothly.

---

