---
title: "Ubuntu Cleaner not opening after install"
date: 2016-12-17
forum: General Help
---

### Post by geovino on 2016-12-17
I installed the Ubuntu Cleaner   [http://www.omgubuntu.co.uk/2016/12/free-space-ubuntu-cleaner-janitor-app](http://www.omgubuntu.co.uk/2016/12/free-space-ubuntu-cleaner-janitor-app)
But after install its icon shows up for a brief moment and then disappears. 

How do you get it to work?

---

### Post by howefield on 2016-12-17
Try running it through a terminal, you might get a clue as to what the issue is, I don't know the application but I guess that using ubuntu-cleaner in the terminal should launch it (or give you the errors)

```
ubuntu-cleaner
```

---

### Post by geovino on 2016-12-17
I get this

davek@dell:~$ ubuntu-cleaner
Traceback (most recent call last):
  File "/usr/bin/ubuntu-cleaner", line 7, in <module>
    import dbus
ImportError: No module named dbus
davek@dell:~$ 

maybe those instructions were wrong? I'll uninstall it for now.

---

### Post by howefield on 2016-12-17
> **geovino said:**
> File "/usr/bin/ubuntu-cleaner", line 7, in <module>

What I'd do now is search for the most likely looking part of the error, ie, the above.

Google gives a couple of links (which may need translating for you) with a fix of installing python-dbus.

---

### Post by geovino on 2016-12-17
Thanks! installing python-dbus and reinstalling ubuntu cleaner... now works. :)

---

### Post by howefield on 2016-12-17
Cool, glad you got it working.

Have to say also that there is nothing that a cleaning application will do that you couldn't do manually, just saying that for newer users, you have been around long enough to know what's best for your machines :) 

Thanks for marking as solved.

---

### Post by geovino on 2016-12-17
yes, youre right. after running ubuntu cleaner its all things that I do anyway except clearing out older kernels. which maybe isn't a big deal anyway.

---

### Post by howefield on 2016-12-17
> **geovino said:**
> .......except clearing out older kernels. which maybe isn't a big deal anyway.

Not a big deal until you're /boot fills up with old unused kernels and ends up borking your package management system.

You can periodically run autoremove to keep them down.

```
sudo apt autoremove
```

Or get unattended-upgrades to do it for you automatically by editing the /etc/apt/apt.conf.d/50unattended-upgrades (not sure which Ubuntu version this option became default).

```
sudo nano /etc/apt/apt.conf.d/50unattended-upgrades
```

changing "*//Unattended-Upgrade::Remove-Unused-Dependencies "false";*" to "*//Unattended-Upgrade::Remove-Unused-Dependencies "true";*"

---

### Post by geovino on 2016-12-17
Thanks for the info.

---

