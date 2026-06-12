---
title: "Compiz not running on start up"
date: 2008-05-03
forum: General Help
---

### Post by talisfang on 2008-05-03
I am using ubuntu 8.04 and installed compiz like here [http://ubuntuforums.org/showthread.php?t=763829&highlight=change+desktop](http://ubuntuforums.org/showthread.php?t=763829&highlight=change+desktop)

It works but compiz doesnt start automatically on start up. I run it by starting compiz fusion icon. How can I make compiz start automatically?

---

### Post by Zorael on 2008-05-03
I'd make an entry in Sessions to launch that fusion-icon upon login. :>

KDE way would be this.
```
$ ln -s /usr/bin/fusion-icon ~/.kde/Autostart/fusion-icon
```

---

### Post by talisfang on 2008-05-03
> **Zorael said:**
> I'd make an entry in Sessions to launch that fusion-icon upon login. :>

KDE way would be this.
```
$ ln -s /usr/bin/fusion-icon ~/.kde/Autostart/fusion-icon
```

Thanks. Code didnt work beacuse I am using gnome. But I made an entry in sessions. And works great.

---

