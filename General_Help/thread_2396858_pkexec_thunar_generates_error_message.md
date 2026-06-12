---
title: "pkexec thunar generates error message"
date: 2018-07-21
forum: General Help
---

### Post by Seadevil on 2018-07-21
i keep getting this message when i try to run pkexec thunar in the terminal: 

[HTML]Gtk-Message: 15:10:41.128: Failed to load module "canberra-gtk-module"
[/HTML]



i copied the code from a post on here & changed the name from nautilus to thunar in  com.ubuntu.thunar.policy.

how to i fix/install/correct this module?

---

### Post by #&amp;thj^% on 2018-07-21
Can you show us the link you followed? (We don't know what code you copied)
Also show us the output of this :
```
echo $DESKTOP_SESSION

```

---

### Post by Seadevil on 2018-07-21
ok, here's the link:      [https://ubuntuforums.org/showthread.php?t=2225832](https://ubuntuforums.org/showthread.php?t=2225832)

---

### Post by Seadevil on 2018-07-21
the echo command you gave me just comes back with    :         ubuntu

nothing else.....

---

### Post by Yellow Pasque on 2018-07-21
Is the error message causing an issue?

EDIT: Do you have libcanberra-gkt0 package installed? Thunar is still using GTK2 so just having the default libcanberra-gtk3-0 package installed won't solve the message.

---

