---
title: "VNC Server"
date: 2022-09-14
forum: General Help
---

### Post by mitchell2345 on 2022-09-14
I have a fresh install of ubuntu setup on my home server and for the life of me cannot get VNC to work.  I want to be able to access the GUI from my home PC to manage it.  Some relevant info:
```
mitchell@mythtv:~$ vncserver

New Xtigervnc server 'mythtv:1 (mitchell)' on port 5901 for display :1.
Use xtigervncviewer -SecurityTypes VncAuth -passwd /home/mitchell/.vnc/passwd :1 to connect to the VNC server.

```

```
mitchell@mythtv:~$ cat .vnc/xstartup
#!/bin/sh

#xrdb "$HOME/.Xresources"
#xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
#export XKL_XMODMAP_DISABLE=1
#/etc/X11/Xsession



#!/bin/sh
# Start Gnome 3 Desktop
#[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
#[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
#vncconfig -iconic &
#dbus-launch --exit-with-session gnome-session &
#!/bin/sh
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
exec startxfce4
mitchell@mythtv:~$

```
```

mitchell@mythtv:~$ vncserver -list

TigerVNC server sessions:

X DISPLAY #     RFB PORT #      RFB UNIX PATH   PROCESS ID #    SERVER
1               5901                            1945            Xtigervnc
mitchell@mythtv:~$

```
I have tried using vncviewer & tightvnc to *ip-address:5901* and neither will connect.  

Any help is appreciated.

---

### Post by TheFu on 2022-09-14
Don't use VNC, use x2go.  

But if you are on the same LAN, having a full remote desktop is really a waste. Use normal X11 forwarding and run the program on the remote system, but have it displayed on your local workstation.  This is how Unix people do things and has been about 40 yrs.

x2go is 2-3x faster than VNC or RDP while using ssh for security.  Trust me. It is easier, faster, and better.
Oh ... and none of them work with Gnome3/4 or KDE-Plasma desktops, so you'll need to pick a lighter DE - say  XFCE, LXQt, Mate, Cinnamon, really any DE/WM except Gnome3 or later or Plasma.  All remote desktops have this same issue, since those DEs decided that access to a GPU is almost mandatory.

Use x2go.  It is in the repos.  The only trick, if you want to call it that, is to setup ssh connections between the client and server BEFORE installing x2go.

---

### Post by HermanAB on 2022-09-15
Hmm, old users don’t bother with VNC or X2go and just use straight up SSH:  Much less hassle and it works well enough.

---

### Post by ActionParsnip on 2022-09-15
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04)

---

### Post by TheFu on 2022-09-15
> **HermanAB said:**
> Hmm, old users don’t bother with VNC or X2go and just use straight up SSH:  Much less hassle and it works well enough.

+100!  

I use x2go only when traveling and I don't want any sensitive data on the local machine. 

On the LAN, I use **ssh -X .... ** to run GUI programs on remote system and have the window displayed on my current workstation. Heck, this browser window is running on a different system using that method.  That's my standard method. Only a few programs are actually running locally.

---

### Post by mitchell2345 on 2022-09-15
> **TheFu said:**
> Don't use VNC, use x2go.  

But if you are on the same LAN, having a full remote desktop is really a waste. Use normal X11 forwarding and run the program on the remote system, but have it displayed on your local workstation.  This is how Unix people do things and has been about 40 yrs.

x2go is 2-3x faster than VNC or RDP while using ssh for security.  Trust me. It is easier, faster, and better.
Oh ... and none of them work with Gnome3/4 or KDE-Plasma desktops, so you'll need to pick a lighter DE - say  XFCE, LXQt, Mate, Cinnamon, really any DE/WM except Gnome3 or later or Plasma.  All remote desktops have this same issue, since those DEs decided that access to a GPU is almost mandatory.

Use x2go.  It is in the repos.  The only trick, if you want to call it that, is to setup ssh connections between the client and server BEFORE installing x2go.

this worked great and was super simple to setup. thanks!

---

