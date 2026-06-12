---
title: "Installing printer problems"
date: 2008-04-02
forum: General Help
---

### Post by markdjones82 on 2008-04-02
All,  when I go to the system->administration->printers gui, it has add printer greyed out and I cannot add one.  I try to connect to server localhost and it will not do this either. 

Am I doing something wrong?  Does cups need to be running or something?

---

### Post by stchman on 2008-04-02
> **markdjones82 said:**
> All,  when I go to the system->administration->printers gui, it has add printer greyed out and I cannot add one.  I try to connect to server localhost and it will not do this either. 

Am I doing something wrong?  Does cups need to be running or something?

One of the menus in the print manager has an option to become administrator.  Choose it.

If that does not work try this:

Gutsy
```
sudo system-config-printer
```

Feisty or earlier
```
sudo gnome-cups-manager
```

---

### Post by metalf8801 on 2008-04-02
Is your printer on [http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)

---

### Post by markdjones82 on 2008-04-03
Yes, the printer is in the list, but I don't see any sort of choose admin option.  Everything just appears greyed out even with using sudo to open the gui.

I am running Gutsy.


Edit: Cupsys had to be started.  How do I add it to the startup scripts anyway?

---

