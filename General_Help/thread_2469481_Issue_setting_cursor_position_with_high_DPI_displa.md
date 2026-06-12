---
title: "Issue setting cursor position with high DPI display"
date: 2021-11-30
forum: General Help
---

### Post by jwilm on 2021-11-30
Hello,

I've been running into an issue with a 4k display where applications that set the cursor position function incorrectly and cause the mouse to erroneously move twice. I can reliably make it happen on my machine using `xdotool mousemove 200 200` (or any pixel position). The observed behavior is that the cursor first moves to the requested position in *physical* pixels, and then when the mouse is moved ever so slightly, the cursor jumps to the same coordinates in *logical* pixels.

I have reproduced this in multiple desktop environments (Default for Ubuntu 20.04, i3wm) which makes me think it's something happening at the X server level. I haven't configured any DPI scaling by hand, this is all out of the box on Ubuntu 20.04. Not sure where to go from here and any help would be appreciated.

Thank you!

---

