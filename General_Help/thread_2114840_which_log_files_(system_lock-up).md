---
title: "which log files? (system lock-up)"
date: 2013-02-11
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2013-02-11
i was playing STK 0.8 (raring) when the system locked up. audio player was just playing the last second or less over and over, no mouse movement, panels froze 
running xubuntu 12.10 (quantal) 64bit with linux 3.8.0-5-generic (raring)
i tried to do the reisub (ctrl+alt+sysrq+reisub) thing, but i could not get it right or it would not respond
which log files should i be looking in for what happened, assuming it was able to write to the log when it locked up
edit: just remembered i had flash buffering a video (server is slow atm)

---

### Post by dino99 on 2013-02-11
the first log to glance at is : ~/.xsession-errors
then /var/log/dmesg

if that issue is reproducible, then you can test by adding:

- nmi_watchdog=0 to the boot line (replacing "quiet splash")
- and/or : debugpat

these parameters can be set permanently inside /etc/default/grub; then update-grub might be run

---

### Post by zika on 2013-02-11
> **dino99 said:**
> the first log to glance at is : ~/.xsession-errors
then /var/log/dmesg

if that issue is reproducible, then you can test by adding:

- nmi_watchdog=0 to the boot line (replacing "quiet splash")
- and/or : debugpat

these parameters can be set permanently inside /etc/default/grub; then update-grub might be runOr ```
echo 0 | sudo tee -a  /proc/sys/kernel/nmi_watchdog
```to change without reboot if needed...

---

### Post by dino99 on 2013-02-11
> **zika said:**
> Or ```
echo 0 | sudo tee -a  /proc/sys/kernel/nmi_watchdog
```to change without reboot if needed...

yeah of course; but OP said "system locked"
so how do you set "echo ...." with a system locked ?   ):P

---

### Post by zika on 2013-02-11
> **dino99 said:**
> yeah of course; but OP said "system locked"
so how do you set "echo ...." with a system locked ?   ):PTrue, I was just giving an option if OP do anticipate locking next time... Not competing, just giving options... Also giving a way to check if setting worked after boot...
> **zika said:**
> Or ```
echo 0 | sudo tee -a  /proc/sys/kernel/nmi_watchdog
```to change without reboot **if needed**...

---

### Post by pqwoerituytrueiwoq on 2013-02-11
dmesg has nothing useful, based on uptime numbers
xsession errors appears to be the same, mostly just gmusicbrowser output
only thing that may be useful is syslog and kernel.log

i did test the resuib thing after i posted to see if it worked and i was doing it right when it locked up

so far today i booted up around 3:30 am eventually locked up
offered dad chance to check email on my guest session
went back to what i was doing
forced to hold power button to reboot
booted backup 
posted here
tested the reisub thing
current session

when i figure out what time it locked up i will edit that in here
edit: seems it was around 6:30 (probably 6:35) when it locked up

---

