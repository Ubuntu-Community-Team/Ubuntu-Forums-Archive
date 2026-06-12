---
title: "Thumb scroll issue"
date: 2014-04-19
forum: General Help
---

### Post by dhogandrexler on 2014-04-19
So I have a mouse with a thumb-scroller. In 13.10 I had this setup to increase/decrease the system volume & it worked a charm. With the same exact setup in 14.04 it now only works when the mouse focus is on the desktop. For instance, it will not adjust the volume when my mouse is hovered over a browser (or any other) window. This is particularly annoying when I want to adjust the volume of a fullscreen video quickly. In some programs it seems to actually be accepting a 'scroll' input when available (such as vlc).

I'm really pretty baffled about this one. At first I had a little script that would increase/decrease the volume that would get run through the 'commands' plugin in compiz. After having this issue I changed it to use 'xdotool key XF86AudioRaiseVolume' thinking that because it was emulating keypresses it wouldn't have an issue with focus, but the results are the same.

So my question is; is there any way to maybe disable the 'scroll' command it is sending globally without disabling the wheel entirely? Or at least force the focus for the scroller to always be that of the desktop?

---

