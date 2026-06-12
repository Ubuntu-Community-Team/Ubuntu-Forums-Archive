---
title: "how to switch from 12.10 to 13.04"
date: 2013-04-25
forum: General Help
---

### Post by Isaacmarritt on 2013-04-25
i have ubuntu 12.10 and i would like to upgrade to the new 13.04 i heard you do it through software sources but software sources does not work on my computer is there a way for me to get software sources working or to upgrade a different way like though the terminal . also i would like to keep all my aplications ducuments and settings

---

### Post by kc1di on 2013-04-25
Hello Isaacmarritt,
[Here's ]("http://www.techdrivein.com/2013/03/how-to-upgrade-to-ubuntu-1304-raring-from-ubuntu1210.html")and easy way to do it. That being said upgrades do not always go as planned so make sure you ***BACK UP*** any important data.

---

### Post by Isaacmarritt on 2013-04-25
cant my software up update program no longer works i do everything through the terminal

---

### Post by kc1di on 2013-04-25
did you try running the command in the terminal and if so what error messages did you get?

---

### Post by Isaacmarritt on 2013-04-25
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 115, in <module>
    app.start_update()
  File "/usr/lib/python3/dist-packages/UpdateManager/UpdateManager.py", line 164, in start_update
    self._start_pane(UpdateProgress(self))
  File "/usr/lib/python3/dist-packages/UpdateManager/UpdateProgress.py", line 56, in __init__
    self.install_backend = get_backend(self.datadir, self.window_main)
  File "/usr/lib/python3/dist-packages/UpdateManager/backend/__init__.py", line 51, in get_backend
    from .InstallBackendAptdaemon import InstallBackendAptdaemon
  File "/usr/lib/python3/dist-packages/UpdateManager/backend/InstallBackendAptdaemon.py", line 11, in <module>
    from aptdaemon import client, errors
EOFError: EOF read where not expected

---

### Post by kc1di on 2013-04-25
you can try what [this page]("http://www.ossdoc.com/2013/04/simple-way-to-upgrade-to-ubuntu-1304.html") suggests also.

---

### Post by Isaacmarritt on 2013-04-25
im just gonna start fresh and install it new and just transfer my important files thanks for the help

---

### Post by kc1di on 2013-04-25
that's almost always best IMHO. Good Luck

---

