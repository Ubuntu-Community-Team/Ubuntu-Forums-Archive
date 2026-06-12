---
title: "Terminal"
date: 2008-01-12
forum: General Help
---

### Post by rene53 on 2008-01-12
i have make an install in terminal and now i want to look the installation file ( procedure ) of that program, i shutdown the terminal before taking a kopy of that installation file.
Does the terminal makes logfiles of installed programs ?

---

### Post by erfahren on 2008-01-12
> **rene53 said:**
> i have make an install in terminal and now i want to look the installation file ( procedure ) of that program, i shutdown the terminal before taking a kopy of that installation file.
Does the terminal makes logfiles of installed programs ?
try
```

sudo cat /var/log/apt/term.log

```
note: if you want to see a list of the installed files (and where installed) of a program do this:

open up Synaptic Package Manager - go to Settings > Preferences and check "Show package properties in main window"

search Synaptic for the installed package and click on the Installed Files tab

you can also see the packages in the repoos (and their info) online at: [http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/)
you can search it with Google like:
*name-of-package* site:[http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/)

---

### Post by rene53 on 2008-01-12
i do not have a directory called apt in /var/log.

It was a third party application called gjukebox and i have made changes during the installation witch i want to see.

---

