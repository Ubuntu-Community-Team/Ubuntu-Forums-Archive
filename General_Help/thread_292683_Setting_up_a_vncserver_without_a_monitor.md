---
title: "Setting up a vncserver without a monitor?"
date: 2006-11-04
forum: General Help
---

### Post by speedsix on 2006-11-04
I have a Dapper machine (mythtv server with no monitor) which I want to connect to from my Edgy desktop machine.

I have installed vncserver on the server and vncviewer on my desktop but it refuses to connect. Is installing the vncserver package enough for the server to run or do I need to start it another way? 

Any ideas?



Thanks

---

### Post by justplayin on 2006-11-04
Hi, I'm no expert at this, but I once couldn't connect because I forgot to forward port 5900 on my router to the server and make sure there's no firewall blocking that port. 5900 is the default port vncviewer or server uses. When using a connection with vnc over the internet I make sure port forwarding for port 5900 is enabled on the server- and the client side.
Furthermore I greatly increased the performance of vnc by installing

```
vnc4server
vnc-common
```

on the server and

```
xvnc4viewer
```

on the client

as described [here.]("http://wiki.ubuntuusers.de/VNC")

on the client. It seems that these are different packages than the default vnc-packages that come shipped with the default ubuntu installation.

Do you use "vncviewer <IP-Adress of the server>:0" to connect to the server?

Maybe this is of some help.

---

