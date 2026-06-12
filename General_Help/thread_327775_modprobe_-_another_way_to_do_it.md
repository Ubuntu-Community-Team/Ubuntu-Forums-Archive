---
title: "modprobe - another way to do it?"
date: 2006-12-29
forum: General Help
---

### Post by Scorpuk on 2006-12-29
I have installed the drivers for my Soundgraph iMON vfd / ir panel, but everythime I reboot I need to do the following as root user:

```
sudo modprobe lirc_dev
sudo modprobe lirc_imon
```

I have tried adding those commands in as a cron job to run at system startup, but no luck.

Currently my cron job order is:

modprobe lirc_dev
modprobe lirc_imon
lircd
chmod 666 /dev/lcd0   {need this line to allow all users to write to the device otherwise only root can}
perl /home/john/time.pl {This perl script displays the system time in a loop so that it updates constantly}


When my computer boots the clock is not running. I have to manually type: 

```
sudo modprobe lirc_dev
sudo modprobe lirc_imon
```

and then it starts. All the other commands are running, but waiting for the appropriate modprobe.


So is there another way of doing the modprobe so that I have access to my lcd panel?


Any help is much appreciated. :)

---

### Post by tokj on 2006-12-29
You can insert *lirc_dev* and *lirc_imon* in the file */etc/modules* (edit it with a text editor).

In that way the two modules will be loaded on boot.

Cheers :mrgreen:

---

### Post by Scorpuk on 2006-12-29
added the two to /etc/modules and rebooted, but it doesnt look like its worked.


I still had to do the modprobes at the terminal. Infact /dev/lcd0 didnt exist until i completed both.


copy of my /etc/modules file:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
lib_dev
lib_imon
```

---

### Post by Scorpuk on 2006-12-29
LOL

notice the typo's in my modules file?


I didn;t until now and I even copied and pasted it here.

OMG

](*,) 


I'll try again with the right speeling ;)

---

### Post by Scorpuk on 2006-12-29
Update:


The modules have loaded, but I now have a different problem. :D 


If I keep the following as cron jobs, to be run at system startup:

```
chmod 666 /dev/lcd0
perl /home/perl/time.pl
```

(both run as root)

I get an error message once the computer has auto logged me on:

> failed to initialise HAL


hmmmm :-k

---

### Post by pejcao on 2007-03-21
Can you control the VDF in ubuntu? (lcdproc/lcd4linux)
Does the knob on the vdf work? (vol up/down, mute)

---

