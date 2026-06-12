---
title: "Remote enablement of VNC/Vino/Remote-X/etc.?  Getting a little tired of blind alleys."
date: 2016-09-08
forum: General Help
---

### Post by CelticWhisper on 2016-09-08
I'm trying to connect to my Ubuntu 16.04.1 box to check on a(n unfortunately) GUI-only application and am thus far unable to enable any kind of remote graphical interface.

I am consistently able to login over SSH and have sudo permissions.  The problem seems to be in giving myself a way, *without being physically present at the system*, to access an already logged-in local session.  Simplified, this is the scenario of someone who boots their PC in the morning and logs in, goes to work or on vacation or wherever, and needs to access work they were doing with a mouse and keyboard earlier without then having access to that same mouse and keyboard later.  Assume someone is at work and won't be home until 6:00 but it has to be done by 4:30.

I've seen discussions about configuring Vino on the command line but all I get is 
```
/usr/lib/vino/vino-server
Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused
Cannot open display:
Run 'vino-server --help' to see a full list of available command line options

```

Once upon a time, there apparently was a file called %gconf.xml located in ~/.gconf/desktop/gnome/remote_access/ that could be edited to enable Vino to accept unencrypted connections or whatever had to happen, but apparently the remote_access directory no longer exists in 16.04.

tightvncserver works when run as root, but I have only a "windowmaker" styled grey background and black-X cursor and, more importantly, it does not seem to be able to connect to a current, active session.  Running it as my non-root account yields 
```
 vncserver
vncserver: Wrong type or access mode of /home/user1/.vnc.
```


More troubling still is the abject lack of a straight, direct answer that is applicable to 16.04 on how to do this at a point after initial installation.  None of the blogs I've read seem to offer anything useful.  Not to put too fine a point on it, but

THIS.
IS.
**FRUSTRATING.**

I love FOSS, Linux, Ubuntu, all that jazz, and screw everything to do with Windows (and doubly so with Windows 10), but I have to admit I don't have this kind of difficulty when I'm trying to access a current session on a Windows box.  I hope it's just a knowledge gap on my part, but either way, I'm weary of beating my head into the wall.

Is there a way to enable remote access, from a state at which it was not enabled, and without needing physical access to the host, to a current, active, locally-logged-in, alive-and-dancing-in-the-@#$%^&!-streets session from a point of only having SSH access?  If so, would the Ubuntu community please come through where blogs and other sites have failed and help me effect this?

Thank you in advance.  I don't often reach out for help but when I do it's because I'm at my wit's end, so anything you can do to help will be most appreciated.

---

### Post by TheFu on 2016-09-10
I know of no way to connect to an already running X/session. However, if you start and use a remote session with either VNC or x2go and use it locally or remotely, then you can have access to the same "session" from anywhere in the world within a limitation. Only 1 connection can be active at a time. In practice, that isn't an issue, since you can start the session at home, travel to work, reconnect to it (which will disconnect the home connection to the session), use it all day, either disconnect (or not) from work before leaving, get home, reconnect to the session and have the session desktop just like it was when you left work.

Of course these remote sessions (even when local) will have limitations that all remote graphical sessions have. Don't expect video playback to work well - it may not work at all depending on the available bandwidth.  Any programs that demand direct access to a GPU WILL NOT WORK. That is a limitation of those programs, not X/Windows.  For normal office-productivity things, these remote connections can be excellent and work well.  I use one every day, all day via x2go.  When traveling, I connect back to it from 5 miles away or 14K miles away and get acceptable performance.

Hope this makes sense. It means working in a completely different way and not really using that nice GPU in the local system, but it does work.

VNC isn't secure without a full VPN.  Plus VNC feels 2-3x slower than x2go which is based on NX. NX uses ssh for authentication, so no VPN is needed (or wanted).

The vnc issue is probably a permissions problem. Don't run GUI applications as root is the short answer.  It just causes issues for people who don't understand file and directory permissions enough and often (though not always) breaks the app for use by normal userids.

I hope there is NEVER away to connect remotely to any existing, default, X/Windows application. That would be a huge, huge, huge, huge, security problem and X/Windows already has enough security problems.

---

### Post by steeldriver on 2016-09-10
Instead of 

```

/usr/lib/vino/vino-server

```

try
```

DISPLAY=:0 dconf write /org/gnome/desktop/remote-access/enabled 'true'

```
(replace :0 with the number of your target X display, if different)

Check with
```

dconf dump /org/gnome/desktop/remote-access/

```

NOTE: if you're trying to access via a public network, I'd strongly encourage you to use SSH tunneling rather than exposing an open VNC port

---

### Post by HermanAB on 2016-09-10
...and once you are tired of faffing around with VNC, then you can just use ssh - like this:
$ ssh -C -c blowfish -X user@ipaddress "gedit filename"

It has the added advantage that it is secure too.

---

### Post by TheFu on 2016-09-10
> **HermanAB said:**
> ...and once you are tired of faffing around with VNC, then you can just use ssh - like this:
$ ssh -C -c blowfish -X user@ipaddress "gedit filename"

It has the added advantage that it is secure too.

**ssh -X user@server** is only practical on a LAN or extremely fast WAN that isn't too far away, plus it won't connect to an already running X-client application.

On a solid LAN, **ssh -X** is completely awesome.  

And with ssh, don't forget to use the ~/.ssh/config file so all those options happen automatically. The manpage is pretty good for that config file.

---

