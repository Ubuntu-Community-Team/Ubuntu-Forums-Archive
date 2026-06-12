---
title: "reboot command causes server to shut down"
date: 2014-02-10
forum: General Help
---

### Post by nathan20 on 2014-02-10
I have Ubuntu Server 13.10 running kernel 3.11.0-15-generic.  When I issue any of the following commands, the server shuts down and does not come back up: `reboot` (as root), `reboot --force` (as root), `sudo reboot` (as any user), and `sudo reboot --force` (as any user).  This isn't a problem in other OS, including Windows and CentOS.  If I boot into the Ubuntu Server 13/10 install DVD, select the repair option, and go to a command line, I can successfully reboot the machine.  However, from inside the 13.10 installation, I cannot successfully reboot.  
  
I ran (as root) `apt-get update` and that didn't help.  I'm not sure where to go from here to get `reboot` to actually reboot the server, and not just shut it down.  Any help is hugely appreciated!

---

### Post by tfrue on 2014-02-10
Well, I normally use the shutdown command with the restart option, as so:
```

sudo shutdown -r now
```
That has always worked for me.

---

### Post by nathan20 on 2014-02-10
Thank you for the quick response tfrue.  When I issue the command  ```
sudo shutdown -r now
``` the system powers down and does not come back up.  This is the same behavior as when I issue a `reboot` command.

---

### Post by tfrue on 2014-02-10
You might try reseating your RAM or moving the RAM to the next dual/triple channel slots, and maybe removing or reseating any PCI cards on the motherboard. You could even get compressed air and blow out any dust or debris from your computer.

---

### Post by nathan20 on 2014-02-10
I tried re-seating the RAM and the PCI card, with no luck.  I'm not sure it has any relation, but when I execute `sudo shutdown now`, I get the following line


```
* Killing all remaining processes...   [fail]
```

---

