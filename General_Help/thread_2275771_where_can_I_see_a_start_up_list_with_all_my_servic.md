---
title: "where can I see a start up list with all my services like mysql,php5,apache2."
date: 2015-04-28
forum: General Help
---

### Post by sebastiaan5 on 2015-04-28
ubuntu 14.04 LTS
When I start up my ubuntu all my services are running how can I set them off as default?

services like: mysql,apache2...

greetings

---

### Post by nerdtron on 2015-04-28
I think it's like this in ubuntu:

```
sudo update-rc.d openvpn disable
```

---

### Post by sebastiaan5 on 2015-04-28
file does not exists :/

---

### Post by nerdtron on 2015-04-28
Can you post the complete output?

---

### Post by sebastiaan5 on 2015-04-28
sudo update-rc.d openvpn status gives this:

```

update-rc.d: /etc/init.d/openvpn: file does not exist


```

---

### Post by nerdtron on 2015-04-28
because openvpn is not installed on your computer. replace it with the service you want to disable.

---

### Post by Bucky Ball on 2015-04-28
Change of tack. I'm wondering if you have the 'Save session for next time' option enabled when logging out/rebooting.

You could boot your machine, switch everything you want off at boot off, then log out and tick the 'Save Session for next time' option. Login and everything you switched off should be switched off on reboot/login. Now log out again with everything switched off and untick the 'Sessions' option. That should let you boot to a 'blank' computer and it won't save whatever you open for next boot when you reboot/shutdown/logout. 

You can also look in Session & Startup>Startup Applications and see if anything is set to boot with the machine. Disable what you need to.

---

### Post by nerdtron on 2015-04-28
BTW.

I just remember I used a GUI tool previously on managing/enable/disable system services.

```

:~$ apt-cache show bum
Package: bum
Priority: optional
Section: universe/admin
Description-en: graphical runlevel editor
 Boot-Up Manager is a graphical tool to allow easy configuration
 of init services in user and system runlevels, as far as changing
 Start/Stop services priority.

```

Just install Boot-up Manager or bum from the software center or the command line.

---

