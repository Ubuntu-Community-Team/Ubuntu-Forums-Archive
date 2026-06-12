---
title: "Enable network in recovery mode doesn't work."
date: 2014-11-22
forum: General Help
---

### Post by CantankRus on 2014-11-22
How do you enable networking in recovery mode?
This is supposed to mount the file system in read/write mode with internet access.

I can drop to a root shell and remount / as read and write using a command but I want internet access as well.
The enable network recovery option asks if you want to mount in read/write mode.
I select yes, but then the terminal won't accept input.
You are supposed to be returned to the menu as in this guide.... [http://askubuntu.com/questions/92556/how-do-i-boot-into-a-root-shell](http://askubuntu.com/questions/92556/how-do-i-boot-into-a-root-shell)

Is there a command I can use to enable my network on eth0 once I am in read/write mode.

---

### Post by CantankRus on 2014-11-23
Well couldn't get the networking option in recovery to work but 
using the "drop to root shell " option I can:

mount / in read write mode
```
mount -o rw,remount /
```

and then enable networking with...
```
dhclient [COLOR="#FF0000"]eth0[/COLOR]
```
[COLOR="#FF0000"]Your network interface[/COLOR].

---

