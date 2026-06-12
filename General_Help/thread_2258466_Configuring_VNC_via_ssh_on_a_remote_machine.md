---
title: "Configuring VNC via ssh on a remote machine"
date: 2014-12-27
forum: General Help
---

### Post by Billy_Martinez on 2014-12-27
Hello,  I'm trying to set up tightvnc on a machine via ssh, but when I connect to the machine I see a gray screen with an X as the mouse pointer.

1. I installed vnc from the command line: sudo apt-get install tightvncserver
2. This I started the server and configured the password with this command.  vncserver :1 -geometry 1024x768 -depth 16 -pixelformat rgb565
3. Then I opened up my vpn client and connected to the machine via the ip address and uses port 1 "10.0.0.223:1".

It asked me for a password which I inputed and then it said that the client detected a problem and asked me if I wanted to report it. I clicked cancel and then it gave me a gray screen with a X as the mouse pointer. 

Please help.

---

### Post by TheFu on 2014-12-28
That is the X/Windows "root" window.  You need to start a window manager or desktop environment.  Might be able to right click to see a menu and select one of those.  Or center-button click ... if the menu choices don't include those, maybe a terminal then you can manually launch the WM or DE of choice.

There are settings for VNC ... think they fit into a ~/.vnc/xstartup   at least for some VNC servers.
```
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
/usr/bin/xterm -sb  &
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession

```
is what I have. Haven't used it in years, so don't know for certain if this works. It does launch a terminal, so you can run whatever WM.

Over a LAN, I just use X/Windows forwarding with **ssh -X userid@servername program**. This is more secure than VNC. It is also more convenient if ssh-keys are used. Of course the machine I'm sitting behind is Linux and has X running. Not useful for Windows.

Over the internet, use **x2go** which is 2-3x more efficient than VNC and uses ssh tunnels automatically.  There is an x2go server and client. Only ssh needs to be setup for remote access and ssh-keys can/should be used for authentication. 

Trust me.  VNC really isn't desired anymore.  x2go is easier and more secure and more efficient.

---

### Post by Billy_Martinez on 2014-12-28
I'm a Linux newbie, so please bear with me. I have a macbook retina and an old PC with a fresh install of Lubuntu on it. What I want to be able to do is VNC into my old computer from my mac. 


> **TheFu said:**
> That is the X/Windows "root" window. You need to start a window manager or desktop environment. Might be able to right click to see a menu and select one of those. Or center-button click ... if the menu choices don't include those, maybe a terminal then you can manually launch the WM or DE of choice.

I did some research and found out that I needed the gnome desktop environment installed, I installed it (sudo apt-get install gdm) and reboot the machine and it still didn't work. 



You lost me a little bit when you started talking about the modifying this file.

> **TheFu said:**
> 

There are settings for VNC ... think they fit into a ~/.vnc/xstartup   at least for some VNC servers.
```
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
/usr/bin/xterm -sb  &
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession

```


---

### Post by steeldriver on 2014-12-28
gdm isn't the gnome desktop environment, it's the **g**nome **d**isplay **m**anager. You wouldn't need/use a display manager when starting a session via tightvnc

Basically your ~/.vnc/xstartup file should tell the tightvncserver how to start your desired desktop session. I use VNC tunnelled over SSH for my work - FWIW here is my xstartup file:

```

#!/bin/sh

MODE="lxde"

#Uncommment this line if using Gnome and your keyboard mappings are incorrect.
#export XKL_XMODMAP_DISABLE=1

# Load X resources (if any)
[ -r "$HOME/.Xresources" ] && xrdb "$HOME/.Xresources"

case $MODE in

xfce4)
    if which startxfce4 > /dev/null; then
        exec startxfce4 
    fi
    ;;

lxde)
    if which startlxde > /dev/null; then
        exec startlxde
    fi
    ;;

openbox)
    if which openbox-session > /dev/null; then
        exec openbox-session
    fi
    ;;

*)
    echo "Falling back to default minimal X session"
    ;;

esac

xsetroot -solid "#DAB082"
x-terminal-emulator -geometry "80x24+10+10" -ls -title " Desktop" &
x-window-manager &

```

The MODE=xxx line near the top and switch/case structure just lets me change between sessions conveniently - you don't really need anything that complicated. Note that I don't have a gnome desktop amongst them - I prefer to use the lighter-weight desktops when running over VNC (I never got the 3D unity desktop working at all).

---

### Post by TheFu on 2014-12-28
What is confusing about making a file?
Open it in any editor you like.
Copy/paste the lines shown.
Make the file permissions executable - chmod +x ~/.vnc/xstartup

Restart the vnc-server ... whatever it is called.
Try to connect from the vnc client ... be happy should be the result.


I still strongly suggest using x2go. There is an osx client, I understand.  Less hassle to get working.  Also, please follow Steeldriver's advice and use a minimal GUI, not Unity.  lxde, xfce or any plain WM work well.

---

