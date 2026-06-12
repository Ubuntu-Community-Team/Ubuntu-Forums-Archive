---
title: "GMD don't start in VNC session"
date: 2007-06-08
forum: General Help
---

### Post by ikus060 on 2007-06-08
I setup a month a go, a VNC server with inet. Last week the server crash due to a power failure. When we restart the server there was alot of corruption in the service prodive by this server. Every service are now up, except the VNC server (I'm the only one who use it). Now that I have some free time, I want to reconfig the VNC server.

Here are every config that (I know) is related to the VNC server :
/etc/xinetd.d/Xvnc
```

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = no
        user = root
        server = /usr/bin/Xvnc
        server_args = :1 -inetd -once -query localhost -geometry 1024x768 -depth 16 -desktop kira -IdleTimeout 1800 -log *:stdout:50 -securitytypes=none
        port = 5901
}


```

/etc/gmd/gdm.conf
```

[...]

[deamon]
# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
RemoteGreeter=/usr/lib/gdm/gdmlogin

[...]

[security]
DisallowTCP=false

[...]

[xdmcp]
Enable=true


```

Here a screen shot of what I see when I log in with VNC.
[IMG]http://img355.imageshack.us/img355/6112/screenshottx3.png[/IMG]

---

### Post by Damanther on 2007-06-15
Do you have a /root/.vnc/.vncstartup file?

If so, which display manager does it 'attempt' to start?

---

