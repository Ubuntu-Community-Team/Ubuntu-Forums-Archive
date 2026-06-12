---
title: "Ubuntu 14 and Tight VNC - Gray Screen"
date: 2015-02-02
forum: General Help
---

### Post by Billy_Martinez on 2015-02-02
Hello I'm trying to get tight vnc working on Ubuntu 14. I installed tightvncserver from the softtware repositories and it installed fine, but when I logged in remotely the only thing I got was a grey screen and cursor with a X on it. I did some research online and I wasn't able to find any website that could help me. I saw some sites that had scripts on them that I didn't understand. 

I really need this working because I use my Ubuntu machine for school. I want to be able to remotely log into my pc from work and from my university so that I can have access to my files. 

f someone could please help me I would really appreciate it.

---

### Post by steeldriver on 2015-02-02
What exactly didn't you understand about the scripts you found (I presume you're referring to ~/.vnc/xstartup scripts)?

---

### Post by Billy_Martinez on 2015-02-02
> **steeldriver said:**
> What exactly didn't you understand about the scripts you found (I presume you're referring to ~/.vnc/xstartup scripts)?

The solutions online gave script examples that I didn't understand. I tried copying them and pasting them into xstartup, killing the tightvnc service and starting it up again and I still had the grey screen.

---

### Post by Billy_Martinez on 2015-02-02
For example
> #!/bin/sh

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



---

### Post by steeldriver on 2015-02-02
You will need to make sure that the session(s) you are trying to invoke are actually installed on the machine - that particular example uses ubuntu-2d for example which I don't think is valid anymore (there may be a near equivalent via gnome-flashback, I've kind of lost track of all the various gnomes). Personally I'd use (in fact do use) one of the lighter desktops (LXDE) when operating via VNC.

Also, you do know that tightvnc is different from "Desktop Sharing" right? If you want to access the same desktop session locally  and remotely, you should probably be looking at the default vino-server

---

### Post by Billy_Martinez on 2015-02-02
> **steeldriver said:**
> You will need to make sure that the session(s) you are trying to invoke are actually installed on the machine - that particular example uses ubuntu-2d for example which I don't think is valid anymore (there may be a near equivalent via gnome-flashback, I've kind of lost track of all the various gnomes). Personally I'd use (in fact do use) one of the lighter desktops (LXDE) when operating via VNC.

Also, you do know that tightvnc is different from "Desktop Sharing" right? If you want to access the same desktop session locally  and remotely, you should probably be looking at the default vino-server

Which command would I have to use to use unity?

---

### Post by Billy_Martinez on 2015-02-02
Ok lets start with this, I enabled Vino on ubuntu and I tried to use tightvnc viewer to connect to the the session on port 5900 and it refused. This is what I'm saying VNC on ubuntu is very difficult to get setup and there are little to no resources available on the Internet to help people.

---

### Post by Billy_Martinez on 2015-02-03
For anyone that is having trouble setting up a remote connection to their ubuntu machine, I recommend that they use xrdp. XRDP uses the RDP protocol just like in Windows so you will be able to connect to your linux machine using the Microsoft Remote Desktop application. If you're on a mac you can just download the Remote Desktop application for OS X from Microsoft's website. Follow the video below, the setup is simple and it doesn't require you to know linux scripting to get it to work.The VNC support for linux users is limited so I highly recommend that all noobs stay away from VNC.

[https://www.youtube.com/watch?v=L1ay7toiJ6k](https://www.youtube.com/watch?v=L1ay7toiJ6k)

---

