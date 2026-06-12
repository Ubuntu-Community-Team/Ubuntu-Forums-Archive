---
title: "VNC server can't see kde"
date: 2006-11-27
forum: General Help
---

### Post by d1sturbanc3 on 2006-11-27
I'm being trying to switch e-mail checking to my linux box, and trying to setup a remote desktop to it so I can see my mail.

I installed kubuntu Dapper.

Right now whenever I log into using realvnc on my windows machine I see the X window. I don't see kde window.

I think it might b/c I'm logging in as root, and there is no kde setup for root. But I tried user to the correct account, and I can't log in at all.

This is Xvnc file. Help? Thank you!!

```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901
}
```

---

