---
title: "which workspace am i in"
date: 2019-10-15
forum: General Help
---

### Post by Skaperen on 2019-10-15
the [COLOR=#0000cd][FONT=courier new]**wmctrl -d**[/FONT][/COLOR] command lists managed desktops and flags the active desktop (workspace). with that, it is possible to simply getthe number of the active desktop, even if it runs in some other desktop.  what i really want to get is which desktop the program is running in.  does anyone know a way to do that?  one use of that would be a script to temporarily jump to another desktop then jump back.

---

### Post by dragonfly41 on 2019-10-16
I have docky installed with open app buttons at bottom of screen.
In docky settings > Docklets I enabled plugin Workspace Switcher.
This shows a grid of virtual workspaces. 
You can then click on cells in the grid to switch workspaces.

---

### Post by Holger_Gehrke on 2019-10-16
'wmctrl -l' gives a list of all windows the window manager is working with. Output is in at least four columns depending on options in use. First column is the id of the window, then the desktop (zero-based, -1 means window is on all desktops), next to last is the hostname the client runs on and last is the title of the window. Another way if you know the id of a window is 'xprop -id put_id_here _NET_WM_DESKTOP'.

Holger

---

### Post by Skaperen on 2019-10-16
so the next question is: how can a shell script or Python script or C program running under a terminal like xfce4-terminal (as opposed to an SSH session) determine its window ID?  i just verified that it's not in an environment variable.  IMHO, terminal programs should put this in an environment variable.

---

### Post by Holger_Gehrke on 2019-10-17
See the manual for wmctrl. 'wmctrl -l -p' has the PID of the process that owns a window as it's third column.

Holger

---

### Post by Skaperen on 2019-10-17
> **Holger_Gehrke said:**
> See the manual for wmctrl. 'wmctrl -l -p' has the PID of the process that owns a window as it's third column.

Holger

combining that and my [COLOR=#0000cd][FONT=courier new]_**ptb**_[/FONT][/COLOR] script (_P_ID _t_race _b_ack) lets a script find out what workspace it is in.
```

lt2a/forums /home/forums 15> wmctrl -l -p
0x00c00004 -1 3547   lt2a xfce4-panel
0x00a00003 -1 3551   lt2a Desktop
0x03200003  1 3718   lt2a Terminal
0x03400003  2 3839   lt2a Terminal
0x03600003  3 3965   lt2a Terminal
0x03800003  4 4086   lt2a Terminal
0x03a00003  9 17900  lt2a [xubuntu] which workspace am i in - Reply to Topic - Mozilla Firefox
lt2a/forums /home/forums 16> ptb $$
  PID TTY      STAT   TIME COMMAND
 3722 pts/7    Ss     0:00 bash
 3718 ?        Sl     0:02 xfce4-terminal --disable-server --hide-toolbar --hide-menubar --geometry=137x36+0+0 --font=18
    1 ?        Ss     0:01 /sbin/init splash
lt2a/forums /home/forums 17>

```

---

