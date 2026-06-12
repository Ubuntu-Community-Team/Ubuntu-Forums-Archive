---
title: "Xubuntu root privileges?"
date: 2006-11-15
forum: General Help
---

### Post by voided3 on 2006-11-15
Hello. I soon am going to be installing Xubuntu on some of my older computers at home. To gain root privileges in Nautilus on Ubuntu, I always used Alt+F2 then ran "gksudo nautilus", but how would I do this (if I can) in Xubuntu? I know the Alt+F2 keyboard shortcut still works, but what should I enter to get a new window to open with root privileges? Thanks!

---

### Post by bswilson on 2006-11-15
> **voided3 said:**
> Hello. I soon am going to be installing Xubuntu on some of my older computers at home. To gain root privileges in Nautilus on Ubuntu, I always used Alt+F2 then ran "gksudo nautilus", but how would I do this (if I can) in Xubuntu? I know the Alt+F2 keyboard shortcut still works, but what should I enter to get a new window to open with root privileges? Thanks!

Try:

```
sudo nautilus &
```

---

### Post by john.nicholls on 2006-11-16
Try

 ```
gksuexec xfce4-terminal
```

John

---

### Post by kerry_s on 2006-11-16
Same thing, it's still sudo, gksudo, or gksu. I usally just use gksu for gui and sudo for command line.

Sample:

gksu thunar <- Root filemanager
gksu mousepad (path to file)  <- root file edit

On xfce4 it's easy to create several launchers on one icon, i usually make a launcher for the root-filemanager and synaptic on my home icon. You can also create right click actions like root-edit & root-open.

---

### Post by voided3 on 2006-11-16
Thanks, gksu thunar worked perfectly!

---

