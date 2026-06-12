---
title: "A couple things I just can't seem to get working"
date: 2021-06-05
forum: General Help
---

### Post by DigiAngel on 2021-06-05
Hey all,

So...here's the first one (Ubuntu 20).  I have a backup scrip that runs that includes:

```
/usr/bin/gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 0
<other stuff>
/usr/bin/gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 7200
```

with the goal being to disable the machine sleep.  The above don't seem to work, even though run with my own cron and include export DISPLAY=:0;.

Is there a way to temporarily disable the system sleep?

Next up, is sysctl.conf.  For the life of me I cannot get:
```
net.netfilter.nf_conntrack_udp_timeout = 45
```
to stick...I have it in /etc/sysctl.conf and /etc/sysctl.d/zzz-myctl.conf, but I still have to manually apply it after each reboot.  Why isn't this working?

Thanks all!

---

### Post by QIII on 2021-06-05
Is this 20.04 or 20.10?

---

### Post by DigiAngel on 2021-06-05
20.04

---

### Post by TheFu on 2021-06-05
Would you consider coming at the issue from a different angle?  Perhaps using a faster/better backup method?

IMHO, if backups take more than 15 minutes, something is wrong.  Find a better backup tool. One that does incremental backups with versioning.

```
=== Time for Backups to regulus === 
StartTime 1622870104.00 (Sat Jun  5 01:15:04 2021)
EndTime 1622870250.62 (Sat Jun  5 01:17:30 2021)
ElapsedTime 146.62 (2 minutes 26.62 seconds)
TotalDestinationSizeChange 27141600 (25.9 MB)

=== Time for Backups to hadar === 
StartTime 1622871304.00 (Sat Jun  5 01:35:04 2021)
EndTime 1622871962.14 (Sat Jun  5 01:46:02 2021)
ElapsedTime 658.14 (10 minutes 58.14 seconds)
TotalDestinationSizeChange 86971131 (82.9 MB)

=== Time for Backups to romulus === 
StartTime 1622871946.00 (Sat Jun  5 01:45:46 2021)
EndTime 1622872082.94 (Sat Jun  5 01:48:02 2021)
ElapsedTime 136.94 (2 minutes 16.94 seconds)
TotalDestinationSizeChange 141437 (138 KB)

=== Time for Backups to posc === 
StartTime 1622866024.00 (Sat Jun  5 00:07:04 2021)
EndTime 1622866239.62 (Sat Jun  5 00:10:39 2021)
ElapsedTime 215.62 (3 minutes 35.62 seconds)
TotalDestinationSizeChange 29270671 (27.9 MB)
```
The first back takes the same time as an rsync, but after that each incremental backup is just a few minutes.

Does the system sleep faster than 15 minutes?
How often are backups performed?

Backup one system here only 2x a week. It takes a long time, but that's because there are over million files on it. Lots of tiny files makes backups slower.  That system never sleeps as it is a NAS for the house.

Just another option.

On one of my laptops, it does backups nightly and a few minutes after those finish, it goes into suspend mode.
```
#!/bin/bash

/root/bin/backup-to-rom.sh 
sleep 2m
/usr/sbin/pm-suspend

```
That is the actual script I've been using for years.  It runs as root - that's necessary for system-level backups to get all the permissions, files, acls, and xattrs.

For 20.04, the Ubuntu Guide has this: [https://help.ubuntu.com/lts/ubuntu-help/power-autosuspend.html.en](https://help.ubuntu.com/lts/ubuntu-help/power-autosuspend.html.en) . Not really all that useful.  There is a program called Caffeine.  I've never used it.

On my systems, when I want to prevent a screen from blanking or sleeping (though I don't have sleep/suspend enabled unless I close a laptop lid), I use:
```
#!/bin/bash
xset s off &
xset -dpms &

# Disable the screensaver
/usr/bin/xscreensaver-command -exit
```
to disable sleeping. And
```
#!/bin/bash
# Enable the screensaver
/usr/bin/xscreensaver &

xset +dpms &
xset s on &
```
to re-enable it afterwards.
No idea if that is sufficient for Gnome, but it could help lurkers in a few months.  If Gnome uses xscreensaver, it should work. If not - who knows?  However neither of those commands will work from cron.  They require a GUI session - probably X11 (not Wayland) - to work.

---

### Post by DigiAngel on 2021-06-07
Appreciate the response.

---

