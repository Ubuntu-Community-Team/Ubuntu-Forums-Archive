---
title: "VNC grey screen"
date: 2015-11-13
forum: General Help
---

### Post by Billy_Martinez on 2015-11-13
Hello, I'm trying to get TightVNC working on a remote machine that's running Lubuntu. I checked out this page [https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers), and I was able to successfully setup a tunnel between my computer and the other machine. When I open up vnc viewer on my machine and point it to port 5901 on my localhost page 'localhost:5901' and it connects, but I get a grey screen with an X on it. On Ubuntu's VNC site it says that I have to configure the X startup file, like this 

> 
[FONT=inherit][COLOR=#008000][FONT=inherit]#!/bin/sh[/FONT][/COLOR][/FONT]

[FONT=inherit][COLOR=#008000][FONT=inherit]# Change "GNOME" to "KDE" for a KDE desktop, or "" for a generic desktop[/FONT][/COLOR][/FONT]
[FONT=inherit][FONT=inherit]MODE[/FONT]=[COLOR=#004080][FONT=inherit]"[/FONT][/COLOR][COLOR=#004080][FONT=inherit]GNOME[/FONT][/COLOR][COLOR=#004080][FONT=inherit]"[/FONT][/COLOR][/FONT]

[FONT=inherit][COLOR=#008000][FONT=inherit]#Uncommment this line if using Gnome and your keyboard mappings are incorrect.[/FONT][/COLOR][/FONT]
[FONT=inherit][COLOR=#008000][FONT=inherit]#export XKL_XMODMAP_DISABLE=1[/FONT][/COLOR][/FONT]

[FONT=inherit][COLOR=#008000][FONT=inherit]# Load X resources (if any)[/FONT][/COLOR][/FONT]
[FONT=inherit][COLOR=#A00000][FONT=inherit]if[/FONT][/COLOR] [ -[FONT=inherit]e[/FONT] [COLOR=#004080][FONT=inherit]"[/FONT][/COLOR][COLOR=#004080][FONT=inherit]$HOME/.Xresources[/FONT][/COLOR][COLOR=#004080][FONT=inherit]"[/FONT][/COLOR] ][/FONT]
[FONT=inherit][FONT=inherit]then[/FONT][/FONT]
[FONT=inherit]        [FONT=inherit]xrdb[/FONT] [COLOR=#004080][FONT=inherit]"[/FONT][/COLOR][COLOR=#004080][FONT=inherit]$HOME/.Xresources[/FONT][/COLOR][COLOR=#004080][FONT=inherit]"[/FONT][/COLOR][/FONT]
[FONT=inherit][FONT=inherit]fi[/FONT][/FONT]

[FONT=inherit][COLOR=#008000][FONT=inherit]# Try a GNOME session, or fall back to KDE[/FONT][/COLOR][/FONT]
[FONT=inherit][COLOR=#A00000][FONT=inherit]if[/FONT][/COLOR] [ [COLOR=#004080][FONT=inherit]"[/FONT][/COLOR][COLOR=#004080][FONT=inherit]GNOME[/FONT][/COLOR][COLOR=#004080][FONT=inherit]"[/FONT][/COLOR] = [COLOR=#004080][FONT=inherit]"[/FONT][/COLOR][COLOR=#004080][FONT=inherit]$MODE[/FONT][/COLOR][COLOR=#004080][FONT=inherit]"[/FONT][/COLOR] ][/FONT]
[FONT=inherit][FONT=inherit]then[/FONT][/FONT]
[FONT=inherit]        [COLOR=#A00000][FONT=inherit]if[/FONT][/COLOR] [FONT=inherit]which[/FONT] [FONT=inherit]gnome[/FONT]-[FONT=inherit]session[/FONT] >/[FONT=inherit]dev[/FONT]/[FONT=inherit]null[/FONT][/FONT]
[FONT=inherit]        [FONT=inherit]then[/FONT][/FONT]
[FONT=inherit]                [FONT=inherit]gnome[/FONT]-[FONT=inherit]session[/FONT] --[FONT=inherit]session[/FONT]=[FONT=inherit]ubuntu[/FONT]-[COLOR=#0080C0][FONT=inherit]2[/FONT][/COLOR][FONT=inherit]d[/FONT] &[/FONT]
[FONT=inherit]        [COLOR=#A00000][FONT=inherit]else[/FONT][/COLOR][/FONT]
[FONT=inherit]                [FONT=inherit]MODE[/FONT]=[COLOR=#004080][FONT=inherit]"[/FONT][/COLOR][COLOR=#004080][FONT=inherit]KDE[/FONT][/COLOR][COLOR=#004080][FONT=inherit]"[/FONT][/COLOR][/FONT]
[FONT=inherit]        [FONT=inherit]fi[/FONT][/FONT]
[FONT=inherit][FONT=inherit]fi[/FONT][/FONT]

[FONT=inherit][COLOR=#008000][FONT=inherit]# Try a KDE session, or fall back to generic[/FONT][/COLOR][/FONT]
[FONT=inherit][COLOR=#A00000][FONT=inherit]if[/FONT][/COLOR] [ [COLOR=#004080][FONT=inherit]"[/FONT][/COLOR][COLOR=#004080][FONT=inherit]KDE[/FONT][/COLOR][COLOR=#004080][FONT=inherit]"[/FONT][/COLOR] = [COLOR=#004080][FONT=inherit]"[/FONT][/COLOR][COLOR=#004080][FONT=inherit]$MODE[/FONT][/COLOR][COLOR=#004080][FONT=inherit]"[/FONT][/COLOR] ][/FONT]
[FONT=inherit][FONT=inherit]then[/FONT][/FONT]
[FONT=inherit]        [COLOR=#A00000][FONT=inherit]if[/FONT][/COLOR] [FONT=inherit]which[/FONT] [FONT=inherit]startkde[/FONT] >/[FONT=inherit]dev[/FONT]/[FONT=inherit]null[/FONT][/FONT]
[FONT=inherit]        [FONT=inherit]then[/FONT][/FONT]
[FONT=inherit]                [FONT=inherit]startkde[/FONT] &[/FONT]
[FONT=inherit]        [COLOR=#A00000][FONT=inherit]else[/FONT][/COLOR][/FONT]
[FONT=inherit]                [FONT=inherit]MODE[/FONT]=[COLOR=#004080][FONT=inherit]"[/FONT][/COLOR][COLOR=#004080][FONT=inherit]"[/FONT][/COLOR][/FONT]
[FONT=inherit]        [FONT=inherit]fi[/FONT][/FONT]
[FONT=inherit][FONT=inherit]fi[/FONT][/FONT]

[FONT=inherit][COLOR=#008000][FONT=inherit]# Run a generic session[/FONT][/COLOR][/FONT]
[FONT=inherit][COLOR=#A00000][FONT=inherit]if[/FONT][/COLOR] [ -[FONT=inherit]z[/FONT] [COLOR=#004080][FONT=inherit]"[/FONT][/COLOR][COLOR=#004080][FONT=inherit]$MODE[/FONT][/COLOR][COLOR=#004080][FONT=inherit]"[/FONT][/COLOR] ][/FONT]
[FONT=inherit][FONT=inherit]then[/FONT][/FONT]
[FONT=inherit]        [FONT=inherit]xsetroot[/FONT] -[FONT=inherit]solid[/FONT] [COLOR=#004080][FONT=inherit]"[/FONT][/COLOR][COLOR=#004080][FONT=inherit]#DAB082[/FONT][/COLOR][COLOR=#004080][FONT=inherit]"[/FONT][/COLOR][/FONT]
[FONT=inherit]        [FONT=inherit]x[/FONT]-[FONT=inherit]terminal[/FONT]-[FONT=inherit]emulator[/FONT] -[FONT=inherit]geometry[/FONT] [COLOR=#004080][FONT=inherit]"[/FONT][/COLOR][COLOR=#004080][FONT=inherit]80x24+10+10[/FONT][/COLOR][COLOR=#004080][FONT=inherit]"[/FONT][/COLOR] -[FONT=inherit]ls[/FONT] -[FONT=inherit]title[/FONT] [COLOR=#004080][FONT=inherit]"[/FONT][/COLOR][COLOR=#004080][FONT=inherit]$VNCDESKTOP Desktop[/FONT][/COLOR][COLOR=#004080][FONT=inherit]"[/FONT][/COLOR] &[/FONT]
[FONT=inherit]        [FONT=inherit]x[/FONT]-[FONT=inherit]window[/FONT]-[FONT=inherit]manager[/FONT] &[/FONT]
[FONT=inherit][FONT=inherit]fi[/FONT][/FONT]

I see the settings in that config file for gnome and KDE, but I don't know what to put for LXDE.

---

### Post by Billy_Martinez on 2015-11-14
Can someone please explain to me what the which statement in this script means? Also, why is it pointing gnome-*[FONT=inherit]session[/FONT] *into the null device?


*[FONT=inherit]session[/FONT] *[COLOR=#000000][FONT=inherit]*[COLOR=#A00000][FONT=inherit]if[/FONT][/COLOR] [FONT=inherit]which[/FONT] [FONT=inherit]gnome[/FONT]-[FONT=inherit]session[/FONT] >/[FONT=inherit]dev[/FONT]/[FONT=inherit]null[/FONT]*[/FONT][/COLOR]

---

### Post by steeldriver on 2015-11-14
The 'which' command searches your PATH for executable files matching the names of the  arguments

In this context, it's just testing in turn whether the executables gnome-session or startkde can be run on your system, and then executing the first one that is found

The '> /dev/null' just redirects any output from 'which' to a black hole (we don't care what it says - we are just interested in the numeric output status of the command)

IIRC the equivalent for a plain LXDE session would be 

```

        if which startlxde > /dev/null
        then
          startlxde
        .
        .
        .

```

---

### Post by Billy_Martinez on 2015-11-14
> **steeldriver said:**
> The 'which' command searches your PATH for executable files matching the names of the  arguments

In this context, it's just testing in turn whether the executables gnome-session or startkde can be run on your system, and then executing the first one that is found

The '> /dev/null' just redirects any output from 'which' to a black hole (we don't care what it says - we are just interested in the numeric output status of the command)

IIRC the equivalent for a plain LXDE session would be 

```

        if which startlxde > /dev/null
        then
          startlxde
        .
        .
        .

```

Thanks for your help

---

