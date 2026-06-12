---
title: "Failed to start X server..."
date: 2006-11-17
forum: General Help
---

### Post by umanzor on 2006-11-17
First, I installed the nvidia drivers with Automatix, then I wanted to try the beta ones, and uninstalled the nvidia drivers, again from Automatix. Restarted my computer and now I get this error:

> Failed to start the X server (your graphical interface). It is likely that it is not set up correctly...

What can I do?

There is also a problem when I try to shut down or reboot my computer. Nothing happens after the Ubuntu screen. It just stays frozen with the progress bar empty.

---

### Post by adwait on 2006-11-17
Try using
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by umanzor on 2006-11-17
> **adwait said:**
> Try using
```
sudo dpkg-reconfigure xserver-xorg
```

Already tried, changed settings a bit, still doesn't work.

Maybe if I can get a default xorg.conf file and replace it?

---

### Post by umanzor on 2006-11-17
Guess I can try replacing the file with the backup, easiest solution... but, how do I that from the command line?

great place btw.... :-?

---

### Post by adwait on 2006-11-18
Well, you could use
```
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

This will replace your current xorg file with the backup file.

---

