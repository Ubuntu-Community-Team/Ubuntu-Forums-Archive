---
title: "Boot hangs at eth0: link is not ready"
date: 2007-05-20
forum: General Help
---

### Post by weatherman1293 on 2007-05-20
After getting my belkin wireless card to actually work, I went to reboot. Seeming I cannot see the splash screen or anything on a normal day, and it was taking a bit while, I decided to go back through recovery mode. There, I noticed that it was hanging with eth0: link is not ready. After that, nothing.

Any help would be GREATLY appreciated.:(

---

### Post by mbradlcu on 2007-05-21
I'm sure there's a better way to do this but,, 
use a live CD and mount you're HD to /mnt, I'm going to guess about your hardware and setup here:

```
mount /dev/hda1 /mnt
```
```
cd /mnt/etc
```
I use vi but use nano or what ever you're comfortable with:
```
vi /mnt/etc/network/interfaces
```
and comment out the offending interface
```
#auto eth0
#iface eth0 inet dhcp

```

ok so you should be able to boot up now,, I don't have a wireless card on this machine, I'll post more when I'm on my craptop.

check out the 'dmesg' command and see if it reveals why it's hanging at the network stage.

---

### Post by weatherman1293 on 2007-05-21
Still no go, now it stops at the line before that.

---

### Post by mbradlcu on 2007-05-21
aarrgg,,, I have experienced this problem but it was due to a bug with ldap,, I'm guessing this isn't your case,, anyway now what does it stop at? ,, and just to clarify this started happening after you installed your wireless nic driver?

---

### Post by weatherman1293 on 2007-05-21
It stops as it's trying to find an EIP

---

### Post by mbradlcu on 2007-05-21
humm, it's getting a little deep for my skill set but,, EIP is the instruction pointer (here's a great site with more info then you may want to know [http://www.win.tue.nl/~aeb/linux/lk/lk-2.html](http://www.win.tue.nl/~aeb/linux/lk/lk-2.html)).. I'm guessing you installed a module for your new network card,, if so I would remove any insistence in the /etc/rc.* that try to load the new module. If you need help on how to do this let me know.,,

---

### Post by weatherman1293 on 2007-05-22
Alright, I need your help with that!

---

### Post by mbradlcu on 2007-05-23
actually I'm not sure,, I think the modules would be invoked with a script in /etc/init.d/  but maybe not.. it could also be invoked by /etc/modules. sorry I can't be more helpful ; (

---

