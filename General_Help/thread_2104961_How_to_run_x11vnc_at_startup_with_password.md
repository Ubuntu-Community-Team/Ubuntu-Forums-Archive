---
title: "How to run x11vnc at startup with password?"
date: 2013-01-14
forum: General Help
---

### Post by blnl on 2013-01-14
I'm trying to run x11vnc at startup using built-in Startup Applications utility.

When using following options x11vnc server start at startup and I can normally connect from a remote client:
```
x11vnc -forever -rfbport 5900
```

The problem is when I include password file as follows:
```
x11vnc -forever -rfbport 5900 -rfbauth $HOME/.vnc/x11vnc.pass
```

The remote client connects, but after I enter the password the response is:
> password check failed!

I do not understand why this is happening, because when I start the x11vnc server from the command line, using exactly same options, password is accepted and I can normally connect from a remote client.

Can anyone help please?

---

### Post by blnl on 2013-01-16
Still no response from anyone.

In the meantime I have found a rather satisfactory workaround:
```
x11vnc -forever -rfbport 5900 -timeout 300 -accept popup -passwd <password>
```

The example above does work with Startup Applications, but is less secure. The password is written in the command line (hence human readable).
In order to make it less dangerous, I have enabled two additional options.
[LIST]
[*]-timeout 300 ; it is possible to connect only within 5 minutes window after vnc server is started.
[/LIST]
[LIST]
[*]-accept popup ; a user confirmation from the server side is needed in order to connect.
[/LIST]

By the way, if anyone knows how to enable "-rfbauth" option**, I would still like to know.**

---

