---
title: "UbuntuMATE won't boot past emergency mode..."
date: 2015-12-20
forum: General Help
---

### Post by nzdreamer55 on 2015-12-20
Hello everyone,

So I have ubuntumate on my raspberry pi.  I had been noticing it was slow to do things like open new terminal windows, ls, and some other things that I cannot remember.  When I tried rebooting it this morning it booted into emergency mode.  I tried to reboot again, it just keeps going back to emergency mode.  Tried unplugging and still cannot get it to boot properly.  It looks like I can get some output if I type "journalctl -xb".  There are some red lines but I don't have a way to capture them (maybe with my phone camera?)

Google gave me this answer

[https://www.raspberrypi.org/forums/viewtopic.php?f=56&t=124149](https://www.raspberrypi.org/forums/viewtopic.php?f=56&t=124149)

but in this case the raspberry pi would sometimes start.

So can someone give me tips of how to trouble shoot an issue like this?


Thanks

---

### Post by Bucky Ball on 2015-12-20
So you're saying you tried the fix outlined on that link you provided and now your RPi starts sometimes?

---

### Post by nzdreamer55 on 2015-12-21
> **Bucky Ball said:**
> So you're saying you tried the fix outlined on that link you provided and now your RPi starts sometimes?

Sorry it was not clear.  Yes I have tried this solution and I still get put into emergency mode.  Are there logs that I can look at that would help and what would I be looking for?  the things in red from the journalctl -xb are listed below

```
raspberry system-modules-load[88]: Failed to find module 'lp'
raspberry system-modules-load[88]: Failed to find module 'ppdev'
raspberry system-modules-load[88]: Failed to find module 'parport_pc'
raspberry systemd[1]: Failed to start Load Kernel Modules.
raspberry systemd[1]: Timed out waiting for devices dev-sdb1.device.
raspberry systemd[1]: Timed out waiting for devices dev-disk-by\x2uuid-1869FE6619D6FB.device.
raspberry systemd[1]: Failed to mount /home/pi/Scratch
raspberry kernel: CIFS VFS: Error connecting to socket. Aborting operation.
raspberry kernel: CIFS VFS: cifs_mount failed w/return code = -101

```
If I issue "systemctl default" the emergency mode prompt I get this message that just keeps coming up every 120 seconds

```
[306.263851] INFO: task plymouth:393 blocked for more than 120 seconds
[306.264119]          Not tainted 4.1.10-v7+ #821
[306.264279] "echo 0 > /proc/sys/kernel/hung_ask_timeout_sec" disables this message.
```

---

### Post by Bucky Ball on 2015-12-21
Looks like it's waiting for the device sdb1 (that would be the first partition on the second attached external hard drive ... don't know what model of RPi you are using so can't say for sure). There isn't an entry in fstab for an external device that you've since unplugged?

---

