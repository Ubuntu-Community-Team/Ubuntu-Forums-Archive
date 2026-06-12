---
title: "Upstart not running at boot"
date: 2013-01-26
forum: General Help
---

### Post by dave01945 on 2013-01-26
Hi all I have been trying to figure out my problem for some time and think it is now time to ask someone who know more than me. Hopefully this is only a simple solution for someone in the know

Basically I have 2 upstart scripts that I created but only 1 will run at boot and the other will not although both run fine when called manually

Here is the one that works

```
# status led daemon
#

description "Status led daemon; Used for controlling the server status led"
author "None"

start on (started dbus and started mountall)
stop on (xbmc-do-stop or runlevel [!2345])

exec led.sh
respawn
```

and here is the one that does not

```
# irexec daemon
#

description "irexec daemon"
author "None"

start on (started dbus and started mountall)
stop on (xbmc-do-stop or runlevel [!2345])

exec irexec /home/pi/.lircrc
respawn
```

as you can see they are very similar and I cannot find out why one will work but the other will not

Thanks

---

