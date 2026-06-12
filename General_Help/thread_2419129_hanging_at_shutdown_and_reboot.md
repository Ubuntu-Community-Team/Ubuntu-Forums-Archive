---
title: "hanging at shutdown and reboot"
date: 2019-05-17
forum: General Help
---

### Post by Skaperen on 2019-05-17
many times, but not always, when i shutdown (sudo halt -p) or reboot, the whole system hangs for about a minute and a half.  i suspect some process is not going away when every process is sent a TERM signal (then later is a KILL signal that can't be trapped).  what i would like to do is run a process that *also* stays alive after the big TERM signal and after about 45 seconds does a "ps" command redirected to a file so i can see what processes were still running.  early this morning, i did a reboot then a 2nd reboot after cleaning up a few huge files that filled up /var.  the 2nd reboot hung while going down, after being up for about 4 minutes.  can someone suggest *how* to do this?

---

### Post by VMC on 2019-05-17
Edit start/stop "system.conf to remove long shutdowns:
```
sudo sed -i 's/\#DefaultTimeoutStartSec=90s/DefaultTimeoutStartSec=10s/' /etc/systemd/system.conf
sudo sed -i 's/\#DefaultTimeoutStopSec=90s/DefaultTimeoutStopSec=10s/' /etc/systemd/system.conf
```

---

### Post by Skaperen on 2019-05-17
i don't want to shorten those time settings because if there happens to be something running that needs to save data and clean up, i want to give it a good opportunity to finish doing it.  i just want to know what is running this long and see if it is something that can be cut off faster.  it way be something that is just ignoring all signals.  i hope i can do this in python.

---

### Post by DuckHook on 2019-05-17
On my systems, disabling "quiet splash" in GRUB allows many startup and shutdown processes to display. Misbehaving shutdown processes in particular are revealed.

---

### Post by Skaperen on 2019-05-18
i can probably find where that is set, now, if it is explicitly coded, already.  but i don't know how to rebuild grub once i change that file, or if i really need to (my / fs is ext4).

what i am thinking of trying is a bash script with a trap to ignore SIGTERM and do a loop 30 times around "sleep 1" followed by "ps awux >> /root/ps.out".

---

### Post by VMC on 2019-05-18
> **DuckHook said:**
> On my systems, disabling "quiet splash" in GRUB allows many startup and shutdown processes to display. Misbehaving shutdown processes in particular are revealed.
I never could find the offending process that hangs. I've remove quiet, splash in the past, but nothing showed up as I remember. Good point if it does though.

---

### Post by VMC on 2019-05-18
> **Skaperen said:**
> i can probably find where that is set, now, if it is explicitly coded, already.  but i don't know how to rebuild grub once i change that file, or if i really need to (my / fs is ext4).

what i am thinking of trying is a bash script with a trap to ignore SIGTERM and do a loop 30 times around "sleep 1" followed by "ps awux >> /root/ps.out".
"**/etc/default/grub**" edit out the quiet, splash from there.

---

### Post by Skaperen on 2019-05-18
i made a little bash script:

```
#!/bin/bash
trap "sleep 35;(date;ps awux) >> /root/ps.out;sync;exit" term hup quit usr1 usr2
sleep 120
touch /root/waitps_was_not_killed
```

i modified my reboot script to run this script (i named /root/waitps) in the background before doing the reboot command.  it worked.  it was sent the SIGTERM signal like all other processes, waited 35 seconds, then appended the date and the output of ps to /root/ps.out.  not including kernel processes or defunct processes there were 139 processes running, 52 of which were in disk i/o wait.  lots of desktop processes were running.  one of my cron scripts was also running.

then i did a quick reboot immediately after the system came up to capture a minimal reference case.  this had 14 running processes.

i'll leave this in place to capture more data and look for patterns.

---

