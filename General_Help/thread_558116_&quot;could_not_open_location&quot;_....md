---
title: "&quot;could not open location&quot; ..."
date: 2007-09-23
forum: General Help
---

### Post by bigeyedphish4134 on 2007-09-23
It seems as though I cannot access any storage areas on my hard drive - I even downloaded a file to the desktop, and it doesn't show up.  When I click on Places > Desktop, for instance, i get an error message that says.  "Could not open location 'file:///home/greg/Desktop' There is no default action associated with this location.

This happens when trying to access anything (including the CD drive), not just the desktop.

Any ideas of what I can do to fix this?  It was working just fine before.

Thanks!

---

### Post by jrib on 2007-09-23
in a terminal you can get to locations like ~/Desktop and 'ls' though?

Try 
```

sudo update-desktop-database
sudo update-mime-database /usr/share/mime
sudo killall nautilus

```

for kicks

---

### Post by enpakkam on 2008-07-14
i have also faced the same problem, and also executed those three commands but not solved yet.

_**cause of the problem**_
to speed-up my ubuntu i have removed lot of packages from synaptic package manager and i have restarted. system booted fine but there is no icons on the desktop and i cant open the file browser and when i right click my mouse on desktop => no response

but i could do all things by using terminal.

**how to fix this bug?**

---

