---
title: "boot script"
date: 2007-03-01
forum: General Help
---

### Post by giannaccio on 2007-03-01
hi, I installed linux without any problem, except for the network.
at every boot i have to do the commands:

rmmod islsm_pci islsm_device islsm
modprobe ndiswrapper


how i can run the commands automaticly at the boot system?

---

### Post by colo on 2007-03-01
By appending them to "/etc/rc.local".

Regarding modules, this isn't advised though. You should use "/etc/modules/blacklist" for modules you want to prevent from loading, and "/etc/modules.autoload.d/kernel-2.6" you want to load explicitely.

(Those filenames cited from the top of my head - may be inaccurate, just poke around, as the naming is pretty self-explanatory.)

---

### Post by paxmanchris on 2007-03-01
assuming your useing gnome ubuntu:

write a bash script for your code in a file.. call it start.sh, save in home directory
```

#!/bin/bash
rmmod islsm_pci islsm_device islsm
modprobe ndiswrapper


```

then go to your menu:
System -> pref -> sessions 
click on [Startup Programs] tab
click on [add] button
click on [browse] button, find your bash script, click on [open] button

this should work

---

### Post by colo on 2007-03-01
This approach kinda sucks for things that affect all of your system, because it only kicks in when your User logs in. Furthermore, module (un)loading require elevated privileges. which the script simply won't have that way. You could use sudo, which would fail due to the password requirement in its default configuration.

Bottom line is: just don't do it that way. That's how you should start all-userspace, non-system-wide, personal stuff you want to have under X11 with GNOME only.

---

### Post by giannaccio on 2007-03-02
thx for the reply

I tried for first:

By appending them to "/etc/rc.local" and it's work well ;)

thx :)

---

