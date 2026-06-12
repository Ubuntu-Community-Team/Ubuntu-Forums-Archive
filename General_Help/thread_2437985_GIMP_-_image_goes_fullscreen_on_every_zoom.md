---
title: "GIMP - image goes fullscreen on every zoom"
date: 2020-03-04
forum: General Help
---

### Post by JamButty on 2020-03-04
I have used GIMP for years with no major problems. I had an oddity with the toolbox I did not understand and so I deinstalled, deleted snap/gimp and reinstalled. Now every time I zoom in, the display goes to fullscreen, which is a major problem.
edit-preferences-image windows-"resize window on zoom" is NOT checked. In any event, checked or unchecked has no effect on this behavior.
What am I missing? Previously the main image window always remained in the middle of the display area so that scroll bars did not expand under other windows to the left and right regardless of the zoom level. How do I return to that?
This is GIMP 2.10.18 in Ubuntu 18.04.4

---

### Post by sdsurfer on 2020-03-04
With the zoom tool selected in the toolbox, did you try Window->Dockable Dialogs->Tool Options->AutoResize Window unchecked? I know it should be the same thing as what's in preferences but maybe it's not.
As for your second question, are you docking window dialogs or floating? If docked they shouldn't overlap but I work in float mode with dual monitors so I'm not sure. You can also try fiddling with the overall window maximize/minimize buttons.

---

### Post by JamButty on 2020-03-04
Auto-resize window on zoom tool is unchecked.
Resizing main window with single window mode unchecked, then enabled and edit-preferences-window management -"positions saved" got it back to what I had before.
Thanks sdsurfer!

---

