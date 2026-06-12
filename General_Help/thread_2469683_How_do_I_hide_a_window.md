---
title: "How do I hide a window?"
date: 2021-12-06
forum: General Help
---

### Post by kata88 on 2021-12-06
I'd like to hide a window (a Chromium window from a Selenium process) so that it also disappears from the task bar.
How can I do that in Ubuntu, either with a command or in C or C++?

---

### Post by HermanAB on 2021-12-06
You can try moving the unwanted window off-screen with xdotool.

---

### Post by TheFu on 2021-12-06
Don't use a task bar?  There are lots of window managers that don't have one.
However, you cannot remove it from the process table ... er ... without hacking the kernel.  This is how root-kits work to hide on systems.

I like the idea of moving the window to a different workspace.  I know this works:
```
xdotool set_desktop_viewport 1980 0
sleep 1s;
# move Firefox to a specific place and size
xdotool search --name "Mozilla Firefox" windowmove 100 143
```

I have a 1920x1200 monitor, so moving passed 1920 to 1980 is enough, then xdotool finds "firefox" and moves that window from whatever workspace it is on to the new  relative location in the new workspace.

You might want to iconify the browser at that point.  Some WMs can force all icons to be placed on a specific workspace.

The bad news, is that even after this, I still see firefox in the window list from other workspaces.  But my WM doesn't have any taskbar, so it only shows up when specifically asked.

---

### Post by kata88 on 2021-12-06
It's fine if it isn't gone from the process list, I just need it off the desktop.
I have trouble getting xdotool to move a window off the screen. If I specify negative coordinates or coordinates that are higher than my workspace size, it puts the window into a corner instead.
I found a way that works though: xdotool windowunmap makes a window disappear without terminating the application.

---

### Post by HermanAB on 2021-12-06
Hmm, xdotool is one of those utilities that one can use to drive an unsuspecting user stir crazy with a little background script...

---

### Post by dragonfly41 on 2021-12-06
There is another way I use .. 
Create an automation script which ..
maximises browser (selenium) window
moves cursor to browser top bar
right click
select Move to Workspace Down (moves Window off active workspace)

I use Actiona for such window operations and it can work with xdotool and other scripts (bash, python etc.).

Actiona is similar to AutoHotKey in Windows.
Action scripts are run using command .. actexec myscript.ascr

---

### Post by TheFu on 2021-12-06
xdotool probably doesn't work with Wayland, so when running with Xorg isn't available anymore, we'll need a different tool.  I use it and cnee to automate some website scaping on a weekly basis.

---

