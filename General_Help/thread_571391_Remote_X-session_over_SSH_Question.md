---
title: "Remote X-session over SSH Question"
date: 2007-10-09
forum: General Help
---

### Post by blacklobo on 2007-10-09
I am trying to establish an X-session between 2 Linux machines over an SSH session, but have it show up in a window on the local machine.

I am able to establish the X-session over SSH fine however I have not been able to figure out how to make it show up in a window on my local machine.  I have been unsuccessful in my Google searches to find this answer.

---

### Post by thirddeep on 2007-10-09
Do you mean ssh -x ?  That will allow you to execute an X application from the remote machine on your local system

Thd.

---

### Post by nikhilk on 2007-10-09
> **thirddeep said:**
> Do you mean ssh -x ?
It is -X not -x, -x disables X11 forwarding :)

---

### Post by thirddeep on 2007-10-09
<---- puts head in sand :-)

---

### Post by negated on 2007-10-09
FYI, if you encounter stability problems with "ssh -X", try "ssh -X **-Y**".

-S

---

### Post by blacklobo on 2007-10-09
I am really just looking to establish a secure (SSH) GUI session with the remote server.

The best option I had found was ssh -X (or -Y) and then running "gnome-session".  However I would like to force this connection into a Window.

---

### Post by jonnymccullagh on 2007-10-09
I am having a lot of problems with this if anyone can help??
I am able to run X programs on a Red Hat server from my Ubuntu desktop locally over our network using: 
xhost +servername
ssh -X myusername@servername
(I have also unticked the System->Administraion->Login Window->Security->Deny TCP connections to XServer and when I nmap my IP port 6000 is listening)

However, we have a lot of Solaris 8 boxes and nothing I do seems to allow me to run X programs from Solaris on Ubuntu? My colleagues use Slackware and can run the same X programs.

Has anyone got any ideas? I'd prefer to stick with Ubuntu.

---

### Post by thirddeep on 2007-10-09
To : jonnymccullagh

xhost has nothing to do with ssh -X.

Check on the Solaris servers in the sshd config file if X forwarding is allowed.

Thd.

---

### Post by jonnymccullagh on 2007-10-09
thanks thirddeep - your advice is appreciated - I had spent some time crawling the web trying to solve this.
I checked sshd_config on the Solaris server and found:
```
X11Forwarding no
X11DisplayOffset 10
X11UseLocalhost yes
```
I changed X11Forwarding to yes and restarted the shhd service.

When I next logged in using:
ssh -X username@server
I noticed this message:
/usr/openwin/bin/xauth:  creating new authority file /home/username/.Xauthority

and when I ran my x program it was delivered to Ubuntu.
Many thanks,
jonny

---

### Post by timcredible on 2007-10-09
what you probably want to do is run Xnest after establishing your ssh connection so you get a normal xdm login screen within a window - makes life much easier.  Xnest is available for solaris 9 on the companion cd, but i think i remember having to download Xnest for solaris 8 off the free solaris software site.  I also remember having problems with Xnest on solaris 8, but it's been a long time since i've used solaris 8, and i don't remember what the problem was.

---

### Post by cwaldbieser on 2007-10-10
> **blacklobo said:**
> I am really just looking to establish a secure (SSH) GUI session with the remote server.

The best option I had found was ssh -X (or -Y) and then running "gnome-session".  However I would like to force this connection into a Window.

It sounds like want a VNC or FreeNX session instead of an X-session.  VNC shows a remote desktop (to use your terminology, "in a window").

---

### Post by jonnymccullagh on 2007-10-10
Xnest does look interesting but I don't need a full-blown graphical solution. There are just 2 xwindows programs I need to run which do not have command line equivalents so for now I'll stick with X11forwarding but thanks for letting me know about Xnest - I hadn't heard about it before.
thanks,
jonny

---

