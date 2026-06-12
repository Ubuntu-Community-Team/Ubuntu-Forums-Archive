---
title: "Automatix failed to install"
date: 2007-03-27
forum: General Help
---

### Post by gmcm1979 on 2007-03-27
i have just upgraded to edgy and was trying to install the new version of automatix, unfortunately it didnt completely install. i got an error message to type into terminal sudo apt-get install -f to complete the installation, unfortunately whatever automatix was doing has now messed up my applications menu and i cant get many apps to launch, can anyone help install automatix and fix my problems with the menu

---

### Post by taurus on 2007-03-27
Can you post your /etc/apt/sources.list?  Maybe you have a wrong version of automatix (repo) in there.

```
cat /etc/apt/sources.list
```

---

### Post by gmcm1979 on 2007-03-27
cant get terminal to launch from the menus where can i find it?

---

### Post by taurus on 2007-03-27
<Alt>F2 -> gnome-terminal

---

### Post by gmcm1979 on 2007-03-27
error message

Could not open location 'file:///gnome-terminal'

---

### Post by taurus on 2007-03-27
How did you upgrade from Dapper to Edgy?  Maybe you need to get to a console and have a look at your /etc/apt/sources.list.

<Ctrl><Alt>F2

---

### Post by gmcm1979 on 2007-03-28
i have rebooted and there is now nothing on my desktop, so i am now using the live cd. when i press ctrl alt f2 and run cat /etc/apt/sources.list, how do i get that to print to screen.

---

