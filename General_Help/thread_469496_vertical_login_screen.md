---
title: "vertical login screen?"
date: 2007-06-09
forum: General Help
---

### Post by m4v on 2007-06-09
there's a way for rotate the login screen? maybe running a "xrandr -o left" command somewhere?
I have a monitor that can rotate 90º and most of the time I use it vertically, so the login screen is always turned around, when I log the screen automatically switches to vertical.

Is not a real problem but is a bother to twist my head every time I need to log on or change user, the only times I need the screen horizontally is while watching a video fullscreen which isn't very common.

---

### Post by toobuntu on 2007-06-22
Option 2 below will give you a vertical logon screen.

modify /etc/X11/xorg.conf to allow for rotating the monitor:

gksudo gedit /etc/X11/xorg.conf or sudo vim /etc/X11/xorg.conf (use whichever text editor you prefer)

1. under "Devices" section, add the following in order to have an option in 'System->Preferences->Screen Resolution' to rotate the monitor:
Option "RandRRotation"
2. or, under "Devices" section, add the following in order to automatically rotate the monitor counterclockwise upon starting X:
Option "Rotate" "CCW"
3. note: when the monitor is rotated and using VMware (or other memory-intensive apps), there is a SIGNIFICANT increase in latency and overall slow performance.  it is not usable for me when rotated, and I have not found a solution yet.

Note: if using option 1, there should be a check box in 'System->Preferences->Screen Resolution to set the selected rotation as the default for the machine (i.e. same effect as option 2).

---

