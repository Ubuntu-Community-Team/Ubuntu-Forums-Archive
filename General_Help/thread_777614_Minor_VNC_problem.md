---
title: "Minor VNC problem"
date: 2008-05-01
forum: General Help
---

### Post by Jaiinus on 2008-05-01
Hey there folks, I'm running HH 8.04 and I got seriously frustrated at Vino. For some reason selecting "only accept local connections" actually means "Deny all connections, muahahaha". So I installed tightvncserver and wasted half an hour researching how to get it to pass on the -localhost option so that it would only accept localhost connections. Turns out that if you just tell it to do it (tightvncserver -localhost) it will pass it on. I want to know if there is a good way to idiot proof this so that when new users come on board they don't open themselves up to a major hurting. I tried trudging through the wrapper script (/usr/bin/tightvncserver) and I came up empty.

Also, if there is some way to not have to put in a separate VNC password or synchronize it to the users password and have a SSO type environment, that would be awesome.

---

### Post by Jaiinus on 2008-05-05
I'd really appreciate any help here, someone must know how to do this. Basically, I want some way to hard code the -localhost flag into the wrapper script or somewhere so that when new users are added, their terminals aren't just open to the world.

---

### Post by Ruzihm on 2008-05-14
I'm having the same problem, running HH 8.04 64 bit and Vino will not accept any connections when "Only allow local connections".  In fact, I try to connect to the computer's own VNC server (connection to 127.0.0.1 -should- be local, right?) and it still does not work, and needless to say, it doesn't work on a computer on the same network (connecting internally at 192.168.x.x, is remote, right?).  If someone could post an answer or direct me to a post that addresses this, that would be great.

In any case, I'm trying to tunnel a TightVNC VNC viewer running on windows through an encrypted putty connection.  The ssh connection works fine, and VNC works when tunneled, but I would still like to prevent VNC connections that are not being tunneled, or just remote connections, in general.  Is there another way of doing that, perhaps?  I'm already so close--all I need is for VNC to deny remote connections--but if it needs to be done another way, any kind of guidance in that direction would be fine as well.

Thanks

---

