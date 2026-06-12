---
title: "Concurrent remote GUI users - Any advise ?"
date: 2013-10-16
forum: General Help
---

### Post by mscag on 2013-10-16
Hi,

We are 5 programmers who need to connect remotely to a server (many CPU's and plenty of RAM) that we bought together. Some of us need to work with Eclipse IDE and do the programming/compiling on the server resources. One of us needs to run a virtual machine running Windows so that he will be able to use his simulator (which has to be run on Windows) all remotely.

I have been using/managing many headless Ubuntu Server for may years but all through SSH and CLI.

What would be the best approach ? UbuntuServer with GUI added, or UbuntuDesktop ? Which GUI ? How do we connect remotely and concurrently ?

Any advise ?

---

### Post by sudodus on 2013-10-16
I'm no expert in this field, but if you answer these questions, it might be easier to give advice.

What kind of security do you need? Will you connect only via LAN? I guess some simpler, faster but less secure system can be used if you are working in-house (using a LAN, and not the internet).

---

### Post by steeldriver on 2013-10-16
What you are describing sounds pretty much identical to what we do at my work - people will likely tell you that VNC is too slow to use outside a LAN  but I do this from home a few miles away and find it quite acceptable (I  have a ~25Mb/s residential cable service) provided I stick to one of  the lighter desktops. The box is currently running 13.04 with a selection of available desktops

```

$ ls /usr/share/xsessions/
LXDE.desktop  openbox.desktop  openbox-gnome.desktop  openbox-kde.desktop  twm.desktop  wmaker-common.desktop  xfce.desktop

```

We then have tightvncserver installed but restricted to local connections (i.e. the external VNC ports are closed), so the users SSH in with a tunnel and start a vncserver instance on an available display

```
vncserver -geometry 1728x1080 :9
```

We each pretty much pick a display # and stick with it which simplifies the tunnel setup because we know what remote port to tunnel when we initiate the SSH connection. You can keep the remote sessions running 24/7/365 (barring server downtime) so it's just a matter of tunneling in and connecting your VNC client - some clients such as Remmina even manage the tunneling for you so it really is one click.

---

### Post by mscag on 2013-10-16
Hi,

We'll be having only LAN connections, thus, a less secure environment is something  we can live with. 

From the responses, here is what I have understood. Please correct me if necessary : We can use Ubuntu Server with "tightvncserver" installed, and then have many/any of the GUI desktops "steeldriver" mentioned installed on top of them. And on the client side, VNC will be suitable as long as the connection is on a LAN. Also, we'll be able to create many users on the Ubuntu Server, and allow them to connect concurrently using any desktop they like.

Thanks for all the quick responses.

Regards.

---

### Post by sudodus on 2013-10-16
I think so, and it is an advantage to use a desktop environment with a light foot-print, but let us wait for *steeldriver*'s confirmation :-)

---

### Post by nerdtron on 2013-10-17
On the server, why not spin up a VM using kvm and libvirt? Then use the GUI tool virt-manager on your desktop (or on the developer's desktop pc) to manage the VMs on the server?
No GUI required on the server.

---

### Post by steeldriver on 2013-10-17
I don't think it really matters whether you start from  the Server version or the Desktop version - I just wouldn't recommend using the full compiz-based ubuntu-desktop remotely.

Regarding 'concurrency', the way I understand it VNC setups basically break down in 2 groups

[LIST=1]
[*]'desktop sharing' where other client sessions can view (and optionally interact with) a single session (usually the local X session on the box itself) 
[*]independent sessions on separate X *displays* - usually the local console is :0 or :1, then you can start remote sessions on :3, :4 etc. 
[/LIST]
Option (2) may be run off a headless box - but doesn't need to be if you already have a workstation you want to use for this. The 'tightvncserver' package is one implementation of (2), there's also vnc4server and maybe others. Each user starts his/her own vncserver - by default it selects the next available display, but you can request a particular display (which is easier, since it allows an SSH tunnel to be set up ahead of time). The server listens on a port corresponding to the display number e.g. display :4 listens on port 5900 + 4 = 5904 (5900 being the default port for VNC when used for sharing the primary local display). Users can set which desktop their session uses via a configuration file called ~/.vnc/xstartup

See [https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

---

### Post by mscag on 2013-11-03
Hi,

Just to let anyone know how I proceeded :

I have followed the link titled "Worked on Ubuntu Desktop for multiple concurrent users." at [http://rbgeek.wordpress.com/2012/06/25/how-to-install-vnc-server-on-ubuntu-server-12-04](http://rbgeek.wordpress.com/2012/06/25/how-to-install-vnc-server-on-ubuntu-server-12-04).

On a fresh Ubuntu 12.04.3 LTS Server, I installed tightVNCServer together with the Gnome-Core. 

Regards.[URL="http://rbgeek.wordpress.com/2012/06/25/how-to-install-vnc-server-on-ubuntu-server-12-04/"]

[/URL]

---

