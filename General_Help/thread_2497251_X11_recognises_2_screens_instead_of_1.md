---
title: "X11 recognises 2 screens instead of 1"
date: 2024-04-28
forum: General Help
---

### Post by Wise Ferret on 2024-04-28
Ubuntu noble, using nvidia 550 driver.
I have one monitor only. However, x11 recognises two screens (or is it displays? or monitors?), and places one of them to the right of my actual screen.
This causes several issues. I can "lose" my mouse pointer at the right hand side of my actual screen. Some apps start on the non-existent screen, and it is hard or impossible (in case of some steam games) to pull them out into my actual screen.
Gnome settings shows the two screens, my real screen first and the non-existent one second. The non-existant screen appears as idsabled, but apparently it is not (it shows two screens pn wayland sessions too, but there it behaves and does not create an extra imaginary screen to the side). It won't let me activate it either. It seems that xrandr sees this screen too:
```
$ xrandr -q
Screen 0: minimum 8 x 8, current 7680 x 2160, maximum 32767 x 32767
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 600mm x 340mm
   3840x2160     60.00*+  30.00  
   2560x1440     59.95  
   1920x1080     60.00    59.94  
   1600x900      60.00  
   1280x1024     60.02  
   1280x800      59.81  
   1280x720      60.00    59.94  
   1152x864      59.96  
   1024x768      60.00  
   800x600       60.32  
   720x480       59.94  
   640x480       59.94    59.93  
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
None-1-1 connected (normal left inverted right x axis y axis)
   3840x2160     60.00 +

```
But I cannot remove the extra screen with xrandr:
```
$ xrandr --output None-1-1 --off
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  7 (RRSetScreenSize)
  Serial number of failed request:  45
  Current serial number in output stream:  47

```
This is the content of /sys/class/drm:
```
$ ls /sys/class/drm
card0  card0-Unknown-1  card1  card1-DP-1  card1-DP-2  card1-HDMI-A-1  card1-HDMI-A-2  renderD128  version
```
Any idea? What should I delete to have only one screen and eliminate the problem?

---

### Post by TheFu on 2024-04-28
Just a shot in the dark, try **lxrandr** and disable the "extend desktop" setting.  BTW, if wayland is used, I don't think any of this X11 stuff works.

When I shift to the right, that takes me to a different workspace, not a different display.  Multiple workspaces have been common in Linux for 25+ yrs. They are provided by the Window Manager.  I use a 3x1 workspace now, but in the old days, I used a 3x3 workspace to keep different tasks on different workspaces.  Mostly these days, I use an empty workspace to share my screen while teaching without having to close/minimize all the other open windows.  xrandr/lxrandr don't have anything to do with workspace management, BTW.  It is 100% controlled by the WM and/or DE being used.

---

### Post by Wise Ferret on 2024-04-29
lxrandr shows the two monitors, the real one (DP-0) and the unreal one (None-1-1). The unreal one is marked as disabled. When I enable it and press Save, I get the error "xrandr: Configure crtc 4 failed".
lxrandr shows no "extend desktop" option on my system. It shows a "Location" drop lists for the two monitors which are grayed out.
I don't think this has anything to do with workspaces. Those work just fine. The problem is that my system believes I have an invisible second monitor, adjascent to my current one (I cannot access it, I know it's there because my mouse pointer gets lost in there when I move it beyond the right border of my real monitor), without any apparent way to tell it I do not.

---

### Post by TheFu on 2024-04-29
lxrandr "Save" hasn't ever worked to my knowledge.  I use it to setup presentation modes on my laptop when giving presentations at LUGs around here.  I've never seen what you describe.  OTOH, I haven't had nVidia on a laptop, er .... ever and removed an nVidia GPU from my Ryzen desktop by switching to a "G" model APU 2 and 3 yrs ago.  I was looking forward to having nVidia driver issues gone from my life.  That goal was definitely achieved.

Would you be willing to use the non-proprietary drivers and test again?  Need to isolate the issue.  Is is all nvidia drivers or just 550 or the card that is the issue?  Does this problem happen when you boot from an ISO in "Try Ubuntu" mode?  If not, then the problem is with the settings on your system, not the card.  Lots of ways to isolate the exact problem.   Does the GPU have any jumpers to disable different outputs?  IDK, just guessing.

---

