---
title: "Logging out when monitor is turned off"
date: 2021-01-11
forum: General Help
---

### Post by colinzealknows on 2021-01-11
I have Ubuntu 20.04 running on my desktop, with a Toshiba TV plugged in as a monitor through HDMI.
It's been half a year that it started actually logging off of my session when the TV is turned off. When I turn it back on, it shows "no signal" until I press Ctrl+Alt+F1, when the login screen shows up and I have to type in my password to get in.
I looked into absolutely every setting on Settings, all are good (automatic suspend = off, blank screen = never, blank screen delay = off, automatic screen lock = off, lock screen on suspend = off); on Tweaks there was a setting that some people said it mattered, "suspend when laptop lid is closed", changed that to off as well; followed steps on [this thread]("https://askubuntu.com/questions/1001198/screen-turning-off-when-idle-even-with-power-settings-disabled"), nothing changed as well.
It is driving me absolutely up the walls, I don't know what else to do. Please help. Thank you.

---

### Post by TheFu on 2021-01-11
Sorry, I have no clue,  but have these questions which might be relevant:[LIST]
[*]
[*]X11 or Wayland?
[*]What GPU?
[*]Which GPU drivers?
[*]Does the OS use dpms to turn off and on the monitor? Does the TV honor that?
[/LIST]

---

### Post by colinzealknows on 2021-01-11
> **TheFu said:**
> Sorry, I have no clue,  but have these questions which might be relevant:
[LIST]
[*]X11 or Wayland?
[*]What GPU?
[*]Which GPU drivers?
[*]Does the OS use dpms to turn off and on the monitor? Does the TV honor that?
[/LIST]


Thank you.
X11;
GeForce GT 1030;
Driver I think it's GP108? That's what it shows on lspci and lshw
Not sure about dpms, all I know is that I have this TV for years and I never had this issue before...

---

### Post by colinzealknows on 2021-01-13
Can anyone help me?

---

