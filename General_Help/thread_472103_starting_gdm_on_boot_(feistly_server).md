---
title: "starting gdm on boot (feistly server)"
date: 2007-06-12
forum: General Help
---

### Post by SDE on 2007-06-12
i installed feisty server and i can start the graphical environment with: startx

i want the system to boot up in this mode like it does with the desktop install.  how can i do this?

---

### Post by zvacet on 2007-06-12
```
sudo /etc/init.d/gdm start
```

---

### Post by meatpan on 2007-06-12
Try this out:
```

sudo update-rc.d gdm defaults

```

update-rc.d manages the unix system-V style startup programs.  The command specifies that gdm (the gnome-display-manager) shoult be run at boot according to the default gdm paramaters.

There's likely a better way to do this, but this technique has always worked for me.

---

### Post by RedSquirrel on 2007-06-12
> **SDE said:**
> i installed feisty server and i can start the graphical environment with: startx

i want the system to boot up in this mode like it does with the desktop install.  how can i do this?

When I install gdm from the Ubuntu repositories it is configured to start automatically.

```
sudo apt-get install xterm gdm
```

---

