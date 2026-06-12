---
title: "VNC Server Web access"
date: 2007-03-02
forum: General Help
---

### Post by Demodog on 2007-03-02
Hi!

Anyone know howto change the port for vncserver webaccess from 5801 to something like 8080 so that I can connect from my work, they have a firewall blocking the port.

---

### Post by LotsOfPhil on 2007-03-02
For me, it is in /etc/xinetd.d/Xvnc

---

### Post by Demodog on 2007-03-03
Okay will check it now and see if I can find it. Would be neat to change it to 8080 or something. 

Btw.. When Im logging into ubuntu then Vino starts and that get dekstop :0. So this means that I have to start vncserver to do a new desktop and that gets :1 ?
Can I connect to vncserver and get the gnome login interface and then login as normal?

---

### Post by Demodog on 2007-03-03
Okay in /etc/xinetd.d/Xvnc I have a line "port = 5901" but how do I set the http port?

I get the feeling that the webaccess in vncserver is not activated because If I check which ports are open and listening shouldnt it be 5800 and 5801 since 5900 and 5901 are open and listening?

---

### Post by Mr. C. on 2007-03-03
Setup an SSH connection instead to your remote system.  Tunnel your VNC ports through the SSH tunnel. This is more secure, and you can use whatever ports you decide to tunnel.

MrC

---

### Post by Demodog on 2007-03-03
Yes I have an SSH remote connection from my work using Putty.
You mean I can run vncserver through SSH?
That would be great, how do I go about doing it? Is it hard?

---

### Post by Mr. C. on 2007-03-03
Absolutely, and its the only way your should be doing it remotely!

First, let me suggest changing from Putty, to Tunnelier, a far easier to configure SSH client.  Either way, its pretty trivial and there are HowTos on various VNC sites (RealVNC for example).

The basic concept is this. 

Your SSH server is configured to :
  - allow you to connect from work
  - allow port forwarding (man sshd_config)
 
The only port you need open on your firewall is 22 (SSH).

Your home system is running a VNC server (I prefer UltraVNC for several reasons).  The VNC server is configured to allow localhost users to connect.

Now you configure your SSH client to forward port 5900 locally to remote port 5900.

Then, you use your VNC client to connect to localhost:5900.

Your SSH client has setup the tunnel, and when you connect to localhost:5900, SSH forwards port 5900 traffic to your SSH server, which then forwards to the correct port on your server.

There are all sorts of configurations you can do, even reverse tunnels.

MrC

---

### Post by KrIaXPaTaLa on 2007-03-14
But lets assume you REALLY want a http connection to your vnc server, on port 80. Is it possible?

Regards,

KrIaX. Portugal

---

### Post by Mr. C. on 2007-03-14
To answer your question in a nut shell, no not really.  Having said that, just about anything is possible with networking, but it can take some work.

By default, HTTP is stateless (connections come and go very quickly).  VNC is stateful, and requires the connection to be open for the life of the session. 

If you already have a web server listening on port 80, you'd need to support a new protocol, and wrap the VNC connection through it, and then it would have to create a new instance of itself to create and retain a connection to the client.  

If you don't have a web server listening on 80, you can certainly put your VNC connection there, but it will get a lot of traffic not intended for VNC.  Also, ports below 1024 are typically considered secure ports, only for privileged processes.

VNC does have the ability to be run as a java applet via web browser, but again, thats on a different port than the standard VNC connection, and it certainly isn't port 80.


MrC

---

### Post by KrIaXPaTaLa on 2007-03-15
Thanks, I see. Seems a little bit too mutch for me, but I'll take a look more closely over the weekend.

Regards,

KrIaX, Portugal

---

### Post by Mr. C. on 2007-03-15
Sure, no prolem.  I'm curious, what is it you are trying to accomplish ?

MrC

---

### Post by KrIaXPaTaLa on 2007-03-15
Access to my home computador from work. My connection at work is a "direct" line to Germany, and my access to the internet is provided trough a proxy server (seems only port 80 and 443 are allowed, for web browsing - haven't checked ssh 22 yet, but I doubt it works). I have no power over the connection or the proxy, so the only idea I came up with was to configure my home vnc server to send data trough port 443. I got tightvnc java applet and configured a web browser (apache) with ssl to connect to the vnc server on port 5902 trough that applet, works great, but not in the way I was expecting.

Basically, I allows a connection to the applet, trough port 443, but after the load and authentication to the vnc server, it connects on port 5902. From work, the proxy blocks this, so all I get is the applet with the vnc authentication form, and an ugly network error after that. 

NOTE: I'm using gnomes simple remote desktop feature, basically.

But, for example, I know that ultravnc server for windows has a configuration for web access. What I dont know is,  if it actually works on port 80 alone (I assumed yes, but now I'm not so sure), or if it also sends the client browser to the vnc "normal" port (5900 or so), making this configuration only usefull to allow access without a specific client (instead, any browser will work) and not to channel traffic over port 80 (as I hoped for).

Regards,

KrIaX, Portugal

---

### Post by Mr. C. on 2007-03-15
I see.

If you have no web server running at home, you can have your SSH server listen on port 80.  Connect via port 80, and tunnel all that you need.

Obviously you can't have a web server running on 80, but you can put the web server on another port and tell you friends to use the re-mapped port.

I am not advising you try to circumvent your work's policies, and in fact personally would not.  What you do is up to you and your values.

MrC

---

### Post by KrIaXPaTaLa on 2007-03-15
That is a very good advice. The thing is, I'm not a user, I'm a systems admin, and my works gets really limited by the proxy policies. Soon I hope to get my own private internet connection, with no restrictions, but for now I'm trying to manage as well as I can (the company just got bought by the germans, things are still... unbelivably messed up).

Regards and thanks for all the help.

KrIaX, Portugal

---

