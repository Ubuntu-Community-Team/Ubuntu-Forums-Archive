---
title: "How to get ROOT or SU rights ?"
date: 2007-05-05
forum: General Help
---

### Post by freshman on 2007-05-05
Hi,

have been fighting with sound problem with my laptop, following
this wiki page:
[http://www.thinkwiki.org/wiki/Problem_with_broken_sound_on_ThinkPad_600]("http://www.thinkwiki.org/wiki/Problem_with_broken_sound_on_ThinkPad_600")

Trying to apply those commands with **sudo**
```
# echo 'activate' > /sys/devices/pnp0/00:05/resources 
# echo 'activate' > /sys/devices/pnp0/00:06/resources
```

getting **Permission denied**

Is it possible to do this at all?

---

### Post by merlinus on 2007-05-05
You might try prefacing the commands with sudo, e.g. sudo echo .....

hth....

-merlin

---

### Post by PilotJLR on 2007-05-05
Do this:
```

sudo -s

```
and then enter these commands. "sudo <command>" doesn't work when you redirect something to a file/device.

---

### Post by freshman on 2007-05-05
I've added root password with sudo passwd command. At least, no Permission denied messages anymore

---

### Post by bettlebrox on 2007-05-05
If you need this done at boot time create a startup script and it will be executed as root.

---

