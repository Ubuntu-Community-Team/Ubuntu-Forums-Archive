---
title: "Ubuntu becomes so slow and memory is full"
date: 2019-08-01
forum: General Help
---

### Post by hrmon on 2019-08-01
Hi!
Lately I have been trying some distros on my laptop. before that I was using ubuntu 18.04 with no problem. But now I am back again on ubuntu 18.04 and facing a strange problem.
Every time after about two days of uptime the system becomes too slow and almost unusable. Even mouse cursor stops working. So I have to restart the system.

I have 8GB memory and it becomes almost full (it's not all buffer/cache). The apps I usually use are vscode, chrome (I tried firefox for a while but nothing changed), telegram and tor.

I use the command below to get total memory usage by active processes:


```

$ ps -e -o rss | paste -sd+ | bc
2773015

```


so it is about 2.7GB. but this is what `free -m` says:

```

$ free -m
               total        used        free      shared  buff/cache   available
 Mem:           7868        6881         220         324         766         413
 Swap:          4095        2297        1798

```

I try to clear cache but it doesn't help:

```

$ sync; echo 3 > /proc/sys/vm/drop_caches
$ free -m
              total        used        free      shared  buff/cache   available
Mem:           7868        6976         213         400         677         243
Swap:          4095        2410        1685

```

It is really annoying, I have searched everywhere I know but found nothing. Can anyone help?
If any extra information is needed tell me to provide.

---

### Post by speartip on 2019-08-01
So when you run top or htop in a terminal, what is it telling you is using the memory?

---

### Post by TheFu on 2019-08-01
Unix systems don't like it when RAM is limited.  Running just a few of those programs will easily eat 8GB of RAM.  If chromium has 1 tab open to a text-only website, that's very different than having 500 tabs open to cnn, youtube, and other high-RAM-abuse websites.

Also, bad GPU drivers can be a huge issue. Be certain you are running the Canonical recommended GPU driver for the hardware you have. In general, it is a bad idea to get the driver directly from AMD or nvidia.  

Don't be afraid to post the batch output from **top** here.

Unix systems get slow as a way to warn users they are using too much RAM and should close some processes.  The slowness comes by using swap as virtual RAM.  If you don't want to crash, add more swap, but really that won't help the system be faster.

There could be some funky edge condition that you are experiencing.  Perhaps a kernel issue or DE issue.  Gnome3 isn't exactly "lite".

---

### Post by hrmon on 2019-08-01
Thanks for your response.
As I said using ps command to get memory usage of active processes I get no clue of who is eating memory. they all seem normal. so htop would say so. But when I face the problem again I will share its output.
About processes when I close all these apps (chrome, telegram and ...) I don't get much more available memory than 1GB out 8GB.
I use the free amdgpu driver which is installed by ubuntu installer itself. So I don't use any  proprietary drivers.
As I said the strange thing is that the last time I was using Ubuntu with same setup I had no problem.
Don't you think It can be a hardware problem? How can I check?

---

### Post by TheFu on 2019-08-01
Please prove, with command output, your claims..
Have you checked the system logs?  Things that make systems slow are often logged.

---

### Post by oldfred on 2019-08-02
That RAM is full is not unusual as Linux caches your activity as you often reuse it.
       Linux ate my RAM! -  memory use cache
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

But using swap especially with 8GB of RAM is unusual. And typically would be very slow. My old laptop with 1.5GB of RAM would turn gray for a second or two, so I learned not to load more than one large app at a time.
Are you editing videos are very large photos?

---

### Post by hrmon on 2019-08-02
OK, here is top command output:
```

top - 22:20:59 up 1 day,  4:39,  2 users,  load average: 3.80, 1.91, 2.34
Tasks: 305 total,   2 running, 249 sleeping,   2 stopped,   0 zombie
%Cpu(s): 16.2 us,  4.6 sy,  0.0 ni, 76.3 id,  1.9 wa,  0.0 hi,  0.8 si,  0.0 st
KiB Mem :  8056920 total,   150288 free,  7204636 used,   701996 buff/cache
KiB Swap:  4194300 total,  2365088 free,  1829212 used.   258856 avail Mem 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
18945 hamon     20   0  751180 123496  98000 S  32.6  1.5   0:02.59 chrome
11763 hamon     20   0  567392  57520  35528 S  25.6  0.7  20:02.93 chrome
 2766 hamon     20   0 1188900  58380  42724 S  11.6  0.7  58:50.13 Xorg
18895 hamon     20   0  765608 143440  82012 S   9.3  1.8   0:07.20 chrome
18969 hamon     20   0   52868   4044   3296 R   9.3  0.1   0:00.11 top
 2894 hamon     20   0 4063808 148256  38860 S   7.0  1.8  50:27.83 gnome-shell
11718 hamon     20   0  936784 113008  60960 R   4.7  1.4   6:08.75 chrome
18916 hamon     20   0  787072 154596  74032 S   4.7  1.9   0:04.34 chrome
18955 hamon     20   0  675488  43464  37412 S   4.7  0.5   0:00.05 chrome
   10 root      20   0       0      0      0 I   2.3  0.0   2:17.93 rcu_sched
18482 hamon     20   0 1886988 171200  44092 S   2.3  2.1   1:13.06 telegram
    1 root      20   0  225644   4492   2932 S   0.0  0.1   1:17.82 systemd
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.07 kthreadd
    3 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 rcu_gp
    4 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 rcu_par_gp
    6 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kworker/0:0H-kb
    8 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 mm_percpu_wq
    9 root      20   0       0      0      0 S   0.0  0.0   0:04.52 ksoftirqd/0
   11 root      20   0       0      0      0 I   0.0  0.0   0:00.00 rcu_bh
   12 root      rt   0       0      0      0 S   0.0  0.0   0:00.05 migration/0
   13 root      rt   0       0      0      0 S   0.0  0.0   0:00.31 watchdog/0
   14 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/0
   15 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/1
   16 root      rt   0       0      0      0 S   0.0  0.0   0:00.34 watchdog/1
   17 root      rt   0       0      0      0 S   0.0  0.0   0:00.05 migration/1
   18 root      20   0       0      0      0 S   0.0  0.0   0:05.38 ksoftirqd/1
   20 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kworker/1:0H-kb
   21 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/2
   22 root      rt   0       0      0      0 S   0.0  0.0   0:00.33 watchdog/2
   23 root      rt   0       0      0      0 S   0.0  0.0   0:00.06 migration/2
   24 root      20   0       0      0      0 S   0.0  0.0   0:05.26 ksoftirqd/2
   26 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kworker/2:0H-kb
   27 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/3
   28 root      rt   0       0      0      0 S   0.0  0.0   0:00.34 watchdog/3
   29 root      rt   0       0      0      0 S   0.0  0.0   0:00.04 migration/3
   30 root      20   0       0      0      0 S   0.0  0.0   0:07.89 ksoftirqd/3
   32 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kworker/3:0H-kb
   33 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kdevtmpfs
   34 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 netns
   35 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_tasks_kthre
   36 root      20   0       0      0      0 S   0.0  0.0   0:00.28 kauditd
   40 root      20   0       0      0      0 S   0.0  0.0   0:00.14 khungtaskd
   41 root      20   0       0      0      0 S   0.0  0.0   0:00.00 oom_reaper
   42 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 writeback
   43 root      20   0       0      0      0 S   0.0  0.0   0:20.31 kcompactd0
   44 root      25   5       0      0      0 S   0.0  0.0   0:00.00 ksmd
   45 root      39  19       0      0      0 S   0.0  0.0   0:00.00 khugepaged
   46 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 crypto
   47 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kintegrityd
   48 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kblockd
   49 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 ata_sff
   50 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 md
   51 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 edac-poller
   52 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 devfreq_wq
   53 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdogd
   58 root      20   0       0      0      0 S   0.0  0.0   3:14.48 kswapd0
   59 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kworker/u9:0-hc
   60 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ecryptfs-kthrea
  105 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kthrotld
  106 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 acpi_thermal_pm
  111 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 ipv6_addrconf
  120 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kstrp
  137 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 charger_manager
  186 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_0
  187 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 scsi_tmf_0
  188 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_1
  189 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 scsi_tmf_1
  193 root       0 -20       0      0      0 I   0.0  0.0   0:01.16 kworker/3:1H-kb
  196 root       0 -20       0      0      0 I   0.0  0.0   0:02.06 kworker/2:1H-kb
  219 root      20   0       0      0      0 S   0.0  0.0   0:00.92 jbd2/sda2-8
  220 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 ext4-rsv-conver
  249 root       0 -20       0      0      0 I   0.0  0.0   0:07.80 kworker/1:1H-kb
  252 root       0 -20       0      0      0 I   0.0  0.0   0:00.60 kworker/0:1H-kb
  260 root      19  -1  214628  10984   9708 S   0.0  0.1   0:08.65 systemd-journal
  287 root      20   0   48356   1500   1028 S   0.0  0.0   0:06.87 systemd-udevd
  412 root      -2   0       0      0      0 S   0.0  0.0   0:38.41 i915/signal:0
  413 root      -2   0       0      0      0 S   0.0  0.0   0:00.00 i915/signal:1
  414 root      -2   0       0      0      0 S   0.0  0.0   0:00.00 i915/signal:2
  415 root      -2   0       0      0      0 S   0.0  0.0   0:00.00 i915/signal:6
  428 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 cfg80211
  457 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 loop0
  458 root       0 -20       0      0      0 S   0.0  0.0   0:00.25 loop1
  459 root       0 -20       0      0      0 S   0.0  0.0   0:00.02 loop2
  460 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 loop3
  461 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 loop4
  462 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 loop5
  465 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 loop6
  466 root       0 -20       0      0      0 S   0.0  0.0   0:00.01 loop7
  467 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 loop8
  468 root       0 -20       0      0      0 S   0.0  0.0   0:00.08 loop9
  469 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 loop10
  470 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 loop11
  471 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 loop12
  472 root       0 -20       0      0      0 S   0.0  0.0   0:00.01 loop13
  473 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 loop14
  474 root       0 -20       0      0      0 S   0.0  0.0   0:00.04 loop15
  484 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 ttm_swap
  487 root      -2   0       0      0      0 S   0.0  0.0   0:00.00 gfx
  488 root      -2   0       0      0      0 S   0.0  0.0   0:00.00 comp_1.0.0
  489 root      -2   0       0      0      0 S   0.0  0.0   0:00.00 comp_1.0.1
  490 root      -2   0       0      0      0 S   0.0  0.0   0:00.00 comp_1.0.2
  491 root      -2   0       0      0      0 S   0.0  0.0   0:00.00 comp_1.0.3
  492 root      -2   0       0      0      0 S   0.0  0.0   0:00.00 comp_1.0.4
  493 root      -2   0       0      0      0 S   0.0  0.0   0:00.00 comp_1.0.5
  494 root      -2   0       0      0      0 S   0.0  0.0   0:00.00 comp_1.0.6
  495 root      -2   0       0      0      0 S   0.0  0.0   0:00.00 comp_1.0.7
  496 root      -2   0       0      0      0 S   0.0  0.0   0:00.00 sdma0
  497 root      -2   0       0      0      0 S   0.0  0.0   0:00.00 sdma1
  714 root      20   0       0      0      0 D   0.0  0.0   0:09.07 jbd2/sda3-8
  715 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 ext4-rsv-conver
  813 systemd+  20   0  146108      0      0 S   0.0  0.0   0:00.27 systemd-timesyn
  814 systemd+  20   0   71140    884    592 S   0.0  0.0   0:10.51 systemd-resolve
 1065 root      20   0   36484   1408   1144 S   0.0  0.0   0:00.05 bluetoothd
 1079 root      20   0  434388   1848   1848 S   0.0  0.0   0:00.22 ModemManager
 1082 root      20   0  110480   1144   1068 S   0.0  0.0   0:08.64 irqbalance
 1083 root      20   0  296288   2636   2044 S   0.0  0.0   0:02.46 accounts-daemon
 1084 root      20   0  188520   1584   1380 S   0.0  0.0   0:09.97 thermald
 1090 root      20   0    4552      8      0 S   0.0  0.0   0:08.72 acpid
 1095 root      20   0  503424   4024   2732 S   0.0  0.0   0:08.92 udisksd
 1103 root      20   0   70724   2048   1744 S   0.0  0.0   0:02.68 systemd-logind
 1154 root      20   0 1366792   6200    620 S   0.0  0.1   0:22.15 snapd
 1156 avahi     20   0   47312    644    400 S   0.0  0.0   0:01.50 avahi-daemon
 1170 root      20   0   39980    844    756 S   0.0  0.0   0:00.16 cron
 1171 message+  20   0   51960   3088   1100 S   0.0  0.0   0:21.02 dbus-daemon
 1284 avahi     20   0   47076     40      0 S   0.0  0.0   0:00.00 avahi-daemon
 1368 root      20   0   45600     48      0 S   0.0  0.0   0:05.82 wpa_supplicant
 1398 root      20   0  179244   2052   2000 S   0.0  0.0   0:00.31 networkd-dispat
 1404 syslog    20   0  263036    104     20 S   0.0  0.0   0:01.20 rsyslogd
 1447 root      20   0  305224   4080   2748 S   0.0  0.1   0:02.35 polkitd
 1687 root      20   0  195944   2008   2008 S   0.0  0.0   0:00.21 unattended-upgr
 1726 root      20   0 1325464   6264    816 S   0.0  0.1   0:41.49 containerd
 1778 root      20   0  309740   2992   2364 S   0.0  0.0   0:00.22 gdm3
 1792 root      20   0  263108   2120   1624 S   0.0  0.0   0:00.10 gdm-session-wor
 1832 debian-+  20   0  106504  22888   3828 S   0.0  0.3   2:58.66 tor
 1876 gdm       20   0   77156    816    812 S   0.0  0.0   0:00.44 systemd
 1882 gdm       20   0  114136     32      0 S   0.0  0.0   0:00.00 (sd-pam)
 1953 gdm       20   0  199352   1844   1844 S   0.0  0.0   0:00.01 gdm-wayland-ses
 1955 gdm       20   0   50280   1204   1016 S   0.0  0.0   0:00.20 dbus-daemon
 1984 gdm       20   0  560476   2844   2228 S   0.0  0.0   0:00.40 gnome-session-b
 2073 gdm       20   0 3650832  39836  15320 S   0.0  0.5   2:21.56 gnome-shell
 2213 whoopsie  20   0  538012   3108   2684 S   0.0  0.0   0:00.40 whoopsie
 2219 root      20   0  324084   2696   2004 S   0.0  0.0   0:02.69 upowerd
 2232 kernoops  20   0   56940     72      0 S   0.0  0.0   0:04.49 kerneloops
 2234 kernoops  20   0   56940     76      0 S   0.0  0.0   0:04.49 kerneloops
 2308 gdm       20   0  614844   3044   2656 S   0.0  0.0   0:00.50 Xwayland
 2316 gdm       20   0  349236   1784   1784 S   0.0  0.0   0:00.03 at-spi-bus-laun
 2321 gdm       20   0   49924    988    988 S   0.0  0.0   0:00.01 dbus-daemon
 2323 gdm       20   0  220764   1900   1900 S   0.0  0.0   0:00.03 at-spi2-registr
 2327 gdm       20   0 1417216   2212    916 S   0.0  0.0   0:00.46 pulseaudio
 2328 rtkit     21   1  183504    800    800 S   0.0  0.0   0:01.06 rtkit-daemon
 2364 gdm       20   0  363012   1916   1916 S   0.0  0.0   0:00.45 ibus-daemon
 2377 gdm       20   0  282300   1380   1380 S   0.0  0.0   0:00.02 ibus-dconf
 2380 gdm       20   0  489692   4268   3800 S   0.0  0.1   0:00.19 ibus-x11
 2385 gdm       20   0  280112   1496   1496 S   0.0  0.0   0:00.01 ibus-portal
 2399 gdm       20   0  640208   4100   3664 S   0.0  0.1   0:00.29 gsd-xsettings
 2400 root      20   0  450192   2772   2356 S   0.0  0.0   0:15.20 packagekitd
 2401 root      20   0  298424   2176   1972 S   0.0  0.0   0:00.69 boltd
 2469 gdm       20   0  279672   1804   1804 S   0.0  0.0   0:00.02 gsd-a11y-settin
 2470 gdm       20   0  489324   4108   3676 S   0.0  0.1   0:00.27 gsd-clipboard
 2471 gdm       20   0  822896   5860   4048 S   0.0  0.1   0:15.19 gsd-color
 2474 gdm       20   0  395264   2116   2116 S   0.0  0.0   0:00.02 gsd-datetime
 2475 gdm       20   0  285296   1440   1440 S   0.0  0.0   0:00.01 gsd-housekeepin
 2478 gdm       20   0  643652   4556   3644 S   0.0  0.1   0:00.27 gsd-keyboard
 2479 gdm       20   0 1151356   5636   4052 S   0.0  0.1   0:00.57 gsd-media-keys
 2483 gdm       20   0  203552   1052   1052 S   0.0  0.0   0:00.00 gsd-mouse
 2484 gdm       20   0  935580   5240   4008 S   0.0  0.1   0:01.13 gsd-power
 2487 gdm       20   0  268560   1544   1544 S   0.0  0.0   0:00.00 gsd-print-notif
 2488 gdm       20   0  203572   1068   1068 S   0.0  0.0   0:00.00 gsd-rfkill
 2489 gdm       20   0  277288   1092   1092 S   0.0  0.0   0:00.00 gsd-screensaver
 2494 gdm       20   0  306624   1708   1708 S   0.0  0.0   0:00.01 gsd-sharing
 2497 gdm       20   0  379452    816    816 S   0.0  0.0   0:00.02 gsd-smartcard
 2502 gdm       20   0  334376   1760   1760 S   0.0  0.0   0:00.00 gsd-sound
 2505 gdm       20   0  574476   4244   3640 S   0.0  0.1   0:00.26 gsd-wacom
 2525 gdm       20   0  206444   1788   1788 S   0.0  0.0   0:00.15 ibus-engine-sim
 2574 colord    20   0  326568   2712   1960 S   0.0  0.0   0:00.47 colord
 2741 root      20   0  417028   4312   3064 S   0.0  0.1   0:00.46 gdm-session-wor
 2746 hamon     20   0   80556   5604   2896 S   0.0  0.1   0:02.12 systemd
 2747 hamon     20   0  261600     36      0 S   0.0  0.0   0:00.00 (sd-pam)
 2760 hamon     20   0  290020   2612   1780 S   0.0  0.0   0:00.96 gnome-keyring-d
 2764 hamon     20   0  213684   2136   1848 S   0.0  0.0   0:00.04 gdm-x-session
 2780 hamon     20   0   55708   5796   1096 S   0.0  0.1   0:06.79 dbus-daemon
 2783 hamon     20   0  569412   3420   2344 S   0.0  0.0   0:01.63 gnome-session-b
 2866 hamon     20   0   11304     40      0 S   0.0  0.0   0:00.41 ssh-agent
 2869 hamon     20   0  349280   1688   1612 S   0.0  0.0   0:00.07 at-spi-bus-laun
 2874 hamon     20   0   49928   1432   1100 S   0.0  0.0   0:04.09 dbus-daemon
 2876 hamon     20   0  220788   2068   1744 S   0.0  0.0   0:18.95 at-spi2-registr
 2901 hamon     20   0  293628   2296   1780 S   0.0  0.0   0:00.27 gvfsd
 2906 hamon     20   0  416116   1732   1636 S   0.0  0.0   0:00.05 gvfsd-fuse
 2918 hamon      9 -11 2222936   4320   2144 S   0.0  0.1  12:47.65 pulseaudio
 2931 root      10 -10       0      0      0 S   0.0  0.0   0:00.00 krfcommd
 2933 hamon     20   0  437640   4216   2376 S   0.0  0.1   3:14.71 ibus-daemon
 2937 hamon     20   0  282328   2056   1880 S   0.0  0.0   0:00.03 ibus-dconf
 2939 hamon     20   0  345668   4772   3624 S   0.0  0.1   0:01.07 ibus-x11
 2943 hamon     20   0  280244   2032   1568 S   0.0  0.0   0:00.43 ibus-portal
 2953 hamon     20   0  692912   7288   2920 S   0.0  0.1   0:01.24 gnome-shell-cal
 2975 hamon     20   0  308108   2688   1380 S   0.0  0.0   0:05.65 gvfs-udisks2-vo
 2976 hamon     20   0 1319232   3948   2508 S   0.0  0.0   0:00.99 evolution-sourc
 2983 hamon     20   0  380368   2020   1728 S   0.0  0.0   0:00.10 gvfs-afc-volume
 2988 hamon     20   0  277424   2040   1760 S   0.0  0.0   0:00.11 gvfs-mtp-volume
 2994 hamon     20   0  806660  16892   2816 S   0.0  0.2   0:04.16 goa-daemon
 2995 hamon     20   0  290336   2044   1804 S   0.0  0.0   0:00.13 gvfs-gphoto2-vo
 2999 hamon     20   0  280280   2096   1768 S   0.0  0.0   0:00.12 gvfs-goa-volume
 3001 hamon     20   0  188384   2788   1896 S   0.0  0.0   0:00.95 dconf-service
 3006 hamon     20   0  206948   2620   2112 S   0.0  0.0   0:00.14 gvfsd-metadata
 3018 hamon     20   0  304912   1268   1232 S   0.0  0.0   0:00.20 goa-identity-se
 3023 hamon     20   0  893680   2272   1900 S   0.0  0.0   0:00.57 evolution-calen
 3025 hamon     20   0  800100   6168   3700 S   0.0  0.1   0:02.73 gsd-power
 3027 hamon     20   0  350880   2520   2104 S   0.0  0.0   0:00.27 gsd-print-notif
 3028 hamon     20   0  424900   2024   1700 S   0.0  0.0   0:00.36 gsd-rfkill
 3029 hamon     20   0  277288   1716   1428 S   0.0  0.0   0:00.35 gsd-screensaver
 3034 hamon     20   0  454644   3088   2000 S   0.0  0.0   0:08.55 gsd-sharing
 3038 hamon     20   0  453204   1900   1700 S   0.0  0.0   0:00.25 gsd-smartcard
 3042 hamon     20   0  334404   1924   1692 S   0.0  0.0   0:00.24 gsd-sound
 3048 hamon     20   0  496260   5248   3444 S   0.0  0.1   0:01.76 gsd-xsettings
 3051 hamon     20   0  430184   5412   3432 S   0.0  0.1   0:01.42 gsd-wacom
 3064 hamon     20   0  279700   2084   1844 S   0.0  0.0   0:00.22 gsd-a11y-settin
 3065 hamon     20   0  345284   4724   3512 S   0.0  0.1   0:02.24 gsd-clipboard
 3066 hamon     20   0  471280   2600   2228 S   0.0  0.0   0:00.25 gsd-datetime
 3069 hamon     20   0  366244   2320   1768 S   0.0  0.0   0:10.21 gsd-housekeepin
 3070 hamon     20   0 1014980   7320   4264 S   0.0  0.1   0:16.58 gsd-color
 3073 hamon     20   0 1542340   7564   5132 S   0.0  0.1   0:02.90 gsd-media-keys
 3076 hamon     20   0  279704   2140   1848 S   0.0  0.0   0:00.23 gsd-mouse
 3080 hamon     20   0  508208   4996   3464 S   0.0  0.1   0:01.44 gsd-keyboard
 3112 hamon     20   0  510316   2468   2024 S   0.0  0.0   0:00.10 gsd-printer
 3172 hamon     20   0  271936   2288   1580 S   0.0  0.0   0:00.08 gsd-disk-utilit
 3197 hamon     20   0  206580   2664   2092 S   0.0  0.0   0:49.43 ibus-engine-sim
 3208 hamon     20   0 2060192   5372   2820 S   0.0  0.1   0:02.13 evolution-calen
 3227 hamon     20   0  734352   2292   1884 S   0.0  0.0   0:00.19 evolution-addre
 3247 hamon     20   0 1018728   2596   1920 S   0.0  0.0   0:00.37 evolution-addre
 3823 hamon     20   0  649192  10248   7276 S   0.0  0.1   0:03.78 update-notifier
 3838 hamon     20   0 1314160   8084   4284 S   0.0  0.1   0:10.48 gnome-software
 3930 root      20   0  557604   2788   2228 S   0.0  0.0   0:03.83 fwupd
 4289 hamon     20   0 1277840  51592  26256 S   0.0  0.6  21:06.77 code
 4291 hamon     20   0  377564   4316   2788 S   0.0  0.1   0:00.06 code
 4317 hamon     20   0  562004  49500  42764 S   0.0  0.6  19:07.17 code
 4332 hamon     20   0 1249004 221072  45940 S   0.0  2.7  61:12.80 code
 4346 hamon     20   0  759812  28788  14384 S   0.0  0.4   0:36.18 code
 4376 hamon     20   0   56732   3196   2132 S   0.0  0.0   0:01.78 zsh
 4382 hamon     20   0  961308 114624  11872 S   0.0  1.4   3:45.73 code
 4423 hamon     20   0  609800   5864   4536 S   0.0  0.1   0:08.04 code
 4752 root      20   0   26116    784    780 S   0.0  0.0   0:00.02 dhclient
 5283 hamon     20   0  233596   5192   1572 S   0.0  0.1   2:27.19 python
 5287 hamon     20   0  102060   2052   1592 S   0.0  0.0   0:46.31 python
 5988 root      20   0    4508      0      0 S   0.0  0.0   0:00.02 none
 7190 hamon     20   0  361188   1640   1500 S   0.0  0.0   0:00.10 gvfsd-http
 7665 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kworker/u9:2-hc
 8295 hamon     20   0  369924   2640   1960 S   0.0  0.0   0:00.94 gvfsd-trash
 9201 hamon     20   0  593928   6212   4120 S   0.0  0.1   0:05.42 code
 9586 root      20   0  638036   5468   2956 S   0.0  0.1   0:21.02 NetworkManager
11614 hamon     20   0  371928   2320   1896 S   0.0  0.0   0:00.17 gvfsd-network
11645 hamon     20   0  382848   2220   1916 S   0.0  0.0   0:00.16 gvfsd-dnssd
11723 hamon     20   0   16268      0      0 S   0.0  0.0   0:00.00 cat
11724 hamon     20   0   16268      0      0 S   0.0  0.0   0:00.00 cat
11736 hamon     20   0  446188   5572   4620 S   0.0  0.1   0:00.47 chrome
11740 hamon     20   0   27356    868    864 S   0.0  0.0   0:00.01 nacl_helper
11743 hamon     20   0  446188   4116   3016 S   0.0  0.1   0:00.08 chrome
11766 hamon     20   0  541848  35848  20304 S   0.0  0.4   0:43.68 chrome
11853 hamon     20   0  798576  71804  30680 S   0.0  0.9  16:16.41 chrome
11965 hamon     20   0  771176  55792  31128 S   0.0  0.7   0:11.19 chrome
11977 hamon     20   0  631548   8860   6284 S   0.0  0.1   0:05.82 chrome
11989 hamon     20   0  738060  55388  29328 S   0.0  0.7   1:26.75 chrome
12055 hamon     20   0  755360 108464  71072 S   0.0  1.3   0:04.58 chrome
14635 root     -51   0       0      0      0 S   0.0  0.0   0:00.00 irq/125-mei_me
16095 root      20   0  109240   1500   1164 S   0.0  0.0   0:00.06 cupsd
16096 root      20   0  303656   1420   1420 S   0.0  0.0   0:00.10 cups-browsed
16628 hamon     20   0  311996  41280   3008 T   0.0  0.5   0:11.41 python
16643 hamon     20   0  388616  45680   3208 T   0.0  0.6   6:50.03 python
18222 root      20   0       0      0      0 I   0.0  0.0   0:05.49 kworker/u8:2-ev
18255 root      20   0       0      0      0 I   0.0  0.0   0:06.74 kworker/u8:3-ev
18337 root      20   0       0      0      0 I   0.0  0.0   0:01.51 kworker/3:2-eve
18355 root      20   0       0      0      0 I   0.0  0.0   0:03.96 kworker/u8:1-ev
18383 root      20   0       0      0      0 D   0.0  0.0   0:02.86 kworker/u8:4+ev
18420 root      20   0       0      0      0 I   0.0  0.0   0:01.30 kworker/2:2-eve
18432 root      20   0       0      0      0 D   0.0  0.0   0:01.00 kworker/1:1+eve
18575 root      20   0       0      0      0 I   0.0  0.0   0:00.40 kworker/0:1-eve
18663 root      20   0       0      0      0 I   0.0  0.0   0:00.13 kworker/2:0-eve
18686 root      20   0       0      0      0 I   0.0  0.0   0:00.03 kworker/0:2-eve
18705 hamon     20   0  803356  37940  27128 S   0.0  0.5   0:09.85 gnome-terminal-
18715 hamon     20   0   29872   2924   2664 S   0.0  0.0   0:00.01 tmux: client
18717 hamon     20   0   39772   4900   3064 S   0.0  0.1   0:02.44 tmux: server
18718 hamon     20   0   56332   6140   4020 S   0.0  0.1   0:01.00 zsh
18742 root      20   0       0      0      0 I   0.0  0.0   0:00.00 kworker/1:0-eve
18782 root      20   0       0      0      0 I   0.0  0.0   0:00.02 kworker/3:1-eve
18834 root      20   0       0      0      0 I   0.0  0.0   0:00.02 kworker/2:1-eve
18839 root      20   0       0      0      0 I   0.0  0.0   0:00.00 kworker/1:2-eve
18840 root      20   0       0      0      0 I   0.0  0.0   0:00.02 kworker/0:0-eve
18851 root      20   0       0      0      0 D   0.0  0.0   0:00.18 kworker/u8:0+ev
18891 root      20   0       0      0      0 I   0.0  0.0   0:00.01 kworker/3:0-eve
18911 root      20   0       0      0      0 I   0.0  0.0   0:00.00 kworker/3:3
18930 hamon     20   0  732792 104440  70328 S   0.0  1.3   0:01.21 chrome
19367 root      20   0 1316064   9960      0 S   0.0  0.1   0:56.77 dockerd
19780 root      20   0   10744    972    492 S   0.0  0.0   0:05.47 containerd-shim
19784 root      20   0   10744   1068    472 S   0.0  0.0   0:04.77 containerd-shim
19828 999       20   0   40704    732    412 S   0.0  0.0   2:09.26 redis-server
19829 999       20   0 1146372  12648      0 S   0.0  0.2   6:36.86 mongod
20649 uuidd     20   0   36796     52      0 S   0.0  0.0   0:00.00 uuidd
21121 hamon     20   0  654796   9176   7628 S   0.0  0.1   0:03.38 code
31753 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 xfsalloc
31759 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 xfs_mru_cache
31764 root      20   0       0      0      0 S   0.0  0.0   0:00.00 jfsIO
31765 root      20   0       0      0      0 S   0.0  0.0   0:00.00 jfsCommit
31766 root      20   0       0      0      0 S   0.0  0.0   0:00.00 jfsCommit
31767 root      20   0       0      0      0 S   0.0  0.0   0:00.00 jfsCommit
31768 root      20   0       0      0      0 S   0.0  0.0   0:00.00 jfsCommit
31769 root      20   0       0      0      0 S   0.0  0.0   0:00.00 jfsSync

```

It says 7.2GB of my memory is used and only 258MB is available. But if I use the command below to sum up percentage of memory usage of active processes it is only 25%:

```

$ ps -e -o %mem | paste -sd+ | tail -c +7 | bc
25.3

```

I have read linuxatemyram but it doesn't explain my case. As you see in top command output not much of memory is devoted to buffer/cache. Also I cannot gain much free memory by closing apps and clearing cache.

---

