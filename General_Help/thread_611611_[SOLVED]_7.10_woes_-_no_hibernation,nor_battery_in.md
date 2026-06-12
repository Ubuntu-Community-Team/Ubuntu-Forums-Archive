---
title: "[SOLVED] 7.10 woes - no hibernation,nor battery in notification"
date: 2007-11-13
forum: General Help
---

### Post by _sluimers_ on 2007-11-13
Since my upgrade..

Hibernation and suspend no longer works. It just fades and locks the screen. That's all they do now.

The battery has also disappeared from the notification window when I pull the plug, from my laptop. 
When I added "Battery charge monitor" to my panel for the first time, I got this message:
```

Can't access ACPI events in /var/run/acpid.socket! Make sure the ACPI subsystem is working and the acpid daemon is running.

```

---

### Post by DagMan on 2007-11-13
I'm not sure this will be help or not since I'm not on an Ubuntu machine but from the suggestion of the output, see if acpid is running 
```
ps -e | grep acpid
```
My output looks like this
   63 ?        00:00:00 kacpid
 4666 ?        00:00:00 acpid
and you can see that the last thing in the second thing there is acpid, which is what I was looking for.
if it isn't there try starting it up manually
```
sudo /etc/init.d/acpid start
```
and if it starts and makes all go well then you just need to add it to start on boot using something like the bum package.
If it doesn't start or doesn't exist, install it. 
There is also apparently a script in the same directory in Ubuntu called acpi-support and you might want to try to start that too.  I don't know what it does off hand but it would very likely not hurt to try.  You would start it in the same way as acpid is above.

---

### Post by _sluimers_ on 2007-11-13
Apparantly the update removed acpid, but I'm not there yet,

When I now try to start acpid I get:

```

 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                                    acpid: can't open /proc/acpi/event: Device or resource busy

```

---

### Post by tom.db on 2008-01-09
#

---

