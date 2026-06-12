---
title: "Latop keeps freezing"
date: 2019-06-09
forum: General Help
---

### Post by gmc1 on 2019-06-09
I've got a Asus X553MA latop. Was previously running Debian 9 and there were a few things I didn't like so decided to reformat and install Ubuntu 19.04
Kernel 5.0.0-16-generic.

After 30-60 mins of using the laptop it randomly crashes.  Tried re-installing and trying the previous 3 kernels. All made no difference. Also tried 18.04

Not sure what all logs to provide, I've checked through kernel and dmesg and don't see any issues.

/var/crash is empty.


kernel:
[https://pastebin.com/rVCNykYr](https://pastebin.com/rVCNykYr)

dmesg:
[https://pastebin.com/P6uCkGqe](https://pastebin.com/P6uCkGqe)

lshw:
[https://pastebin.com/ZNWtg7HA](https://pastebin.com/ZNWtg7HA)

Any tips on what I can do? its really unusable like like. Previously has no issues no Debian 9, also tried the latest OpenSUSE Tumbleweed, also no freezing. This issue is specific to Ubuntu.

I've also upgraded my PC (GigaByte and its working fine there), so maybe some hardware incompatibility with Ubuntu?

free -h
```

              total        used        free      shared  buff/cache   available
Mem:          7.7Gi       1.0Gi       5.1Gi       168Mi       1.5Gi       6.2Gi
Swap:         2.0Gi          0B       2.0Gi

```

swapon -s
```

Filename                Type        Size    Used    Priority
/swapfile                                  file        2097148    0    -2


```

---

### Post by TheFu on 2019-06-10
Laptops are funny machines.

I googled the model, asus, ubuntu and saw lots of people having issues with Linux on that model.
[https://askubuntu.com/questions/742874/asus-x553m-laptop-has-trouble-booting-live-cd-installing](https://askubuntu.com/questions/742874/asus-x553m-laptop-has-trouble-booting-live-cd-installing) has a BIOS suggestion.  You've tried that already?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1391908](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1391908)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1810210](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1810210)

Are there any errors in the log files? ** sudo egrep -i 'err|warn' /var/log/*g**
Sometimes the logs don't get flushed to disk when a system is crashing. 

 I'm having that issue on 1 of my newer systems.  It worked great for 6 months before crashing twice over a 2 week period. I've tried to setup journalctl to hold more boot/logs and just need the next crash to happen (in theory).

Are you positive it is really a crash? Does changing to a different tty help <cntl-alt>-F1, F2, F3, ... ?  
Cannot ssh into the machine from a different computer?  Sometimes a GUI issue can appear like a crash.  

Because this is your first post here, I can't tell the level of expertise.

---

### Post by mdurham on 2019-06-10
Have you monitored the temperature?

---

### Post by &amp;wP*!) on 2019-06-11
**/var/log/syslog** files are rotated daily. So you must have a rescued /var/log/syslog.1 next day.
As **mdurham** suggested, temperature might be a problem. Some process is keeping the computer busy. Maybe.
Without **/var/log/syslog** it is difficult to judge.
What about **/var/log/kern.log** ?
Do you hear CPU fan running like hell?

Give us the output of following commands:
```
sensors
hddtemp (for harddrive)
sudo smartctl -l scttemp /dev/sda (for SSD device temperature parameters)
lscpu
```

---

### Post by HermanAB on 2019-06-12
Linux is the same difference.

The best solution is usually just to hunt around for another distribution that works properly on your hardware.  Underneath the various Linux distributions are all the same anyway.  

OK, except Slackware - you need to be a sub-genius to be a Slacker.

---

