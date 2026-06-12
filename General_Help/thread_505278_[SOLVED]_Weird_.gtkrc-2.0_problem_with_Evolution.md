---
title: "[SOLVED] Weird .gtkrc-2.0 problem with Evolution"
date: 2007-07-20
forum: General Help
---

### Post by nvteighen on 2007-07-20
This is strange: my .gtkrc-2.0 file is configured to show white fonts on my panels, but I've found out that Evolution's Preferences window uses the same font color used at the panels. I attach a screenshot with my message to see what I mean.

Here's my .gtkrc-2.0 file, is there something that may be badly written that may be the cause of this behaivor:

```

style "panel"
{
 fg[NORMAL] = "#ffffff"
# fg[PRELIGHT] = "#000000"
# fg[ACTIVE] = "#ffffff"
# fg[SELECTED] = "#000000"
# fg[INSENSITIVE] = "#8A857C"
# bg[NORMAL] = "#000000"
# bg[PRELIGHT] = "#dfdfdf"
# bg[ACTIVE] = "#D0D0D0"
# bg[SELECTED] = "#D8BB75"
# bg[INSENSITIVE] = "#EFEFEF"
# base[NORMAL] = "#ffffff"
# base[PRELIGHT] = "#EFEFEF"
# base[ACTIVE] = "#D0D0D0"
# base[SELECTED] = "#DAB566"
# base[INSENSITIVE] = "#E8E8E8"
# text[NORMAL] = "#161616"
# text[PRELIGHT] = "#000000"
# text[ACTIVE] = "#000000"
# text[SELECTED] = "#ffffff"
# text[INSENSITIVE] = "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"

```

Thanks in advance!

---

### Post by aJayRoo on 2007-07-20
My setup for white panel font is slightly different, inside my .gtkrc-2.0 files is:
```
# comment following line to revert to normal panel font style
include "/home/u0338982/.gnome2/panel-fontrc"
```
and then inside that included file (panel-fontrc inside the .gnome2 folder) is:
```
style "my_color"
{
fg[NORMAL] = "#E2E2E2"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
```
This sets my panel font to white (well a light grey actually) and does not affect the preferences menu in evolution at all (I just checked to make sure!). I hope this can be of some use to you.

---

### Post by nvteighen on 2007-07-20
Great, it worked! And your light grey looks much better than plain white.
Thank you!

---

