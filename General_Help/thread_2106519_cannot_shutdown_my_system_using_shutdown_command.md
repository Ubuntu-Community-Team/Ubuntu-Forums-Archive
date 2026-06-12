---
title: "cannot shutdown my system using shutdown command"
date: 2013-01-19
forum: General Help
---

### Post by pdbon19 on 2013-01-19
i cannot shutdown my system using shutdown command in terminal. after the command executes it gets stuck in ubuntu screen for about 30 mins and then it switches to single user mode with the following message..

Uch file or directory could not get the system bus. Make sure the message bus daemon is running!
Failed to connect to socket /var/run/dbus/system_bus_sock[fail]s

how can i fix this?

---

### Post by efflandt on 2013-01-19
Are you using **sudo shutdown -h now** (or **sudo halt** which does the same thing)?

---

### Post by pdbon19 on 2013-01-19
> **efflandt said:**
> Are you using **sudo shutdown -h now** (or **sudo halt** which does the same thing)?

i used sudo shutwown now and sudo shutdown hh:mm

---

### Post by efflandt on 2013-01-19
If you do not include -h option (or -r to reboot) how is shutdown supposed to know what you want it to do?  In a terminal read: **man shutdown**

Or else you can simply do **sudo halt** (or **sudo reboot** to reboot now).

If you are trying to do it remotely (via ssh, etc.) it would be best to do the following to make sure that sudo is active without having to enter a password for the last command:
```
sudo -v
nohup sudo halt
```

---

### Post by pdbon19 on 2013-01-19
> **efflandt said:**
> If you do not include -h option (or -r to reboot) how is shutdown supposed to know what you want it to do?  In a terminal read: **man shutdown**

Or else you can simply do **sudo halt** (or **sudo reboot** to reboot now).

If you are trying to do it remotely (via ssh, etc.) it would be best to do the following to make sure that sudo is active without having to enter a password for the last command:
```
sudo -v
nohup sudo halt
```

okay, if i use shutdown command with the argument **-h **or **-r **it works.
but **sudo halt **still doesn't work for me. it gets stuck in the ubuntu screen.

---

### Post by pdbon19 on 2013-01-19
if i press esc it shows system is halted, but i had to turn off the power supply to shut it.

---

### Post by efflandt on 2013-01-19
Sorry about that, I usually use **sudo shutdown -h now** in Ubuntu, and only used **sudo halt **on a little Debian based Raspberry Pi on credit card size board, which then has to be unplugged because it has no power switch.

---

### Post by pdbon19 on 2013-01-19
> **efflandt said:**
> Sorry about that, I usually use **sudo shutdown -h now** in Ubuntu, and only used **sudo halt **on a little Debian based Raspberry Pi on credit card size board, which then has to be unplugged because it has no power switch.

Thanks

---

