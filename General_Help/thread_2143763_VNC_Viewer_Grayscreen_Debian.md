---
title: "VNC Viewer Grayscreen Debian"
date: 2013-05-10
forum: General Help
---

### Post by Sjoekeloe on 2013-05-10
Hi,

I've setup my vnc using this guide [http://tipupdate.com/vnc-server-on-linux/](http://tipupdate.com/vnc-server-on-linux/)
This is on [COLOR=#555555][FONT=Helvetica Neue]Debian-6.0-x86
[/FONT][/COLOR]
After following the instructions, the VPS was set-up perfectly.

But after a sudo reboot in putty. I get the typical gray screen + black cross.

I tried commands: vncserver, tightvncserver and [COLOR=#666666][FONT=andale mono]tightvncserver -geometry 1024x768 :1[/FONT][/COLOR]
But none of those seem to work, any suggestions? 

Thank you

---

### Post by Immolatus on 2013-05-10
What desktop environment is the server running?

---

### Post by Sjoekeloe on 2013-05-10
> **Immolatus said:**
> What desktop environment is the server running?

Hi thanks for the fast reply, I'm pretty basic at this.

It's from [www.reversehosts.com](www.reversehosts.com) OpenVZ

I'm trying to use gnome-desktop-environment

---

### Post by Sjoekeloe on 2013-05-10
Little bump if I may. this is how my xstartup looks like:

```

[COLOR=#666666][FONT=andale mono]#!/bin/shxrdb $HOME/.Xresources
[/FONT][/COLOR][COLOR=#666666][FONT=andale mono]xsetroot -solid grey
[/FONT][/COLOR][COLOR=#666666][FONT=andale mono]x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
[/FONT][/COLOR][COLOR=#666666][FONT=andale mono]# x-window-manager &
[/FONT][/COLOR][COLOR=#666666][FONT=andale mono]gnome-session &

```[/FONT][/COLOR]

---

### Post by Sjoekeloe on 2013-05-11
Anybody? :(

---

### Post by steeldriver on 2013-05-11
You seem to have a mix of minimal 'grey root window plus xterm' and 'full gnome-session' - afaik it needs to be one or the other (ideally you want your gnome-session as first choice, with a minimal xterm session as fallback)

If you want to keep it simple, try commenting out everything except the gnome-session - or you can try something like this (I take no credit for it - I stole it from somewhere on the web)

```

$ cat ~/.vnc/xstartup 
#!/bin/sh

# Change "GNOME" to "KDE" for a KDE desktop, or "" for a generic desktop
MODE="GNOME"

#Uncommment this line if using Gnome and your keyboard mappings are incorrect.
#export XKL_XMODMAP_DISABLE=1

# Load X resources (if any)
if [ -e "$HOME/.Xresources" ]
then
        xrdb "$HOME/.Xresources"
fi

# Try a GNOME session, or fall back to KDE
if [ "GNOME" = "$MODE" ]
then
        if which gnome-session >/dev/null
        then
                gnome-session --session=ubuntu-2d &
        else
                MODE="KDE"
        fi
fi

# Try a KDE session, or fall back to generic
if [ "KDE" = "$MODE" ]
then
        if which startkde >/dev/null
        then
                startkde &
        else
                MODE=""
        fi
fi

# Run a generic session
if [ -z "$MODE" ]
then
        xsetroot -solid "#DAB082"
        x-terminal-emulator -geometry "80x24+10+10" -ls -title "$VNCDESKTOP Desktop" &
        x-window-manager &
fi

```

---

### Post by Sjoekeloe on 2013-05-11
> **steeldriver said:**
> You seem to have a mix of minimal 'grey root window plus xterm' and 'full gnome-session' - afaik it needs to be one or the other (ideally you want your gnome-session as first choice, with a minimal xterm session as fallback)

If you want to keep it simple, try commenting out everything except the gnome-session - or you can try something like this (I take no credit for it - I stole it from somewhere on the web)

```

$ cat ~/.vnc/xstartup 
#!/bin/sh

# Change "GNOME" to "KDE" for a KDE desktop, or "" for a generic desktop
MODE="GNOME"

#Uncommment this line if using Gnome and your keyboard mappings are incorrect.
#export XKL_XMODMAP_DISABLE=1

# Load X resources (if any)
if [ -e "$HOME/.Xresources" ]
then
        xrdb "$HOME/.Xresources"
fi

# Try a GNOME session, or fall back to KDE
if [ "GNOME" = "$MODE" ]
then
        if which gnome-session >/dev/null
        then
                gnome-session --session=ubuntu-2d &
        else
                MODE="KDE"
        fi
fi

# Try a KDE session, or fall back to generic
if [ "KDE" = "$MODE" ]
then
        if which startkde >/dev/null
        then
                startkde &
        else
                MODE=""
        fi
fi

# Run a generic session
if [ -z "$MODE" ]
then
        xsetroot -solid "#DAB082"
        x-terminal-emulator -geometry "80x24+10+10" -ls -title "$VNCDESKTOP Desktop" &
        x-window-manager &
fi

```

Thanks for helping! I tried your 2 suggestions and it still didn't work, every odd. I'm gonna try a different OS on the VPS.

EDIT: works with Centos! ty again though

---

