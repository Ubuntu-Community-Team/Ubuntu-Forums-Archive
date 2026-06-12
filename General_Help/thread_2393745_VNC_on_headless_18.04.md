---
title: "VNC on headless 18.04 ??"
date: 2018-06-07
forum: General Help
---

### Post by modomobo on 2018-06-07
I have a Ubuntu 18.04 desktop on a machine that I also want to use headless with VNC.

Got it working when a display is connected, but if no monitor attached the VNC connection is refused.

How can I make it work both when a monitor is attached and also without? I don't mind rebooting.

I have the **Screen Sharing** option turned on and my **.vnc/startup** file (probably wrong?) looks like this:

```
#!/bin/sh

export XKL_XMODMAP_DISABLE=1
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &

#xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#twm &

gnome-panel &
gnome-settings-daemon &
metacity &
nautilus &
gnome-terminal &
```

What do I need to change to get this to work?

Thanks in advance!

---

### Post by nlee2 on 2018-06-07
I believe that Screen Sharing aka vino-server uses xstartup. If disconnecting the monitor after connecting is not an acceptable solution then you can try installing tigervnc-standalone-server. Tigervnc does use xstartup. Rename your .vnc folder before installation. During config a new .vnc folder will be created with a default xstartup that should work.

---

### Post by modomobo on 2018-06-07
Starting the machine with a monitor and then disconnecting it is not an option.

I did what you suggested, and then tried starting the server by entering vncserver in the shell.

I get the following:

> vncserver: Failed command '/etc/X11/Xvnc-session': 256!

And

> Can't exec "/usr/bin/xterm": No such file or directory at /usr/bin/tigervncserver line 877.

And

>  vncext:      VNC extension running!
 vncext:      Listening for VNC connections on local interface(s), port 5901
 vncext:      created VNC server for screen 0
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1"
      after 175 requests (175 known processed) with 0 events remaining.
Killing Xtigervnc process ID 3064... which seems to be deadlocked. Using SIGKILL!

I tried restarting without a monitor and connecting via VNC, but I just get the same error as before.

Now what?

---

### Post by mastablasta on 2018-06-08
if it's "headless", why do you need a desktop then? desktop is there to help you interact with PC via monitor and input devices, if you are not using monitor then there is no point in having a desktop. 

if you need a GUI for server maintenance then it is better to use a webgui. there are plenty out there, but i would say Zentyal and Ajenti are both worth a look. or if you don't mind Debian then Openmediavault is good, while Nethserver works on the CentoS and is also aimed at users that want to avoid CLI as much as possible. there are also a bunch of other WEB GUIs available.

most server setup is done in config files so the GUI is not really that necessary, though it can come in handy.

---

### Post by modomobo on 2018-06-08
Well, I could explain the reasons for VNC, but they are tangential. I have Webmin installed already.

Is it not possible to just set up VNC on Ubuntu so that it works whether I have a monitor connected or not?

Should I be looking at a different distro with a community that can speak to this kind of issue?

---

### Post by nlee2 on 2018-06-08
What is the output of

ls -la ~/.vnc
cat ~/.vnc/thefilenamehere.log
cat ~/.vnc/xstartup

---

### Post by deadflowr on 2018-06-08
You usually need the xserver-xorg-video-dummy package if you want to run headless.

---

### Post by modomobo on 2018-06-08
Thanks much for your messages.

I tried installing xserver-xorg-video-dummy and then rebooting. No change.

The files look like this:

```
[COLOR=#000000][FONT=Monaco][COLOR=#34bc26]me@MyServer[/COLOR]:[COLOR=#5230e1]~[/COLOR]$ ls -la ~/.vnc[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]total 20[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]drwxr-xr-x  2 me me 4096 Jun  8 14:37 [COLOR=#5230e1].[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]drwxr-xr-x 22 me me 4096 Jun  8 18:03 [COLOR=#5230e1]..[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]-rw-r--r--  1 me me 5768 Jun  8 14:37 MyServer:1.log[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]-rw-------  1 me me    8 Jun  8 08:48 passwd[/FONT][/COLOR]

[COLOR=#000000][FONT=Monaco][COLOR=#34bc26]me@MyServer[/COLOR]:[COLOR=#5230e1]~[/COLOR]$ cat ~/.vnc/MyServer:1.log[/FONT][/COLOR]

[COLOR=#000000][FONT=Monaco]Xvnc TigerVNC 1.7.0 - built Dec  5 2017 09:25:01[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]Copyright (C) 1999-2016 TigerVNC Team and many others (see README.txt)[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]See [http://www.tigervnc.org](http://www.tigervnc.org) for information on TigerVNC.[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]Underlying X server release 11905000, The X.Org Foundation[/FONT][/COLOR]

[COLOR=#000000][FONT=Monaco]Fri Jun  8 08:48:59 2018[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco] vncext:      VNC extension running![/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco] vncext:      Listening for VNC connections on local interface(s), port 5901[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco] vncext:      created VNC server for screen 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1"[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]      after 175 requests (175 known processed) with 0 events remaining.[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]Killing Xtigervnc process ID 4044... which seems to be deadlocked. Using SIGKILL![/FONT][/COLOR]

[COLOR=#000000][FONT=Monaco][COLOR=#34bc26]me@MyServer[/COLOR]:[COLOR=#5230e1]~[/COLOR]$ cat ~/.vnc/xstartup[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco]cat: /home/me/.vnc/xstartup: No such file or directory[/FONT][/COLOR]

```
I guess the xstartup file is missing because I haven't gotten tigervnc to run without exiting?

Thanks again!

---

### Post by nlee2 on 2018-06-09
Normally xstartup in created when you run vncpasswd.

```

#!/bin/sh
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
exec gnome-session

```

---

### Post by modomobo on 2018-06-09
I tried **vncpasswd**. It didn't create ~/.vnc/xstartup.

I created the file using **nano**, and added the content suggested by nlee2 (above). Rebooted.

Tried **vncserver :1** to start the server (why doesn't it start by itself?).

Still can't connect from my vnc client.

Tried: **sudo netstat -nlp | grep 5901**

tcp        0      0 127.0.0.1:5901          0.0.0.0:*               LISTEN      1686/Xtigervnc      
tcp6       0      0 ::1:5901                :::*                    LISTEN      1686/Xtigervnc      

So, it's only listening on the loopback address? How do I get it to listen on the regular server address?

---

### Post by nlee2 on 2018-06-09
If vncserver is only listening on localhost then try using vncviewer over ssh. Otherwise use the xvnc -localhost option. If vncserver needs to start at boot then configure [email]vncserver@:1.servic[/email]e in systemd.

---

### Post by modomobo on 2018-07-01
After searching forums, I found that $localhost = "no"; in /etc/vnc.conf allows other hosts to connect.

At this point, I can start the server with vncserver :1 and connect from an iPad. :D

---

### Post by HermanAB on 2018-07-01
ExWindows users always want to use VNC, but it is really not good for remote administration.

The better way is to use SSH with X forwarding.  You can run any X program remotely and have the GUI pop up on your local desktop:
$ ssh -C -X user@server "gedit filename.txt"

---

### Post by donb21 on 2018-07-11
Have you considered adding a dummy plug onto the video output to make it think there's a monitor connected?

[https://rumorscity.com/2013/12/06/how-to-create-dummy-plugs-for-your-graphics-cards/](https://rumorscity.com/2013/12/06/how-to-create-dummy-plugs-for-your-graphics-cards/)

---

