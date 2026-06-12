---
title: "Firestarter fails at startup"
date: 2006-08-28
forum: General Help
---

### Post by xinix on 2006-08-28
I can't get firestarter to load at startup.  I know that the app I start when I'm logged in is just a gui for ip tables.  But I get "Starting Firestarter: Failed"  as the boot text flies by.  I assume that this means that it's trying to start the ip tables firewall and is failing.  How can I fix this?

thanks

---

### Post by kaamos on 2006-08-28
Hello!

Try this: open a terminal, type
```
gksudo firestarter
```
and press the "start" button in firestarter to see if you get an error message to the terminal.

---

### Post by xinix on 2006-08-28
I should have mentioned.  If I start it manually it seems to work.
If I run ```
/etc/init.d/firestarter start
```it starts up.  I don't understand why it fails at boot.

---

### Post by yopnono on 2006-08-28
are you using network-manager? and you need to enter a password at login.
Then thats you problem, the firestarter don't start until the network interface is up and running.

---

### Post by xinix on 2006-08-28
yes I was using it. no need for it so I took it off and firestarter loads at boot now.  thanks

---

