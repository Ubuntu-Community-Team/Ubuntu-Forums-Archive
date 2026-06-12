---
title: "Pantheon Desktop Environment from remote with SSH and X11 Server"
date: 2020-03-08
forum: General Help
---

### Post by gabriele97 on 2020-03-08
Hi,
I installed through ssh on my ubuntu remote machine elementary-desktop and I am trying to startup pantheon and connect it to my X11 server on my local machine.

I am using this command:

```
export DISPLAY=127.0.0.1:0.0; gala --x11& plank& wingpanel& 
```

but only wingpane and plank starts actually. If i start to run only gala i get these errors:

(gala:6071): libupower-glib-WARNING **: 12:08:10.907: Couldn't connect to proxy: Could not connect: No such file or directory


(gala:6071): libupower-glib-WARNING **: 12:08:10.911: Couldn't connect to proxy: Could not connect: No such file or directory


(gala:6071): GLib-GObject-WARNING **: 12:08:10.913: invalid (NULL) pointer instance


(gala:6071): GLib-GObject-CRITICAL **: 12:08:10.914: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

What's happening exactly? Thank you

EDIT: my terminals shows these messages when try to start everything: [https://pastebin.com/artwbhPv](https://pastebin.com/artwbhPv)

---

### Post by TheFu on 2020-03-08
Did you do an xhost + on the local machine to allow remote X/clients to connect to the local X/server?
The xhost + command format changed since the last time I used it, so you'll want to look up the specific command needed.

BTW, using only X client/server isn't secure.  Best to use either an ssh tunner (ssh -X) or a full VPN.  The ssh-tunnel don't run most DEs, just the individual X/client programs.

Or

if you want a full desktop, perhaps something like x2go would fit better?  I've used x2go from 5 continents and from the same room.  It is how I access my primary desktop even when in the same room.

BTW, why bother exporting a localhost IP?  That doesn't make any sense.
[https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) tries to explain running remote apps, remote desktops, etc.

---

