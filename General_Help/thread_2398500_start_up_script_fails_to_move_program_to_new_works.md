---
title: "start up script fails to move program to new workspace (Ubuntu 16.04)"
date: 2018-08-13
forum: General Help
---

### Post by Robbyx on 2018-08-13
I can not get the 4th line of the following script to move the app to a new workspace when the script is run from the start applications menu. What should I change?

#!/bin/bash
gnome-terminal  --command=" /usr/local/xxx.ac/bin/run_ubuntu.sh"
wait
wmctrl -r XXX.AC -t 4


Note:
This runs a script that creates a window with gui app in it:
gnome-terminal  --command=" /usr/local/xxx.ac/bin/run_ubuntu.sh"

The wait command is intended to stop the script until the app is fully loaded, then, move the window to the 5th workspace. The move does not happen.

---

### Post by again? on 2018-08-14
Does the wmctrl command work if you run separately on a window?
What window manager are you using?
```
wmctrl -m
```
Number of desktops wmctrl sees...
```
wmctrl -d
```


Compiz only has one desktop with virtual workspaces in which case you
would move the window using wmctrl with coordinates.
ie
```
wmctrl -r [COLOR="#FF0000"]<windowname>[/COLOR] -e 0,[COLOR="#FF0000"]X,Y[/COLOR],-1,-1
```

---

### Post by Robbyx on 2018-08-17
Is this of help in getting to a solution?

wmctrl -m
Name: GNOME Shell
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: N/A


~$ wmctrl -d
0  * DG: 3840x1080  VP: 0,0  WA: 0,0 3840x1080  Workspace 1
1  - DG: 3840x1080  VP: N/A  WA: 0,0 3840x1080  
2  - DG: 3840x1080  VP: N/A  WA: 0,0 3840x1080  N/A

---

### Post by again? on 2018-08-17
It helps me help you because even though you posted in ubuntugnome I wasn't sure what desktop environment 
you were using since your using 16.04.

Firstly I would check that the wmctrl command works.
Start your terminal command and see if you can move the created GUI with wmctrl.

If your'e logging in to a Wayland session, wmctrl commands won't work.
```
**[COLOR="#006400"]test@Gubu:~$[/COLOR] echo $XDG_SESSION_TYPE**
wayland
```

However they do work if you log into an the Xorg session.

Workspaces in gnome-shell are by default dynamic (can be set to static), so I don't see how you are going to send to workspace 5
when your output shows only 3 workspaces.
I don't use gnome-shell but have it installed in a test partition and it shows only 2 workspaces on initial boot 
and my wmctrl output looks different than yours.
```
**[COLOR="#006400"]test@Gubu:~$[/COLOR] wmctrl -d**
0  * DG: 1680x1050  VP: 0,0  WA: 67,27 1613x1023  Workspace 1
1  - DG: 1680x1050  VP: N/A  WA: 67,27 1613x1023
```

This is how I use wmctrl to move a nautilus window.
Check session type, list desktops, list windows and lastly use widow list info in move command.
```
**[COLOR="#006400"]test@Gubu:~$[/COLOR] echo $XDG_SESSION_TYPE**
x11

**[COLOR="#006400"]test@Gubu:~$[/COLOR] wmctrl -d**
0  * DG: 1680x1050  VP: 0,0  WA: 0,27 1680x1023  Workspace 1
1  - DG: 1680x1050  VP: N/A  WA: 0,27 1680x1023 
 
**[COLOR="#006400"]test@Gubu:~$[/COLOR]wmctrl -xl**
0x02c00001  0 vivaldi-stable.Vivaldi-stable  Gubu [UbuntuGnome] start up script fails to move program to new workspace (Ubuntu 16.04) - Reply to Topic
0x03400007  0 nautilus.Nautilus     Gubu Home
0x03800006  0 gnome-terminal-server.Gnome-terminal  Gubu test@Gubu: ~

**[COLOR="#006400"]test@Gubu:~$[/COLOR] wmctrl -xa nautilus.Nautilus -t 1**
```

In relation to your script, doesn't the wait command pause the script till the previous command exits.
Maybe change to a sleep command for 1 or 2 secs.

---

### Post by Robbyx on 2018-08-19
robins@robins-desktop:~$ echo $XDG_SESSION_TYPE
x11
robins@robins-desktop:~$ wmctrl -d
0  - DG: 3840x1080  VP: N/A  WA: 0,0 3840x1042  Workspace 1
1  - DG: 3840x1080  VP: N/A  WA: 0,0 3840x1042  Workspace 2
2  * DG: 3840x1080  VP: 0,0  WA: 0,0 3840x1042  Workspace 3
3  - DG: 3840x1080  VP: N/A  WA: 0,0 3840x1042  Workspace 4
4  - DG: 3840x1080  VP: N/A  WA: 0,0 3840x1042  Workspace 5

I changed the wait to a pause, but it made no difference to workspace the app is loaded! It still went to Workspace 0

The app is moved to workspace 4 when I run, from the command line,  **wmctrl -r XXX.AC -t 4**

The CL in startup programs was /home/robins/vpn_move -p 10.
Removing the -p 10 do not make any difference to the app not being moved.

At present it does not move the app when run as part of the start applications. I assume it is something to do with the order in which the start apps are being run. How do I make an app run as the last startup app?

---

### Post by again? on 2018-08-19
Does the actual script work if you run it?
Maybe it's not continuing past your gnome terminal line, waiting for your gui to close.
Perhaps use "&" to allow it to continue.
Eg
```
#!/bin/bash
gnome-terminal --command=" /usr/local/xxx.ac/bin/run_ubuntu.sh" &
sleep 2
wmctrl -r XXX.AC -t 4
```

I thought you were using a bash script in startup applications to autostart your GUI, in which
case it doesn't have a **-p** option to delay startup.

If you want to delay the start of an application in startup applications,
edit it's .desktop file in ~/.config/autostart , adding the line...
```
X-GNOME-Autostart-Delay=10
```

---

