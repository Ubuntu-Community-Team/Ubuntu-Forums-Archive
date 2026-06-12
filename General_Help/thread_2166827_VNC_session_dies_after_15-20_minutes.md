---
title: "VNC session dies after 15-20 minutes"
date: 2013-08-11
forum: General Help
---

### Post by ahmadka on 2013-08-11
I have a VPS on which I'm running Ubuntu 13.04 64 bit currently .. I've installed tightvncserver on it, and then I access the VPS through a VNC connection ..


The problem is that when I boot the VPS, and manually activate the VNC server on the VPS (via putty), from that point, the VNC connection only works for about 15-20 minutes ... After that, VNC no longer works, and to get it to work, I have to restart the VPS and repeat .. Note that even when VNC stops responding, the VPS itself and all its applications are still running .. I know this because I use those application's web interfaces, and they all respond fine .. Putty works too .. Only VNC stops responding after a little while ..


After the said time, any existing VNC connection just stops, and if I try reconnecting VNC, it just says "Too many security failures" or "Too many authentication failures" ..


I had 11.04 64 bit installed before, and the problem was on that too ..


Anyone know what's causing this ?

---

### Post by steeldriver on 2013-08-11
Are you tunneling the VNC over SSH? if not maybe it is getting flooded by malicious connection attempts?

---

### Post by ahmadka on 2013-08-11
Nope I'm not tunneling anything, I think ... I use putty to just start the server, and then I separately start Real VNC Viewer on my PC, and use XXX.XXX.XXX.XXX:1 to start the VNC connection ..

Also, this problem started like a month ago maybe .. Before that it was fine ..

Also, sometimes when I try to connecting, Norton Internet Security 2013 gives me a message that it protected me from some hack attempt "VNC Large Error Response CVE-2001-0167"

How can I fix this ?

---

### Post by steeldriver on 2013-08-11
Tunnel

Don't expose ANY insecure ports on a public facing interface

Add the -*localhost* flag to your vncserver invocation and/or close the VNC port on the VPS with ufw or iptables (in fact, best to drop all incoming traffic by default and just open your SSH port - but remember to add and verify the 'allow SSH' rule BEFORE enabling ufw else you will lock yourself out completely)

Then set up a tunnel using PuTTY - the port-to-display naming convention for VNC is that display :n uses port (5900+n) i.e. for your display :1 you would tunnel to localhost:5901 (remember 'localhost' is actually the remote host in the context of the tunnel). The local port can be any free port but it keeps things simple if you use L5901.

Then point your VNC viewer at localhost:5901

---

### Post by ahmadka on 2013-08-11
I get the first part, about how you're saying I should limit vnc server to localhost only, but I don't get your second set of instructions for setting up the tunnel itself ... Can you elaborate on that a little more, as I've never done this before ? Should I use putty for this ? I looked at putty, but I don't see any options in it to setup a tunnel ..

---

### Post by steeldriver on 2013-08-11
1. in the PuTTY explorer pane, select 'SSH' and then 'Tunnels'

[ATTACH=CONFIG]245291[/ATTACH]

2. type in your 'Source port' and 'Destination' as follows
  
[ATTACH=CONFIG]245290[/ATTACH]

3. click the 'Add' button

[ATTACH=CONFIG]245289[/ATTACH]

Then open the connection as normal

Hope this helps

---

### Post by ahmadka on 2013-08-12
Alright, I did the above, and it opened a normal SSH window (black command prompt) .. I then started VNC server with localhost tag as follows:

vncserver -geometry 1280x960 -localhost

I then opened up Real VNC viewer and tried to connect to the following URL:

XXX.XXX.XXX.XXX:5901

but it couldn't connect ..

So how do I connect VNC Viewer through the tunnel now ?

By the way, thanks for your help ! :)

---

### Post by steeldriver on 2013-08-12
It should work if you enter **localhost**:5901 in the Real VNC viewer instead of XXX.XXX.XXX.XXX:5901

---

### Post by ahmadka on 2013-08-13
Ok that worked, thanks ! :)

---

