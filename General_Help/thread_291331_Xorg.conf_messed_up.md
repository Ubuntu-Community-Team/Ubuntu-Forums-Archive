---
title: "Xorg.conf messed up"
date: 2006-11-02
forum: General Help
---

### Post by hoagie on 2006-11-02
I was messing around with my xorg.conf trying to get beryl to work, and I messed it up. When I tried to reboot, my x-server appeared to be broken and I was unable to reach the gdm-login screen. 
The only think that I have now is a terminal. I'm sure this can be fixed, because I got a backup of the correct xorg.conf, I just need to know the right command to move it from /home/username to /etc/x11. 
Any ideas would be helpful:cool:

---

### Post by PriceChild on 2006-11-02
```
sudo cp /home/username/filename /etc/X11/xorg.conf
```Will restore it for you :)

sudo gives the command root rights.

cp means copy, the next piece being the source, and then finally the destination.

use```
man cp
``` for more info

---

### Post by hoagie on 2006-11-02
I tried this, and I get a message saying that, theres no such file or directory(/etc/x11/xorg.cong, I also tried cd /etc/x11 and got the same message

---

### Post by taurus on 2006-11-02
> **hoagie said:**
> I tried this, and I get a message saying that, theres no such file or directory(/etc/x11/xorg.cong, I also tried cd /etc/x11 and got the same message
It's /etc/X11/xorg.conf as in capital **[SIZE="4"]X[/SIZE]** and number 11!!!

---

### Post by hoagie on 2006-11-02
That worked thank you very much 8)

---

