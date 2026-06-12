---
title: "Free Domain name for VNC?"
date: 2008-05-15
forum: General Help
---

### Post by seeker1458 on 2008-05-15
Hey guys, I want to set up a remote desktop connection for a friend of mine.  She runs a small business from her home, and has another employee that works in a different city.  She just wants to set up a simple Remote session.  Can VNC do this w/o having a domain set up.  If so, how do I configure.  If not, know of any reliable free domain name services?

Let me know...should this be in the networking forum?

---

### Post by Monicker on 2008-05-15
You can tell vnc to just use the ip address. The problem is that if server does not have a static ip address, it coudl change and the person trying to connect would not know the new ip address.

There are several free dynamic dns services which can provide a domain name to use: [www.dyndns.org](www.dyndns.org) and [www.no-ip.com](www.no-ip.com), for example.  She will need to run one of their updater clients so that domain name is stays associated to the proper ip address.  Details can be found at each site.

---

### Post by talz13 on 2008-05-15
What OS are the systems at her work and at home (or wherever she'll be accessing it from)?

I would recommend using an SSH tunnel to encrypt your VNC traffic, especially if it's business related stuff.

My setup is mainly Ubuntu server, windows viewers for VNC, so I tunnel through putty and set up the connection through my tunneled port:

Ubuntu server setup:
1. Get a dynamic dns (I prefer no-ip, but whatever)
2. Get the update client for it (noip2 in synaptic for no-ip)
3. Install ssh server on the server (ssh in synaptic)
4. Install x11vnc on the server (x11vnc)
5. Make a password for x11vnc:```
x11vnc -storepasswd
```
6. Start the vnc server:```
/usr/bin/x11vnc -bg -forever -shared -rfbauth /home/<username>/.vnc/passwd -usepw -rfbport 5900 -o /home/<username>/vnclog -noxdamage
```

Router setup (that is, the router between the server and the 'net, not on the client end):
1. Find your IP address of your Ubuntu server
2. Enter your router setup
3. Look under Port Forwarding or Games & Applications or some such heading
4. Enter 22 for the external port and the IP address of the server for the internal address
5. Save your changes!

Windows client setup:
1. Download [putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)
2. Run putty.exe
3. Enter the no-ip hostname you set up above
4. Go down to Connection\SSH\Tunnels on the left menu
5. Enter: source port: 5900, Destination: localhost:5900, Local, Auto
6. Go back to Session on the left menu
7. Give it a name in "Saved Sessions"
8. Click Save

When connecting in the future, you can double click your saved session in the session list in putty, then log in with your username and password to Ubuntu.

9. After you connected to ssh, run [VNC](http://www.realvnc.com/products/download.html) and enter localhost:5900 in the server box.

This way also lets you leave your VNC port closed on your router.





I figure, even if this isn't your exact situation, it should help me down the road in case I forget how I did this :)

---

