---
title: "[xfce] &quot;Window Buttons&quot; Multi-monitor support..."
date: 2016-04-18
forum: General Help
---

### Post by mehtuus on 2016-04-18
I am wondering if anyone else is having an issue with this as well.

**My System**:
[LIST]
[*]Xubuntu 15.10 (wily)
[*]Gnome 3.16.2
[*]Kernel 4.2.0-35-generic
[*]Window manager being used: XFCE
[*]Two monitors (main left side, secondary right side)
[*]Multiple panels configured (three)
[LIST]
[*]0 - Menu, system info, desktops, window buttons (1st monitor, top-left side of screen)
[*]1 - Weather widget, system tray, clock (1st monitor, top-right side of screen)
[*]2 - Window buttons (2nd monitor, top-right side of screen)
[/LIST]
[/LIST]

_The issue I am having is this_:
I have two [COLOR="#B22222"]Window Buttons[/COLOR] enabled. The first is on my main screen (panel 0), the second is on the other screen (panel 2). Both are configured to only show windows that are on their *own* screen. However, when the system is rebooted [COLOR="#B22222"]Window Buttons[/COLOR] in panel-0 on the main screen works fine, but the [COLOR="#B22222"]Window Buttons[/COLOR] in panel-2 on the second screen always shows only the windows from the main screen (same as [COLOR="#B22222"]Window Buttons[/COLOR] in panel-0) even though the option is still unchecked. At this point if I were to move a window from the main screen over to the second screen neither [COLOR="#B22222"]Window Buttons[/COLOR] would display the window.

The work around is to open the [COLOR="#B22222"]Window Buttons[/COLOR] settings on the second screen then *check* & *uncheck* the [COLOR="#B22222"]Show windows from all monitors[/COLOR] filtering setting. Doing this returns expected functioning to Window Buttons in panel-2 until the next reboot. Has anyone else noticed this odd behavior? 

Screenshots:
Normal: [http://i.imgur.com/cmHrsr3.jpg](http://i.imgur.com/cmHrsr3.jpg)
With Error: [http://i.imgur.com/aiX4ghQ.jpg](http://i.imgur.com/aiX4ghQ.jpg)

---

### Post by mehtuus on 2016-05-02
*bump*
Has anyone else noticed this issue?

---

