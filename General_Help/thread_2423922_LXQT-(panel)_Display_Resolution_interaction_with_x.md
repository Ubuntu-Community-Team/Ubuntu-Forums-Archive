---
title: "LXQT-(panel) Display Resolution interaction with xrandr"
date: 2019-07-31
forum: General Help
---

### Post by atannert on 2019-07-31
Hello,

I am using LUbuntu 19.04 with an old Netbook. The screen resolution is 1024x600. Because of some problems with scrolling maximized windows with Alt-Leftmousebutton I would like to use a virtual screen resolution.

This is no problem with e.g. xrandr --output LVDS1 --panning 1920x1080

The problem is, the LXQt doesn't recognize the new virtual resolution. The lxqt-panel is always at the position bottom of 1024x600. If I maximize a window it maximizes to the 1920x1080 resolution and the panel is fixed above the window. Usable but annoying.

Is there a way to force the lxqt-panel to use the full virtual resolution?

Similar problem with xrandr --output LVDS1 --scale 1.875x1.8

Its like 4 small desktops instead of one scaled from 1920x1080 to 1024x600.

Same question: is the a way to fix the lxqt-panel position and size?


Best regards

---

### Post by guiverc on 2019-07-31
I'm currently looking at this, however the hurdle I think could be [https://github.com/lxqt/lxqt/issues/1175#issuecomment-254019597](https://github.com/lxqt/lxqt/issues/1175#issuecomment-254019597)   (this link came from @HMollerCl)

ie. Tsujan's comment   (Tsujan is an upstream LXQt dev)

*[COLOR=#24292E][FONT=-apple-system]Detecting virtual desktops and viewports is quite easy but adds an X11 dependency, which I don't think anyone approves of. Conversely, it's preferable to remove X11 dependency from apps as far as possible because "wayland will come."[/FONT][/COLOR]*

---

### Post by atannert on 2019-08-01
Hello,

thanks quiverc for the info. I read the thread. So the short answer is until now there is no way and perhaps this is wanted to remove dependency. 

My first thought was to implement the virtual screen before lxqt-panel starts with the hope that then lxqt-panel will detect the virtual screen as a real screen. But I think this won't work after reading your hint.

The starting point of the problem for me is muon. I maximize the muon window and it doesn't look nice but i can work with it. But if I mark a package for installing the window of muon change it's size and becomes bigger than the screen (The window cannot resized in width to 1024 because there is a kind of minimal width). And because it is maximized it cannot moved by mouse. So I have to resize it and then I can at least move it. Annoying. That's why I thought of the virtual screen. And the next problem occurs... .

Small screens are getting a bigger problem that's why I think the possibility the virtual screen size of the X11 is fantastic when it is supported by the desktop manager.

---

### Post by guiverc on 2019-08-01
Filed upstream (mostly as feature request, added here mostly for completeness)

[https://github.com/lxqt/lxqt/issues/1735](https://github.com/lxqt/lxqt/issues/1735)

---

### Post by atannert on 2019-08-01
Hey,

I found a way to get what I want. I don't know how specific this way is because of the hardware. I am using a Samsung N150 Netbook.

When I use the following commands

xrandr --addmode VIRTUAL1 1024x600
xrandr --output VIRTUAL1 --mode 1024x600 --left-of LVDS1 (the the background image becomes wider and I have to move the conole back to the visible screen)
xrandr --output LVDS1 --mode 1024x600 --fb 1920x1080 --panning 1920x1080

Then I have a virtual resolution 1920x1080 with the panel at the bottom of the virtual screen resolution full 1080 pixels wide and the background image is also scaled to 1920x1080

In the LXQt Monitor Settings there are some new items "Fast Menu" "Set position" and "VIRTUAL1" besides the old "LVDS1"

This is the minimum of commands I found to get what I want. I don't understand why this works.

Best regards

PS @guiverc perhaps you can ship that info to GitHub
PPS Already done because I remebered my GitHub login data :-)

---

### Post by guiverc on 2019-08-01
Thanks @atannert for posting upstream (github), on which there have been a number of posts..

I'm pleased you already have a solution  :), but I'll add Tsujun's latest (*added here mostly for completeness*)

[COLOR=#24292E][FONT=-apple-system]"*For now, the easiest workaround is restarting lxqt-panel and pcmanfm-qt*"[/FONT][/COLOR]

---

