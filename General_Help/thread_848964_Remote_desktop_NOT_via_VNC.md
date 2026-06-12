---
title: "Remote desktop NOT via VNC?"
date: 2008-07-04
forum: General Help
---

### Post by rojmab on 2008-07-04
Is there anyway I can remotely access my Ubuntu (Gutsy) box without using VNC?
I like the Ubuntu desktop experience, but the PC I have it on is a Desktop, and is in another room. I'm still experimenting with Ubuntu and I'm not ready to install it on my laptop to replace my XP installation. I'd like to relax on the couch, watch TV, and experiment with it. 
I was able to connect using VNC viewer across my local LAN, but there are a couple drawbacks...
[LIST]
[*]VNC is horribly slow. Windows don't draw right, parts of the windows only show up if I move the mouse over a button for instance. I'm on a LAN, a matter of 6 ft of cabling and 20 ft of wireless away from the machine. I've run other bandwidth-intensive things between these computers before, and bandwidth has never been an issue. I'm using RealVNC.
[*]In order to connect VNC, I need to already be logged into the machine. This computer is only turned on when I want to use it via CLI and doesn't normally have a monitor / keyboard connected.
[/LIST]

In a past job, in order to access the HP OpenView tool, we had to open another program (Don't remember the name of it), which connected to the server (Solaris), and displaed a KDE-like desktop. Is there a similar option available that I can use to experience the Ubuntu desktop experience??

Thanks in advance for any feedback you can give me. Thanks.

---

### Post by txcrackers on 2008-07-04
To do this, you'll need an X-server running on your laptop - Cygwin is a good installation for this ([http://www.cygwin.com/](http://www.cygwin.com/)). Then you'll want to either use SSH (ssh -X for X-forwarding), or you can take the XDMCP route.

Keep in mind that X over the network is **not** that secure and is even slower than VNC can be. And you *can* set up VNC to run as a daemon so you do not have to be logged in to access your desktop system.

I'd recommend sticking with VNC, though. I don't use it directly at the moment (I do make use of KDE's built-in version), but I've done just this kind of thing in the past.

---

### Post by ryanhaigh on 2008-07-04
You could use[ xming ]("http://www.straightrunning.com/XmingNotes/") and open an XDMCP session. That would eliminate the need for logging in (although you can avoid this with VNC too). 

This page [https://help.ubuntu.com/community/HowToCygwinX](https://help.ubuntu.com/community/HowToCygwinX) has a little info on XDMCP and is likely suitable for use with xming also.

---

### Post by I Use Dial on 2008-07-04
In previous versions of Ubuntu I would run the XDMCP sessions and found it to be preferable to VNC because it consumes less resources and is way faster - I experienced no perceptable lag.

However, it only works over a wired LAN and is not very 'secure', meaning if you've got anyone or anything on your network that you're worried about, you shouldn't use it.

I didn't like Cygwin at all and found Xming did the job perfectly.  You can also start a remote session from another Ubuntu machine by going to options at the startup screen and searching for other machines on your network to log into.

---

