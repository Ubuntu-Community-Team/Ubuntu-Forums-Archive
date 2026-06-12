---
title: "Do we have to configure Ubuntu for SSD ?"
date: 2015-07-19
forum: General Help
---

### Post by checoimg on 2015-07-19
H, I'm using Ubuntu GNOME with EXT4 and an SSD

I have followed a tutorial that says to modify "/etc/rc.local" by adding FSTRIM. But I have read that nowadays Ubuntu 15.04 does all the necessary things for SSD's. Should I leave it to Ubuntu GNOME to do the configuration of the SSD features ?

Thank you for your attention6370

---

### Post by checoimg on 2015-07-19
I guess that if you make "fstrim -v /" it will also try to trim the external HDD's plugged at the moment of the trim.

---

### Post by oldfred on 2015-07-20
My old SSD was before Ubuntu added some trim, so I have my own script that was daily and created a log entry.
But Ubuntu version is weekly (not sure if better than daily or not) and does some checks on models as supposedly some models have issues with trim.
So I turned off Ubuntu verions, and added my version back again.
I also edit fstab with noatime, and make sure there is some unallocated space on SSD.
If an older BIOS system make sure AHCI is on for trim to work.

       [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

[http://linux.slashdot.org/story/15/06/16/201217/trim-and-linux-tread-cautiously-and-keep-backups-handy](http://linux.slashdot.org/story/15/06/16/201217/trim-and-linux-tread-cautiously-and-keep-backups-handy)

My script is this one, copied into cron daily and made executeable:
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

       
 ```
#!/bin/sh
# trimSSD
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
# fstrim -v /home >> $LOG
```

---

### Post by checoimg on 2015-07-20
What if I just copy the weekly cron file to the cron.daily folder ?

---

### Post by raptir on 2015-07-20
Ubuntu runs fstrim by default in cron.weekly. The command called is

```
fstrim --all
```

It will run fstrim on any volumes that support it. So it will not run on HDDs and the handful of SSDs that do not support fstrim. It doesn't log anything, either.

The script above allows for logging but will *only* trim the / and /home partition. So if you have a separate /boot partition or anything else that will not be trimmed (though /boot shouldn't typically need it). If your SSD does not support trim then it will not trim it with this command either. If you want logging I would use that script but replace

```
fstrim -v / >> $LOG
fstrim -v /home >> $LOG
```

with

```
fstrim --all -v >> $LOG
```

By default it runs in cron.weekly but you could easily move the stock Ubuntu script to cron.daily if you so chose. It's not really necessary though unless you run your SSD near-full all the time.

In terms of other tweaks, I agree with adding the noatime option to your file systems in fstab, since access time isn't used that often and it results in a bunch of extra writes. I would also reduce the swappiness of your system by adding the following line to /etc/sysctl.conf:

```
vm.swappiness=1
```

This stops the system from swapping unless it *really* needs to, which results in fewer writes to the system. The default value of 60 will swap idle programs even if there's plenty of free RAM.

---

### Post by checoimg on 2015-07-22
Ty :D
1

---

