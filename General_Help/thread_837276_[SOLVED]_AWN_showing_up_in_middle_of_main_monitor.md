---
title: "[SOLVED] AWN showing up in middle of main monitor"
date: 2008-06-22
forum: General Help
---

### Post by Redenbacher on 2008-06-22
As said in the title, AWN is showing up in the middle of my main monitor, not resting on the bottom as it should. I just turned on TwinView for my dual monitor set-up instead of having 2 separate X sessions.

Screen 1 is 1440x900, Screen 2 is 1280x1024. Since I set them both to have a colinear bottom on nvidia-settings (a colinear top is default), AWN has moved up from the bottom and is floating mid-screen (attached is a screenshot).

How can I resolve this? Is there some kind of coordinate system that lies in a file that can be edited?

Thanks in advance for your help!


EDIT: To fix this issue I had to set the second, 1280x1024 monitor as the primary in nvidia-settings.

---

### Post by isaacj87 on 2008-06-23
My guess is AWN is misinterpreting the resolution of the first screen...

Try this...

Press alt+f2 and type "gconf-editor" (without the quotes of course)

Then navigate to apps->avant-window-navigator and over on the right you see the keys "monitor height" and "monitor width" modify those values to your resolution. You might have to turn on the "Force Monitor" option as well.

Hope that works for you :D

---

