---
title: "Run a scrip as root"
date: 2007-08-28
forum: General Help
---

### Post by hraposo on 2007-08-28
I made a script. What I want is when do double click and I say to execute in consoles, that this script run as root… what it does not happen.
What commands I must place at the beginning of script for it run as root?

---

### Post by xMemphisx on 2007-08-28
sudo or gksu would work...

---

### Post by hraposo on 2007-08-29
What I want is in the script, below:
#!/bin/sh

A line of comand that when I do double click on scrip, opens a console as root an the script runs (as root) automatically.

---

### Post by 3rdalbum on 2007-08-29
Make sure Nautilus is set to "Advanced Permissions" through gconf-editor (/apps/nautilus/preferences/show_advanced_permissions). Now open a root file browser window by running the command:

```
gksudo nautilus
```

Find the script, right-click on it, and go to the Permissions tab. Change the owner and group to "root", and make sure that Execute is turned on for the Owner, and that read and write are turned on for "Others". Click the "Set user ID" checkbox underneath to turn it on.

Now whenever you run your script in a terminal, it will automatically be running as root. Be careful.

---

### Post by jusmurph on 2007-08-29
Sweet... i need this too

---

### Post by hraposo on 2007-08-29
Hello 3rdalbum,
I do everything as you sad but the script still run as user, when I do double click on it and clhoose run in console.

---

### Post by kerry_s on 2007-08-29
just create a launcher for your script.

for gui script:
#!/bin/sh
gksu /path/to/your/script

if it needs terminal:
#!/bin/sh
gnome-terminal -e sudo /path/to/your/script

don't forget to make the script executable

---

