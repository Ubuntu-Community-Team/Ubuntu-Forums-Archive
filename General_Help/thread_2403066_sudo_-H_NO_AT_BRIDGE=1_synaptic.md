---
title: "sudo -H NO_AT_BRIDGE=1 synaptic"
date: 2018-10-07
forum: General Help
---

### Post by 3togo on 2018-10-07
wherever I call synaptic, 18.04 bionic will complain. My question is what is the proper way to invoke synaptic?

Case 1:
sudo synaptic

```
(synaptic:18839): dbind-WARNING **: 18:07:38.835: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-1tSsZ5FuWo: Connection refused

(synaptic:18839): IBUS-WARNING **: 18:07:39.152: The owner of /home/jc/.config/ibus/bus is not root!

```

Case 2:
sudo -H synaptic

```
(synaptic:18895): dbind-WARNING **: 18:09:11.058: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-1tSsZ5FuWo: Connection refused
```

Case 3:
sudo -H NO_AT_BRIDGE=1 synaptic

NO COMPLAIN

Case 4:
 ! grep -Fq "NO_AT_BRIDGE" /etc/environment && echo "export NO_AT_BRIDGE=1"|sudo tee -a /etc/environment
sudo -H synaptic

NO COMPLAIN

---

### Post by ajgreeny on 2018-10-07
Which version of Ubuntu is this?

Whichever it might be, try ```
synaptic-pkexec
``` which is how the synaptic.desktop launcher file calls it in the most recent supported versions.

---

### Post by tea for one on 2018-10-07
Are you experiencing this problem with "Ubuntu on Wayland" session or "Ubuntu" session?

If you log out and and log in again, click on the gear wheel near the **Sign In** box and you can identify your session.

I just logged in to a "Ubuntu on Wayland" session and tried to open Synaptic via the terminal. I also received a **Connection refused** error.

Synaptic on an old school Ubuntu session is as good as ever.

---

### Post by ajgreeny on 2018-10-07
Wayland is not the default in 18.04 so if using it instead of X11 you must have chosen it at login.

I'm not even sure if it's installed by default, but nevertheless, **tea for one** has asked a good question which, if you login to a Xsession, may be the complete solution.

---

