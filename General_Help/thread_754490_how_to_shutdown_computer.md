---
title: "how to shutdown computer?"
date: 2008-04-13
forum: General Help
---

### Post by d_deniz on 2008-04-13
how can i shutdown the computer from a terminal? I cant reach desktop while the computer is on. so I have to do it from terminal
however when I typed
```
shutdown (1 minute after as time)
```
it says
```
stopping system deamon---------------------------------[[COLOR="Red"]fail[/COLOR]]
stopping periodic command schedular------------------[[COLOR="Red"]fail[/COLOR]]
```
and the computer is not closed

it came here from the point
```
Starting up...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/c7c2ccbc-18c3-4137-9cb2-f5cc7220f73) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/c7c2ccbc-18c3-4137-9cb2-f5cc7220f73
kinit: no resume image, doing normal boot...
```

---

### Post by oldos2er on 2008-04-13
Try "sudo shutdown"

---

### Post by d_deniz on 2008-04-13
shutdown command needs a time to work
I used this command if you read above
the problem is bigger than shutting down
it is possibly about hibernating, and ubuntu didn't hibernate properly once so it cause problem now.

---

### Post by Kralizec on 2008-04-13
When I want to shutdown or restart from a terminal I use ```
sudo poweroff
``` or ```
sudo reboot
```. The shutdown command shuts down your system but not the computer itself. If you want to power off your computer with the shutdown command, try ```
sudo poweroff -P now
```.

---

### Post by redoscar3 on 2008-04-13
I would generally use a command such as:

sudo shutdown -h now

It has always worked for me in the past.

Red

---

### Post by ghostdog74 on 2008-04-13
init 0

---

