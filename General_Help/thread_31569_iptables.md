---
title: "iptables"
date: 2005-05-03
forum: General Help
---

### Post by flightcrank on 2005-05-03
i use my linux (ubuntu) box to share my net connection. i do this by typing

```
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQERADE
```

and it works !, how ever it does not save and it lost after i reboot !. under mandrake all i do is "service iptables save" how do i do this under ubuntu, theres is no iptalbes entry under /etc/init.d for iptables ?

any help, thanks

---

### Post by flightcrank on 2005-05-05
bump

---

### Post by nemesa on 2005-05-05
Hi!

I use this script:

[http://www.ubuntuforums.org/showthread.php?t=19106&highlight=iptables+script](http://www.ubuntuforums.org/showthread.php?t=19106&highlight=iptables+script)

It's easy to install and it works perfectly for me.

---

### Post by flightcrank on 2005-05-05
i dont have a "/etc/init.d/iptables" entry at all ? i jus want to ad the line ...

sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQERADE

without having to type it in every time i reboot.

---

### Post by nemesa on 2005-05-07
????

After you installed that script, you don't have to type it again and again. Install it, type that command and reboot....and reboot....and reboot....  :smile:

---

