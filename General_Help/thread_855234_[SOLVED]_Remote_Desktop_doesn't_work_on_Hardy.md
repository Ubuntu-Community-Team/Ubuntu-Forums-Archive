---
title: "[SOLVED] Remote Desktop doesn't work on Hardy"
date: 2008-07-10
forum: General Help
---

### Post by foxmajik on 2008-07-10
Hello,

I've been having some difficulty with getting Remote Desktop feature working.

* I have used the remote desktop preferences applet to enable remote connections, (configured as such: do not prompt me when someone connects and use a password).

* I have configured the service to use port 3389 which I verified is mapped to my PC on the home gateway.

* I have verified that no other service is using that port.

* I have verified that I can connect to the machine on other services (ssh works fine).

However, I cannot connect to the machine remotely.  I am getting Connection Refused.  It seems that the vnc server is not starting when I tell the preferences applet that I would like to enable the remote desktop.

While I could just yank this component out and install a "real" vnc server, I'd like to use the fuzzy happy and supported components already there.

Is there some kind of magic I have to perform to get the system to actually *turn on* the remote desktop?

---

### Post by foxmajik on 2008-07-10
Vino is essentially garbage and doesn't have any usable documentation, so I ripped it out and replaced it with x11vnc which does the same thing (exports an existing X session).

Remove vino server and purge the configuration files:

```
$ sudo aptitude purge vino
```

Update the apt cache:

```
$ sudo apt-get update
```

Install x11vnc:

```
$ sudo apt-get install x11vnc
```

Set a password for vnc:

```
$ $x11vnc -storepasswd
```

Start a VNC server that will request a password using the location specified earlier on connect and then display the desktop running on x11 screen (default for Ubuntu) 0:

```
$ x11vnc -rfbauth ~/.vnc/passwd -display :0
```

x11vnc has many other useful features and its author has written a very user friendly tutorial that is available [here]("http://www.karlrunge.com/x11vnc/").

Assuming you've setup a port forward on your router to forward port 5900 to your computer, you can now connect to your external IP address to get your x11 session that's already running.

**NOTE:** If your computer is at the login screen but no one is logged in you need to do more steps.  See the docs for x11vnc.

**NOTE:** If port 5900 is already in use, x11vnc will increment the port until it finds one that is not in use.

**NOTE:** When x11vnc starts up it will spit out a lot of useful data to the terminal that can tell you not only what might have went wrong if it fails to start, but also suggestions on other useful features you might want to try next time you start it.

Read the author's tutorial if you have any trouble.

---

### Post by xp_newbie on 2010-11-11
@foxmajik I agree that vino is useless if one can't assume that the user is already logged into his Gnome desktop. This is indeed my case and after making vino work, I am going to disable it and setup a real vnc server. ;)

Now I have to choose between [vnc4server]("http://ubuntuforums.org/showthread.php?t=795036"), with which I am well familiar, and [x11vnc]("http://www.karlrunge.com/x11vnc/").

Which one is better (and why)?
Will x11vnc work with [RealVNC 4.1]("http://www.realvnc.com/products/free/4.1/download.html")?

Thanks. :popcorn:

---

### Post by krunge on 2010-11-11
> **xp_newbie said:**
> 
Now I have to choose between [vnc4server]("http://ubuntuforums.org/showthread.php?t=795036"), with which I am well familiar, and [x11vnc]("http://www.karlrunge.com/x11vnc/").

Which one is better (and why)?

In their primary usage modes they address different scenarios.  vnc4server creates Virtual (RAM-only) X sessions that can be attached to via VNC (and VNC is the only way to view these sessions.)

x11vnc's primary use is to poll and export via VNC X sessions that are attached to a physical graphics display (i.e. on a real video card) and monitor.

However, x11vnc's options "-create" or "-svc" can emulate vnc4server's RAM-only X sessions as long as you add the 'xvfb' package (x11vnc will start Xvfb for its virtual X server.) The response of x11vnc's emulation mode will not be as fast as vnc4server, but one may want to do this to take advantage of some x11vnc feature (e.g. SSL encryption, server side scaling, unix logins, filetransfer, etc.)   
> Will x11vnc work with RealVNC 4.1?

Yes, that VNC viewer will work with x11vnc.

---

