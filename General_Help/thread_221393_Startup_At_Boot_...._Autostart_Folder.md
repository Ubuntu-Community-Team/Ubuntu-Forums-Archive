---
title: "Startup At Boot .... Autostart Folder"
date: 2006-07-23
forum: General Help
---

### Post by Nibiruet on 2006-07-23
I am using Freepops for d/l Yahoo mail into Thunderbird. Unfortunately the service does not auto start with bootup. Is there any folder I could add the program link to? I know in Kubuntu it is under .kde but not sure where it is in Ubuntu.

---

### Post by Ares Drake on 2006-07-23
You can edit the autostart settings with System->Settings->Session where you can add a program link. Have fun, Ares

---

### Post by Nibiruet on 2006-07-23
Thanks, appreciate it.
Regards

---

### Post by taner on 2006-07-27
anyway, where is the startup folder ? :oops: :oops:

---

### Post by taner on 2006-07-28
oky, i found it. Here is the autostart (startup) folder 
/home/taner/.config/autostart/

---

### Post by zek725 on 2006-10-12
> **Ares Drake said:**
> You can edit the autostart settings with System->Settings->Session where you can add a program link. Have fun, Ares

how do you do that in XUBUNTU?

---

### Post by Mithrilhall on 2006-12-16
From the command line....

```

sudo nano /etc/rc.local

```

and add this before "exit 0"

```

/etc/init.d/./freepops start

```

---

