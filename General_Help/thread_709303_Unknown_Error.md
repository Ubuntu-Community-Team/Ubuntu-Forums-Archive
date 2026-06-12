---
title: "Unknown Error"
date: 2008-02-27
forum: General Help
---

### Post by mrhammad on 2008-02-27
When I open the PC today it gives me the following error :

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.


The things I can see is that my other partitions are not mounted. 

Another thing I found out is that instead of running screen saver it the monitor off.

---

### Post by Yellow Pasque on 2008-02-27
According to this bug report, it is a problem with dbus since they split the package into dbus and dbus-x11
[https://bugs.edge.launchpad.net/ubuntu/+source/gconf2/+bug/139368](https://bugs.edge.launchpad.net/ubuntu/+source/gconf2/+bug/139368)

Try installing dbus-x11 and see if that fixes the issue:
```
sudo apt-get install dbus-x11
```

---

### Post by KC9EVP on 2008-02-27
I would get the following error. I applied the fix suggested. I will let you know the results.

---

