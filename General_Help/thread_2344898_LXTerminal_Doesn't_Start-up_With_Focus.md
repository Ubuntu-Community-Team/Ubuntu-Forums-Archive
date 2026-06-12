---
title: "LXTerminal Doesn't Start-up With Focus"
date: 2016-11-28
forum: General Help
---

### Post by Tk007LwZFJW5ej on 2016-11-28
I have LXTerminal 0.2.0. When I start it up (either from the applications menu or with my keyboard shortcut), the window does not have focus. I have to click on the terminal window to establish focus. No other application does this.

---

### Post by vasa1 on 2016-11-28
I don't know why this is happening for you :confused:

You may be able to fix this by editing ~/.config/openbox/lubuntu-rc.xml.

Before you do, please backup this file just in case.

Open the file in a plain text editor.
Scroll down to near the very end of the file. You should see a line with just </applications> on it.
Just above that line, paste in this code:
```
    <application title="LXTerminal" class="Lxterminal" name="lxterminal">
      <focus>yes</focus>
    </application>

```
Save the file.
Open a terminal and run```
openbox --reconfigure
```Nothing should happen but this step is necessary so that Openbox knows you've made a change.
Close the terminal.
Now when you next open lxterminal, it should have focus.

*In case you get a pop-up when you run openbox --reconfigure, please switch back to your original lubuntu-rc.xml. We'll then need to examine your file for parsing errors.*

---

### Post by Tk007LwZFJW5ej on 2016-11-29
That didn't work.

I just found another application that has this problem: the text editor leafpad.

---

### Post by vasa1 on 2016-11-29
Post the output of```
ps -o pid,ppid,stime,time,command -u $USER
```
and```
echo -e "Version $(lsb_release -a)
Session: $DESKTOP_SESSION
Desktop: $XDG_CURRENT_DESKTOP
Window Manager: $(wmctrl -m | awk '/Name:/{print $2}')
Kernel info: $(uname -a)" 
```
Upload the entire contents of lubuntu-rc.xml to pastebin and post the access link here.

---

### Post by Tk007LwZFJW5ej on 2016-11-29
> **vasa1 said:**
> Post the output of```
ps -o pid,ppid,stime,time,command -u $USER
```

  PID  PPID STIME     TIME COMMAND
  936     1 08:16 00:00:00 /lib/systemd/systemd --user
  937   936 08:16 00:00:00 (sd-pam)
  950   875 08:16 00:00:00 /usr/bin/lxsession -s Lubuntu -e LXDE
 1066   950 08:16 00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/im-launch /usr/bin/lxsession -s Lubuntu -e LXDE
 1069     1 08:16 00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/im-launch /usr/bin/lxsession -s Lubuntu -e LXDE
 1070     1 08:16 00:00:00 /usr/bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
 1082     1 08:16 00:00:00 /usr/lib/gvfs/gvfsd
 1087     1 08:16 00:00:00 /usr/lib/gvfs/gvfsd-fuse /run/user/1000/gvfs -f -o big_writes
 1109   950 08:16 00:00:00 openbox --config-file /home/dk/.config/openbox/lubuntu-rc.xml
 1113   950 08:16 00:00:01 lxpanel --profile Lubuntu
 1115   950 08:16 00:00:00 pcmanfm --desktop --profile lubuntu
 1121     1 08:16 00:00:00 /usr/bin/ssh-agent -s
 1126     1 08:16 00:00:00 update-notifier
 1130     1 08:16 00:00:01 nm-applet
 1133     1 08:16 00:00:00 light-locker
 1141     1 08:16 00:00:00 /usr/lib/dconf/dconf-service
 1144     1 08:16 00:00:00 xfce4-power-manager
 1145     1 08:16 00:00:00 xfce4-power-manager
 1147     1 08:16 00:00:00 /usr/lib/i386-linux-gnu/xfce4/xfconf/xfconfd
 1165     1 08:16 00:00:00 /usr/bin/pulseaudio --start --log-target=syslog
 1179     1 08:16 00:00:00 /usr/lib/menu-cache/menu-cached /tmp/.menu-cached-:0-dk
 1200     1 08:16 00:00:00 /usr/lib/gvfs/gvfs-udisks2-volume-monitor
 1227     1 08:16 00:00:00 /usr/lib/gvfs/gvfs-goa-volume-monitor
 1239     1 08:16 00:00:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
 1245     1 08:16 00:00:00 /usr/lib/gvfs/gvfs-mtp-volume-monitor
 1250     1 08:16 00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
 1252     1 08:16 00:00:00 /usr/lib/i386-linux-gnu/indicator-application-service
 1264     1 08:16 00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.1 /org/gtk/gvfs/exec_spaw/0
 1374  1113 08:16 00:03:01 /usr/lib/firefox/firefox
 1405     1 08:16 00:00:00 /usr/lib/i386-linux-gnu/gconf/gconfd-2
 1473  1113 08:17 00:00:23 /usr/lib/thunderbird/thunderbird
 1562     1 08:18 00:00:00 /usr/lib/gvfs/gvfsd-http --spawner :1.1 /org/gtk/gvfs/exec_spaw/1
 1694   950 08:28 00:00:00 x-terminal-emulator
 1695  1694 08:28 00:00:00 gnome-pty-helper
 1696  1694 08:28 00:00:00 /bin/bash
 1720  1696 08:28 00:00:00 ps -o pid,ppid,stime,time,command -u dk


> 
and```
echo -e "Version $(lsb_release -a)
Session: $DESKTOP_SESSION
Desktop: $XDG_CURRENT_DESKTOP
Window Manager: $(wmctrl -m | awk '/Name:/{print $2}')
Kernel info: $(uname -a)" 
``` 

Version Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial
Session: Lubuntu
Desktop: LXDE
Window Manager: 
Kernel info: Linux lubuntu-sys 4.4.0-47-generic #68-Ubuntu SMP Wed Oct 26 19:39:59 UTC 2016 i686 i686 i686 GNU/Linux

No LSB modules are available.
The program 'wmctrl' is currently not installed. You can install it by typing:
sudo apt install wmctrl

> 
Upload the entire contents of lubuntu-rc.xml to pastebin and post the access link here.
  
[http://paste.ofcode.org/drfkb2dAaWLiKgnyxn9LNh](http://paste.ofcode.org/drfkb2dAaWLiKgnyxn9LNh)

---

### Post by vasa1 on 2016-11-29
Try changing
```
    <focusNew>no</focusNew>
```to
```
    <focusNew>yes</focusNew>
```
in
```

  <focus>
    <focusNew>no</focusNew>
    <!-- always try to focus new windows when they appear. other rules do
       apply -->
    <followMouse>no</followMouse>
    <!-- move focus to a window when you move the mouse into it -->
    <focusLast>yes</focusLast>
    <!-- focus the last used window when changing desktops, instead of the one
       under the mouse pointer. when followMouse is enabled -->
    <underMouse>no</underMouse>
    <!-- move focus under the mouse, even when the mouse is not moving -->
    <focusDelay>200</focusDelay>
    <!-- when followMouse is enabled, the mouse must be inside the window for
       this many milliseconds (1000 = 1 sec) before moving focus to it -->
    <raiseOnFocus>no</raiseOnFocus>
    <!-- when followMouse is enabled, and a window is given focus by moving the
       mouse into it, also raise the window -->
  </focus>

```

---

### Post by Tk007LwZFJW5ej on 2016-11-29
That worked. Thank you.

---

