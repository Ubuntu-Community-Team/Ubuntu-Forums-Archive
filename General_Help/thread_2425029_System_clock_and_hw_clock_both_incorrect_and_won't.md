---
title: "System clock and hw clock both incorrect and won't sync with server"
date: 2019-08-19
forum: General Help
---

### Post by cornsay on 2019-08-19
Hello, 

I am running xubuntu 18.04.3 LTS. This is a recent upgrade over an old install used by whoever had this computer and office before me.

The system clock (as displayed in the panel) is about 15 minutes slow. This does not correct when I set the timezone correctly and set it to sync with servers through the GUI. It also does not correct whatever settings I try to change using timedatectl.

It appears that the hardware clock is also running 15 minutes slow, and I can't work out how to get that to work either. 

At present, hwclock --debug returns:

```
hwclock from util-linux 2.31.1
System Time: 1566216653.231452
Trying to open: /dev/rtc0
Using the rtc interface to the clock.
Assuming hardware clock is kept in UTC time.
Waiting for clock tick...
...got clock tick
Time read from Hardware Clock: 2019/08/19 12:10:54
Hw clock time : 2019/08/19 12:10:54 = 1566216654 seconds since 1969
Time since last adjustment is 1566216654 seconds
Calculated Hardware Clock drift is 0.000000 seconds
2019-08-19 14:10:53.217380+0200


```

hwclock --systohc says:

```
hwclock: Cannot access the Hardware Clock via any known method.
hwclock: Use the --debug option to see the details of our search for an access method.

```

and timedatectl says:

```
 Local time: mån 2019-08-19 14:10:11 CEST
                  Universal time: mån 2019-08-19 12:10:11 UTC
                        RTC time: mån 2019-08-19 12:10:11
                       Time zone: CET (CEST, +0200)
       System clock synchronized: yes
systemd-timesyncd.service active: yes
                 RTC in local TZ: no

```

Any ideas how I can get the time to sync right and stay right?

---

### Post by SeijiSensei on 2019-08-19
Did you run the hwclock command as root with sudo?

```
sudo hwclock --systohc
```

Only root can write to the hardware clock.

---

### Post by cornsay on 2019-08-19
Ah, OK. I hadn't. So, having done run that command as root, the clocks now seem to be right. Will see if they still are tomorrow (about to leave work for the day).

---

