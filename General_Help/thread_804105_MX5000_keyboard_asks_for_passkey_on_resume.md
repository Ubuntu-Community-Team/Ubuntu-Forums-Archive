---
title: "MX5000 keyboard asks for passkey on resume"
date: 2008-05-22
forum: General Help
---

### Post by bungee_70 on 2008-05-22
Hi,

I set up my MX5000 set as per this [howto]("http://ubuntuforums.org/showthread.php?t=432013"). The set is kind of hard mapped and the keyboard doesn't need a passkey to work. 

Except when resuming from hibernation: the keyboard always require a passkey upon resuming and I don't understand why and don't want to. There is no passkey displayed on the screen to type in the keyboard, so it is stuck.

I edited /etc/default/acpi-support to add bluetooth to the services to stop and restart, but it seems to me that it doesn't work anymore since I upgraded to 8.04. The only thing I can do to make the keyboard work again is to type
```
sudo /etc/init.d/bluetooth restart
```
which is very annoying (not counting that I must type my password on another keyboard to execute the command). I tried to add the line to the end of resume.sh (save the 'sudo') but it has no effect.

Please help! Thank you!

---

### Post by bungee_70 on 2008-07-18
Bump

---

