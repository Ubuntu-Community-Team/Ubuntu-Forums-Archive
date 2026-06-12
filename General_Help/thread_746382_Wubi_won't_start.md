---
title: "Wubi won't start"
date: 2008-04-05
forum: General Help
---

### Post by ekmon1582 on 2008-04-05
All of the sudden I get this error message on a black screen, before Ubuntu starts up.

BusyBox V1.1.3 (Debian 1:1.1.3-5 ubuntu12) Built-in Shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)_   


the '_' is a blinking cursor





Anyone know why I'm all of the sudden getting it, what it means, and what I should do?

---

### Post by ekmon1582 on 2008-04-05
Never mind, it all the sudden went.

---

### Post by Jonga on 2008-04-13
I get that same deal whenever I try to run hardy from live cd, the only other reference I could find was here.

[http://www.ubuntuclub.com/node/615](http://www.ubuntuclub.com/node/615)

but I don't know that language

---

### Post by vettypayal223 on 2008-07-10
I figured that it occurs when you abruptly restart your PC. Windows marks NTFS partions as being in use when it's running and marks as not in use when you shutdown or restart your PC properly. Wubi checks for this marks and when it's marked as In use, wubi won't load. so when it happens next time, just startup in windows, restart the system using Windows and then again start in ubuntu. Hope this helps. btw, i'm no subject expert, i just observed a bit.

---

