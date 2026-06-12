---
title: "Problem with adept"
date: 2007-04-17
forum: General Help
---

### Post by amsch on 2007-04-17
"Database locked - another process is using the system package database..."

I have restarted the PC several times without any success. Can anybody help me please?

---

### Post by phidia on 2007-04-17
What do you get from > top and > ps typed in a terminal window?
Have you tried leaving the computer on for awhile to see if the package manager finishes updating it's database?

---

### Post by amsch on 2007-04-17
How long do you think this should last? I left the PC for  over 2 hours without success!

```

 8436 boinc     34  19  303m  81m 3004 S 95.9  8.0  27:31.99 wcg_faah_autodo
 8815 andreas  -99   0 32908  10m 6996 S  2.0  1.1   0:03.95 tvtime
 5280 andreas   15   0  249m 119m  28m S  0.7 11.8  16:58.47 firefox-bin
 3267 root      10  -5     0    0    0 S  0.3  0.0   0:03.37 usb-storage
 4483 root      15   0  107m  83m  11m S  0.3  8.3  16:20.57 Xorg
 4589 gkrellmd  15   0 10856 1268 1040 S  0.3  0.1   0:55.81 gkrellmd
 8834 andreas   15   0 32540  15m  12m R  0.3  1.5   0:00.67 konsole
    1 root      16   0  1628  540  448 S  0.0  0.1   0:01.08 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.48 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 events/0
    5 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.09 kblockd/0
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify
  126 root      10  -5     0    0    0 S  0.0  0.0   0:00.03 kseriod
  159 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  160 root      15   0     0    0    0 S  0.0  0.0   0:00.14 pdflush
  161 root      15   0     0    0    0 S  0.0  0.0   0:00.42 kswapd0
  162 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
 1694 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0
 1850 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 2059 root      10  -5     0    0    0 S  0.0  0.0   0:00.41 kjournald
 2132 root      15   0  1600  540  468 S  0.0  0.1   0:00.00 logd
 2286 root      14  -4  2640 1072  360 S  0.0  0.1   0:00.26 udevd
 3073 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 shpchpd
 3142 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused
 3238 root      15   0     0    0    0 S  0.0  0.0   0:00.00 saa7134[0]
 3266 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 3418 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt
 4077 root      16   0  1600  504  432 S  0.0  0.0   0:00.00 getty
 4078 root      16   0  1596  504  432 S  0.0  0.0   0:00.00 getty
 4079 root      16   0  1600  504  432 S  0.0  0.0   0:00.00 getty
 4080 root      16   0  1600  508  432 S  0.0  0.0   0:00.00 getty
 4081 root      16   0  1596  504  432 S  0.0  0.0   0:00.00 getty
 4082 root      16   0  1600  508  432 S  0.0  0.0   0:00.00 getty
 4266 root      16   0  2200 1148  640 S  0.0  0.1   0:00.00 acpid
 4374 root      15   0  1724  512  420 S  0.0  0.0   0:00.02 dd
 4376 klog      16   0  2392 1272  384 S  0.0  0.1   0:00.04 klogd
 4395 messageb  15   0  2172  828  640 S  0.0  0.1   0:00.14 dbus-daemon
 4410 haldaemo  15   0  7268 5736 1644 S  0.0  0.6   0:02.93 hald
 4411 root      16   0  2908 1064  896 S  0.0  0.1   0:00.01 hald-runner
 4417 haldaemo  25   0  2024  808  692 S  0.0  0.1   0:00.00 hald-addon-acpi
 4421 haldaemo  15   0  2024  812  692 S  0.0  0.1   0:00.06 hald-addon-keyb
 4434 haldaemo  15   0  2024  836  716 S  0.0  0.1   0:00.61 hald-addon-stor
 4436 haldaemo  15   0  2024  832  716 S  0.0  0.1   0:00.49 hald-addon-stor
 4438 haldaemo  16   0  2024  832  716 S  0.0  0.1   0:03.00 hald-addon-stor
 4440 haldaemo  16   0  2024  836  716 S  0.0  0.1   0:01.51 hald-addon-stor
 4463 root      16   0  2680  636  508 S  0.0  0.1   0:00.00 kdm
 4488 root      16   0 21292 1196  816 S  0.0  0.1   0:00.00 hpiod
 4490 root      15   0  3656 1448 1108 S  0.0  0.1   0:00.01 kdm
andreas@neo:~$ ps
  PID TTY          TIME CMD
 8835 pts/1    00:00:00 bash
 8839 pts/1    00:00:00 ps

```

---

### Post by firebadger on 2007-04-17
I think an apt process died on you without cleaning up after itself.  I've had that happen to me before and I can't remember exactly what I did.  Running apt directly might give a clue...

sudo apt-get update
sudo apt-get upgrade

---

### Post by amsch on 2007-04-17
Thx - this solved my problem!

---

