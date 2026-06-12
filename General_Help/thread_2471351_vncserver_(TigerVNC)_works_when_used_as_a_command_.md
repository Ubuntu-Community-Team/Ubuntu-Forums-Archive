---
title: "vncserver (TigerVNC) works when used as a command but loads blank screen as a service"
date: 2022-01-27
forum: General Help
---

### Post by sgtbug on 2022-01-27
Hi,

I am facing a weird problem with TigerVNC running as a service.

My vncserver@.service file is:
```
[Unit]
Description=TigerVNC service (VNC)
After=syslog.target network.target

[Service]
Type=simple
User=user
PAMName=login
PIDFile=/home/%u/.vnc/%H%i.pid
ExecStartPre=/usr/bin/vncserver -kill :%i > /dev/null 2>&1 || :
ExecStart=/usr/bin/vncserver :%i -localhost no -geometry 1920x1080
ExecStop=/usr/bin/vncserver -kill :%i

[Install]
WantedBy=multi-user.target
```

my ~/.vnc/xstartup file is:
```
#!/bin/sh
exec /etc/vnc/xstartup
xrdb $HOME/.Xresources
vncconfig -iconic &
dbus-launch --exit-with-session gnome-session &
```

When I just plain run 'vncserver' from shell, and try to connect, it works without a problem.

However, when I try to connect when starting as a service from systemctl, it shows up a blank screen when connected on VNC.

What am I doing wrong?

---

### Post by HermanAB on 2022-01-27
Howdy,

To explain something:
VNC forwards a user desktop over the network.  To do that it has to run with the same user permissions as that user. That happens automatically when you launch it as a user from your desktop system.

A service launched by systemd runs before any user is logged in and it doesn’t run with user permissions.  Even if you would use su to launch it as your user, it still won’t work right since there is no desktop to forward yet.

---

### Post by sgtbug on 2022-01-27
> **HermanAB said:**
> Howdy,

To explain something:
VNC forwards a user desktop over the network.  To do that it has to run with the same user permissions as that user. That happens automatically when you launch it as a user from your desktop system.

A service launched by systemd runs before any user is logged in and it doesn&#8217;t run with user permissions.  Even if you would use su to launch it as your user, it still won&#8217;t work right since there is no desktop to forward yet.

Fair enough. Thanks for your reply!

People who have written these guides claim it works: [Source 1]("https://tecadmin.net/install-vnc-server-on-ubuntu-20-04/"), [Source 2]("https://bytexd.com/how-to-install-configure-vnc-server-on-ubuntu-20-04/")

What could I be missing here?

---

### Post by HermanAB on 2022-01-27
Sorry I’m not going to read that since I gave up with VNC many years ago already.  I use SSH for everything.  Ssh can do everything VNC does and more and it is secure too.

---

### Post by sgtbug on 2022-01-27
> **HermanAB said:**
> Sorry I’m not going to read that since I gave up with VNC many years ago already.  I use SSH for everything.  Ssh can do everything VNC does and more and it is secure too.

Yeah, I finally gave up and removed the DE entirely. Might install XFCE for some basic stuff..

---

