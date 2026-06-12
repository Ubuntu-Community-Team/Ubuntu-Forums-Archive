---
title: "Compaq Presario C500 laptop hangs on shutdown"
date: 2014-06-04
forum: General Help
---

### Post by vap32 on 2014-06-04
Ubuntu 14.04 LTS i686 (32bit)


Cannot seem to find a proper solution.

I've tried powering down with most shutdown/reboot commands

```
sudo shutdown -h now 
```etc.

Nothing seems to be working at this point.

---------------------------------------------------------------

When trying normal shutdown, I get:

```
nm-dispatcher.action;caught signal 15, shutting down
modemmanager [777] <info> caught signal shutting down
modemmananger [777] <warn> couldnt not aquire the
'org.freedesktop.modem manager1' service name     [FAIL]


Stopping early crypto disks   [FAIL]

Mount:/ is busy
* Will now halt      [OK]
```

When hitting esc at the shutdown splash screen, hope that helps with identifiying the problem. 

Any information on this issue, is greatly appreciated!

---

