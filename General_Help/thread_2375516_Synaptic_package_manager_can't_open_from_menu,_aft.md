---
title: "Synaptic package manager can't open from menu, after upgrade"
date: 2017-10-25
forum: General Help
---

### Post by cyril-auburtin on 2017-10-25
Lubuntu 17.10

It doesn't do anything when clicking it from the desktop menu (System tools > Synaptic Package manager)

When running synaptic-pkexec (which is the command of the menu item) in the terminal, I get:

```

caub@acer:~$ synaptic-pkexec 
==== AUTHENTICATING FOR com.ubuntu.pkexec.synaptic ===
Authentication is required to run the Synaptic Package Manager
Authenticating as: caub,,, (caub)
Password: 
polkit-agent-helper-1: error response to PolicyKit daemon: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: No session for cookie
==== AUTHENTICATION FAILED ===
Error executing command as another user: Not authorized


This incident has been reported.

```

running it with sudo first works fine though
```

sudo synaptic-pkexec

```
```

sudo synaptic

```

---

### Post by ajgreeny on 2017-10-25
There is a currently known problem with synaptic running in a wayland instead of xorg environment, and whilst it is annoying, it can easily be overcome with a simple command ```
xhost +si:localuser:root
``` at the start of the wayland session, or by creating a script and running it at wayland session start.
```
#!/bin/bash
sleep 10;
xhost +si:localuser:root
```
by adding it to the startup applications list.

There is a long standing bug about it which gives the answer, (temporary I hope, before this bug is properly squashed), at [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1712089](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1712089) and many forum posts that will all give the same answer.

---

### Post by cyril-auburtin on 2017-10-26
thanks, ok

---

