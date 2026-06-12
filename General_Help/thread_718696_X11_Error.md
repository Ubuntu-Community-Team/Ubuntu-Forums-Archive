---
title: "X11 Error"
date: 2008-03-08
forum: General Help
---

### Post by ironmagma on 2008-03-08
Hi all,

I'm having trouble running X11 to be remotely accessed from Ubuntu, on a Mac.  I've tried the ssh -x option when connecting to the Ubuntu machine, but it still doesn't help.  Here's the error below; any suggestions? :-/

I get this when I try to launch an x-program like gedit:

/tmp/launch-3EtfkM/: unknown host. (nodename nor servname provided, or not known)
The application 'gedit' lost its connection to the display localhost:10.0;
most likely the X server was shut down or you killed/destroyed
the application.

---

### Post by ssj3strife on 2008-03-08
I assume you've noticed the system -> preferences -> remote desktop menu? Assuming you've set that up, you need to use vnc, not ssh, to connect. I don't know what Mac's come installed with, but try opening a terminal and running vncviewer.

Failing that, there's plenty of free vnc software available online.

---

### Post by ironmagma on 2008-03-08
Well, I know about VNC... but it's not what I need; I need to be able to tunnel (think that's the right word) X11 applications through SSH... but I'm getting an error.  Any other ideas?

---

### Post by unutbu on 2008-03-08
On the local machine (the one that actually runs gedit), type
```

xhost +remote.machine

```

where 'remote.machine' is the name or ip address of the remote machine.

If that does not work, edit /etc/hosts.all to be something like this:

ALL: remote.machine

Please note you might just need one of the fixes suggested above. I don't remember which one. A little experimentation will settle this for you.

---

### Post by ironmagma on 2008-03-08
I tried both of those and neither worked :-/

---

### Post by ironmagma on 2008-03-08
I tried both of those, but neither worked...  any other ideas, anyone? :?

---

### Post by unutbu on 2008-03-08
Sorry, I mistyped. Instead of /etc/hosts.all, you need to edit /etc/hosts.allow.
Do that on the remote machine (the one running sshd).

---

### Post by ironmagma on 2008-03-08
All right... cool, it works now.  However, now I have no clue what to do x.x

When I try to run gedit, it asks me for a display option, so I've tried pretty much everything, 0, 10, 10:0, 0:0 and each time it tells me

cannot open display: 0:0

(or something like that) for each option I try... so I guess I need to start an X session?  How would I do that?  I've tried startx, but I get the error

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.

I'm so confused... What should I do?

---

### Post by ironmagma on 2008-03-08
Bump

---

### Post by unutbu on 2008-03-08
On the machine where you want foreign X apps to be displayed, type the command
```

xhost +<name of foreign machine>

```

This tells the machine that it is alright for the named foreign machine to use its display.

If you have any more trouble, please post the command you typed and the output.
(And if it works, please post to help others who might read this thread).

---

### Post by ironmagma on 2008-03-08
Here's what I put in and got back:

user@hostname:~$ sudo xhost +remotehostname
[sudo] password for user:
xhost:  unable to open display ""

---

### Post by unutbu on 2008-03-08
I just happened to come across [http://www.tldp.org/HOWTO/XDMCP-HOWTO/ts.html](http://www.tldp.org/HOWTO/XDMCP-HOWTO/ts.html)
It may help you.

Perhaps try on the local machine (where you want the foreign X app to appear)
```

xhost +<remote host name>

```

don't use sudo.

If that doesn't work, try
```

xhost +<remote ip address>

```

If that doesn't work, ssh to the remote machine. You get a command line. Type there
```

export DISPLAY=(your local host IP):0.0

```

---

