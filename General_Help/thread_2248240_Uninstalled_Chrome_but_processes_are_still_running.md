---
title: "Uninstalled Chrome but processes are still running with ps -A"
date: 2014-10-13
forum: General Help
---

### Post by tom140 on 2014-10-13
Hi all,

I'm confused why there are so many chrome processes still running in the background even when I uninstalled and purged chrome-stable installation. They are appearing in red color; does this mean they are zombie tasks or something? I'm on trusty 14.04 on my HP Chromebook 14 if that helps with debugging. 

I actually had a working chrome installation but sometimes got some sort of profile error message which led me down this path of not having Chrome working at all anymore. It was related to some profile corruption for Chrome so I tried various solutions which didn't help but made things worse. I eventually removed and purged the Chrome app. Could these 'chrome' and 'chrome-sandbox' tasks be running from my Chromium installation? I don't have any extensions installed in Chromium though or even have it running.


here is what I'm seeing:
[IMG]https://s3.amazonaws.com/pushbullet-uploads/ujBgQRxLyDY-s1SmO6idJigTt8DoZROpbQLCFAShoEmd/chrome.png[/IMG]

---

### Post by Impavidus on 2014-10-13
Have you rebooted after uninstalling thoses applications? Uninstalling doesn't really guarantee any running processes are terminated. Killing them can help. Rebooting is a clean way of killing everything without nasty side effects.

---

### Post by tom140 on 2014-10-13
> **Impavidus said:**
> Have you rebooted after uninstalling thoses applications? Uninstalling doesn't really guarantee any running processes are terminated. Killing them can help. Rebooting is a clean way of killing everything without nasty side effects.


Yes I actually tried a restart and a shut down. But once the system came up, i saw those same chrome processes when running ps -A. I've added a screenshot of what I'm using in my first post.

---

### Post by vasa1 on 2014-10-13
> **tom140 said:**
> Yes I actually tried a restart and a shut down. But once the system came up, i saw those same chrome processes when running ps -A. I've added a screenshot of what I'm using in my first post.For future posts, you can paste terminal output (or anything that needs a fixed font) between code tags (available above the text box in which you compose your post).

Re. > Could these 'chrome' and 'chrome-sandbox' tasks be running from my Chromium installation? I don't have any extensions installed in Chromium though or even have it running. why don't you close all running instances of Chromium as well and then see?

Both Chrome and Chromium have the option to keep or stop background processes running after the browser is closed but I think you know about that. If not, open chrome://settings/, click on "Advanced Settings" and look near the bottom of the page.

Top should tell you how many zombies you have but a reboot should have killed them, IIRC.

---

### Post by tom140 on 2014-10-13
> **vasa1 said:**
> For future posts, you can paste terminal output (or anything that needs a fixed font) between code tags (available above the text box in which you compose your post).

Re.  why don't you close all running instances of Chromium as well and then see?

Both Chrome and Chromium have the option to keep or stop background processes running after the browser is closed but I think you know about that. If not, open chrome://settings/, click on "Advanced Settings" and look near the bottom of the page.

Top should tell you how many zombies you have but a reboot should have killed them, IIRC.

Thanks for the tip! Unfortunately though, I already unticked that option to run in the background. I restarted the machine once more and I typed 'top' right away and I slowly saw all those chrome processes come alive by themselves and wasting my CPU. It's driving me nuts now!:mad:

edit: just confirmed there are no zombie processes either from top

---

### Post by vasa1 on 2014-10-13
> **tom140 said:**
> Thanks for the tip! Unfortunately though, I already unticked that option to run in the background. I restarted the machine once more and I typed 'top' right away and I slowly saw all those chrome processes come alive by themselves and wasting my CPU. It's driving me nuts now!:mad:

edit: just confirmed there are no zombie processes either from top
Hi, can you please run **top -bn1 > ~/Desktop/top.txt** and then post the contents of top.txt here (between code tags)?

---

### Post by vasa1 on 2014-10-14
Maybe it has to do with "I'm on trusty 14.04 on my **HP Chromebook 14**"? I don't know anything about Chromebooks. Maybe if you tell people how you installed 14.04 on the Chromebook they may have some pointers?

---

### Post by tom140 on 2014-10-14
This installation was with crouton which is one the more popular installation methods. Below is the output after typing that in.


```
top - 21:52:20 up  1:57,  0 users,  load average: 0.66, 0.61, 0.36Tasks: 271 total,   1 running, 270 sleeping,   0 stopped,   0 zombie
%Cpu(s):  9.1 us,  5.2 sy,  0.2 ni, 82.1 id,  3.3 wa,  0.0 hi,  0.1 si,  0.0 st
KiB Mem:   3986376 total,  1528748 used,  2457628 free,    35496 buffers
KiB Swap:  5839416 total,        0 used,  5839416 free.   726072 cached Mem


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
    1 root      20   0   11704   2160   1284 S   0.0  0.1   0:00.34 init
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ksoftirqd/0
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:+
    6 root      20   0       0      0      0 S   0.0  0.0   0:00.91 kworker/u:0
    7 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
    8 root      rt   0       0      0      0 S   0.0  0.0   0:00.11 migration/0
    9 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh
   10 root      20   0       0      0      0 S   0.0  0.0   0:00.48 rcu_sched
   11 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 watchdog/0
   12 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdog/1
   13 root      20   0       0      0      0 S   0.0  0.0   0:00.01 ksoftirqd/1
   15 root      20   0       0      0      0 S   0.0  0.0   0:00.23 kworker/1:0
   16 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/1:+
   17 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 khelper
   18 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kdevtmpfs
   19 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 netns
   20 root      20   0       0      0      0 S   0.0  0.0   0:00.00 bdi-default
   21 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kblockd
   22 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ata_sff
   23 root      20   0       0      0      0 S   0.0  0.0   0:00.01 khubd
   24 root      20   0       0      0      0 S   0.0  0.0   0:00.28 kworker/1:1
   25 root      20   0       0      0      0 S   0.0  0.0   0:00.00 khungtaskd
   26 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kswapd0
   27 root      20   0       0      0      0 S   0.0  0.0   0:00.00 fsnotify_m+
   28 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ecryptfs-k+
   29 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 crypto
   43 root      20   0       0      0      0 S   0.0  0.0   0:00.24 kworker/0:1
   44 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_0
   45 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_1
   47 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kpsmoused
   48 root      20   0       0      0      0 S   0.0  0.0   0:00.50 kworker/0:2
   49 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 dm_bufio_c+
   50 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 kinteracti+
   51 root     -51   0       0      0      0 S   0.0  0.0   0:00.66 irq/37-cya+
   53 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 deferwq
   54 root      20   0       0      0      0 S   0.0  0.0   0:00.29 kworker/u:4
   55 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kdmflush
   56 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kverityd
   57 root       0 -20       0      0      0 S   0.0  0.0   0:00.16 kworker/0:+
   58 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ext4-dio-u+
   59 root       0 -20       0      0      0 S   0.0  0.0   0:00.01 kworker/1:+
   83 root      20   0   12060   1548    928 S   0.0  0.0   0:00.08 udevd
  121 root      20   0       0      0      0 S   0.0  0.0   0:00.04 jbd2/sda1-8
  124 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ext4-dio-u+
  126 root      20   0       0      0      0 S   0.0  0.0   0:00.00 jbd2/sda8-8
  127 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ext4-dio-u+
  419 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
  468 root       0 -20       0      0      0 S   0.0  0.0   0:00.08 loop0
  513 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kdmflush
  551 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kcryptd_io
  552 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kcryptd
  562 root      20   0       0      0      0 S   0.0  0.0   0:00.01 jbd2/dm-1-8
  566 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ext4-dio-u+
  645 root      20   0       0      0      0 S   0.0  0.0   0:00.02 flush-8:0
  647 root      20   0       0      0      0 S   0.0  0.0   0:00.00 flush-254:1
 1166 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 cfg80211
 1189 202       20   0  242768   1808   1200 S   0.0  0.0   0:00.37 rsyslogd
 1207 201       20   0   11660   1376    688 S   0.0  0.0   0:00.39 dbus-daemon
 1297 root      20   0    7924    820    712 S   0.0  0.0   0:00.00 agetty
 1342 root      rt   0    8536    880    736 S   0.0  0.0   0:00.00 minijail0
 1347 229       rt   0    6400    684    556 S   0.0  0.0   0:00.01 daisydog
 1350 219       20   0   17168   3292   2636 S   0.0  0.1   0:00.18 wpa_suppli+
 1533 root      20   0  114604  11924   4700 S   0.0  0.3   0:00.49 shill
 1537 202       20   0    6412    684    560 S   0.0  0.0   0:00.00 logger
 1574 root      20   0    8536    876    736 S   0.0  0.0   0:00.00 minijail0
 1605 228       20   0  100548   4904   4148 S   0.0  0.1   0:00.23 powerd
 1710 root      20   0   43376   8104   6556 S   0.0  0.2   0:00.03 session_ma+
 1778 231        0 -20   53732  13636   5724 S   0.0  0.3   0:01.81 X
 1823 207       20   0  244040   1188    760 S   0.0  0.0   0:00.03 tcsd
 1827 223       20   0  122364   5912   4892 S   0.0  0.1   0:00.10 chapsd
 1836 root      20   0   26896   3556   3040 S   0.0  0.1   0:00.00 debugd
 1857 root      20   0  109168   5168   3860 S   0.0  0.1   0:00.03 cryptohomed
 1935 sup3rca+  20   0  672876 195340  75540 S   0.0  4.9   0:24.73 chrome
 2003 sup3rca+  20   0    6388    588    492 S   0.0  0.0   0:00.00 chrome-san+
 2005 sup3rca+  20   0  247856  30060  21072 S   0.0  0.8   0:00.03 chrome
 2084 sup3rca+  20   0    6388    596    496 S   0.0  0.0   0:00.00 chrome-san+
 2093 sup3rca+  20   0   35128   3976   2848 S   0.0  0.1   0:00.00 nacl_helper
 2136 sup3rca+  20   0  272444   9564    540 S   0.0  0.2   0:00.03 chrome
 2289 sup3rca+  20   0  408800  86724  42700 S   0.0  2.2   0:04.76 chrome
 2471 sup3rca+  20   0  188968  10236    468 S   0.0  0.3   0:00.00 chrome
 4349 root      20   0   20532    908    536 S   0.0  0.0   0:00.00 lid_touchp+
 4354 root      20   0    8536    872    728 S   0.0  0.0   0:00.00 minijail0
 4362 root      20   0    4320    728    624 S   0.0  0.0   0:00.00 periodic_s+
 4363 230       20   0   28540   3860   3296 S   0.0  0.1   0:00.00 permission+
 4380 root      20   0    8536    892    740 S   0.0  0.0   0:00.00 minijail0
 4388 226       20   0  104220   4960   4188 S   0.0  0.1   0:00.02 mtpd
 4389 root      20   0    4320    724    624 S   0.0  0.0   0:00.00 periodic_s+
 4426 root      20   0    8536    880    736 S   0.0  0.0   0:00.00 minijail0
 4433 root      20   0    8536    884    736 S   0.0  0.0   0:00.00 minijail0
 4448 241       20   0  239064   5020   3912 S   0.0  0.1   0:02.65 ModemManag+
 4450 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 hd-audio0
 4454 218       20   0   12816   2376   1972 S   0.0  0.1   0:00.00 bluetoothd
 4458 220       20   0  165132   2808   2104 S   0.0  0.1   0:00.16 cras
 4502 root      20   0   29264   1768    956 S   0.0  0.0   0:00.03 metrics_da+
 4509 root      20   0  108444   5204   3880 S   0.0  0.1   0:00.04 update_eng+
 4522 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 hd-audio1
 4583 root      20   0  105268   3132   1900 S   0.0  0.1   0:00.04 disks
 4905 root      20   0   23280   2544   2068 S   0.0  0.1   0:00.02 warn_colle+
 4958 root      20   0    4320    660    568 S   0.0  0.0   0:00.00 sh
 4985 root      20   0    8536    888    736 S   0.0  0.0   0:00.00 minijail0
 5009 232       20   0   26288   3216   2744 S   0.0  0.1   0:00.00 netfilter-+
 5036 234       20   0   14816   1840   1460 S   0.0  0.0   0:00.00 tlsdated
 5037 root      20   0    4236    652    552 S   0.0  0.0   0:00.00 logger
 5051 root      20   0   12716    420     76 S   0.0  0.0   0:00.00 tlsdated-s+
 9655 sup3rca+  20   0  625176  53144  21324 S   0.0  1.3   0:01.01 chrome
 9846 sup3rca+  20   0  608536  36220  18380 S   0.0  0.9   0:00.27 chrome
10217 224       20   0   10976   1400   1192 S   0.0  0.0   0:00.00 dhcpcd
10218 sup3rca+  20   0  605384  35476  17088 S   0.0  0.9   0:00.31 chrome
10226 sup3rca+  20   0  606408  36520  17224 S   0.0  0.9   0:00.31 chrome
10234 sup3rca+  20   0  673516  66452  23384 S   0.0  1.7   0:02.76 chrome
10291 sup3rca+  20   0  604104  36656  17036 S   0.0  0.9   0:00.28 chrome
10300 sup3rca+  20   0   36728   5852   2772 S   0.0  0.1   0:00.06 xterm
10306 sup3rca+  20   0    5208   1964   1596 S   0.0  0.0   0:00.00 bash
10365 sup3rca+  20   0    3752    572    512 S   0.0  0.0   0:00.00 sleep
10368 sup3rca+  20   0    4900   1340    948 R   0.0  0.0   0:00.00 top
10381 sup3rca+  20   0  651376  74436  24300 S   0.0  1.9   0:01.70 chrome
10485 sup3rca+  20   0  634080  42136  20392 S   0.0  1.1   0:00.63 chrome
10585 sup3rca+  20   0  612328  39784  17992 S   0.0  1.0   0:00.45 chrome
10623 sup3rca+  20   0  620108  40876  19972 S   0.0  1.0   0:00.56 chrome
10811 sup3rca+  20   0  662952  80576  19012 S   0.0  2.0   0:03.12 chrome
10853 sup3rca+  20   0  618752  38820  19648 S   0.0  1.0   0:00.48 chrome
10901 sup3rca+  20   0  616984  46696  20432 S   0.0  1.2   0:00.96 chrome
13634 sup3rca+  20   0  661140  53888  30660 S   0.0  1.4   0:10.45 chrome
14193 sup3rca+  20   0    9672   2480   1660 S   0.0  0.1   0:00.03 bash
14845 sup3rca+  20   0    9672   1268    444 S   0.0  0.0   0:00.00 bash
14848 sup3rca+  20   0   11360   2200   1744 S   0.0  0.1   0:00.00 bash
24974 root      20   0   15104   1696   1332 S   0.0  0.0   0:00.00 sudo
24979 root      20   0    4320    800    648 S   0.0  0.0   0:00.02 sh
25133 root      20   0       0      0      0 S   0.0  0.0   0:00.00 flush-253:0
25134 root      20   0       0      0      0 S   0.0  0.0   0:00.01 flush-ecry+
25197 message+  20   0    4576   1616   1000 S   0.0  0.0   0:00.14 dbus-daemon
25235 root      20   0    4220   1716   1416 S   0.0  0.0   0:00.02 systemd-lo+
25277 root      20   0    4312   1736   1360 S   0.0  0.0   0:00.01 su
25286 sup3rca+  20   0    3608    868    708 S   0.0  0.0   0:00.00 xinit
25292 root      20   0   82100  28164  19008 S   0.0  0.7   0:03.80 Xorg
25301 sup3rca+  20   0    2272    624    552 S   0.0  0.0   0:00.00 croutonxin+
25304 sup3rca+  20   0    2272    680    596 S   0.0  0.0   0:00.00 croutonpow+
25305 sup3rca+  20   0    2272    644    560 S   0.0  0.0   0:00.00 croutonclip
25310 sup3rca+  20   0    2272    376    276 S   0.0  0.0   0:00.00 croutonclip
25311 sup3rca+  20   0    2272    320    228 S   0.0  0.0   0:00.00 croutonclip
25312 sup3rca+  20   0    2040    372    308 S   0.0  0.0   0:00.00 croutonweb+
25320 sup3rca+  20   0   10064   3656   1744 S   0.0  0.1   0:00.03 xbindkeys
25322 sup3rca+  20   0    2272    336    260 S   0.0  0.0   0:00.00 croutonxin+
25325 sup3rca+  20   0   10064   4812   2900 S   0.0  0.1   0:00.01 xbindkeys
25341 sup3rca+  20   0   70216   9696   7244 S   0.0  0.2   0:00.30 gnome-sess+
25386 sup3rca+  20   0    4216    368    160 S   0.0  0.0   0:00.00 ssh-agent
25389 sup3rca+  20   0    3856    740    500 S   0.0  0.0   0:00.00 dbus-launch
25390 sup3rca+  20   0    4712   1636    832 S   0.0  0.0   0:00.52 dbus-daemon
25401 sup3rca+  20   0   45540   3768   2876 S   0.0  0.1   0:00.26 ibus-daemon
25413 sup3rca+  20   0   27276   2844   2420 S   0.0  0.1   0:00.03 gvfsd
25418 sup3rca+  20   0   36788   3392   2824 S   0.0  0.1   0:00.01 ibus-dconf
25419 sup3rca+  20   0   66172  13100   9844 S   0.0  0.3   0:00.21 ibus-ui-gt+
25421 sup3rca+  20   0   49784   6980   5560 S   0.0  0.2   0:00.13 ibus-x11
25430 sup3rca+  20   0   43468   3300   2836 S   0.0  0.1   0:00.00 at-spi-bus+
25436 sup3rca+  20   0    4372   1752   1376 S   0.0  0.0   0:00.02 dbus-daemon
25439 sup3rca+  20   0   17368   3248   2784 S   0.0  0.1   0:00.02 at-spi2-re+
25460 sup3rca+  20   0   54784   3544   2988 S   0.0  0.1   0:00.03 gnome-keyr+
25463 sup3rca+  20   0  219908  14696  10480 S   0.0  0.4   0:00.42 unity-sett+
25479 sup3rca+  20   0   75336  14420  10596 S   0.0  0.4   0:00.65 unity-pane+
25483 sup3rca+  20   0   38984   3964   3568 S   0.0  0.1   0:00.02 window-sta+
25488 sup3rca+  20   0  125012   4788   3572 S   0.0  0.1   0:00.13 pulseaudio
25494 rtkit     21   1   21368   1288   1076 S   0.0  0.0   0:00.00 rtkit-daem+
25503 root      20   0   35732   4376   3048 S   0.0  0.1   0:00.15 polkitd
25514 root      20   0   39024   4424   3456 S   0.0  0.1   0:00.31 upowerd
25517 sup3rca+  20   0   38412   4504   3632 S   0.0  0.1   0:00.04 indicator-+
25519 sup3rca+  20   0   71040  10880   7580 S   0.0  0.3   0:00.37 bamfdaemon
25528 sup3rca+  20   0   35720   2988   2536 S   0.0  0.1   0:00.01 indicator-+
25539 sup3rca+  20   0   27480   3308   2768 S   0.0  0.1   0:00.07 ibus-engin+
25556 sup3rca+  20   0  100552   8368   6068 S   0.0  0.2   0:00.10 indicator-+
25570 sup3rca+  20   0   43804   2920   2492 S   0.0  0.1   0:00.00 indicator-+
25588 sup3rca+  20   0   44552   3324   2760 S   0.0  0.1   0:00.09 indicator-+
25594 sup3rca+  20   0   63980   9852   7300 S   0.0  0.2   0:00.10 indicator-+
25608 sup3rca+  20   0   61520   3632   2972 S   0.0  0.1   0:00.03 indicator-+
25617 sup3rca+  20   0   63960   8772   6736 S   0.0  0.2   0:00.07 evolution-+
25619 sup3rca+  20   0  124480   5068   4036 S   0.0  0.1   0:00.05 indicator-+
25635 root      20   0   36416   3764   3088 S   0.0  0.1   0:00.04 accounts-d+
25664 sup3rca+  20   0   91780  10712   7296 S   0.0  0.3   0:00.18 indicator-+
25717 sup3rca+  20   0  222804  59372  27716 S   0.0  1.5   0:04.51 compiz
25719 colord    20   0   37332   5156   4132 S   0.0  0.1   0:00.15 colord
25721 sup3rca+  20   0   24512   2680   2108 S   0.0  0.1   0:00.06 dconf-serv+
25730 sup3rca+  20   0    3748   1004    824 S   0.0  0.0   0:00.28 syndaemon
25736 sup3rca+  20   0  119188  30932   6648 S   0.0  0.8   0:00.20 evolution-+
25760 sup3rca+  20   0   42308   8284   6312 S   0.0  0.2   0:00.07 polkit-gno+
25773 sup3rca+  20   0   51532   8312   6308 S   0.0  0.2   0:00.08 unity-fall+
25775 sup3rca+  20   0  129524  23700  16128 S   0.0  0.6   0:02.24 nautilus
25868 sup3rca+  20   0   38220   4508   3300 S   0.0  0.1   0:00.04 gvfs-udisk+
25878 root      20   0   52532   4672   3416 S   0.0  0.1   0:00.13 udisksd
25887 sup3rca+  20   0   26716   2860   2392 S   0.0  0.1   0:00.01 gvfs-mtp-v+
25891 sup3rca+  20   0   27960   3056   2480 S   0.0  0.1   0:00.00 gvfs-gphot+
25901 sup3rca+  20   0   38892   3036   2488 S   0.0  0.1   0:00.00 gvfs-afc-v+
25908 sup3rca+  20   0   70664   4184   3252 S   0.0  0.1   0:00.07 gvfsd-trash
25918 sup3rca+  20   0   17544   2616   2212 S   0.0  0.1   0:00.00 gvfsd-meta+
25930 sup3rca+  20   0    2272    600    532 S   0.0  0.0   0:00.00 dbus-activ+
25931 sup3rca+  20   0  121732  18948  15184 S   0.0  0.5   0:00.35 hud-service
26202 sup3rca+  20   0    2032    356    296 S   0.0  0.0   0:00.00 croutonvtm+
26435 sup3rca+  20   0   82660  10232   8016 S   0.0  0.3   0:00.07 telepathy-+
26495 sup3rca+  20   0   68448   6336   4988 S   0.0  0.2   0:00.04 zeitgeist-+
26500 sup3rca+  20   0   44488   4396   3604 S   0.0  0.1   0:00.08 zeitgeist-+
26506 sup3rca+  20   0   58300   8596   6900 S   0.0  0.2   0:00.09 zeitgeist-+
26515 sup3rca+  20   0    3772    548    484 S   0.0  0.0   0:00.00 cat
26599 sup3rca+  20   0   60900   9740   7524 S   0.0  0.2   0:00.09 update-not+
26959 root      20   0    9520    812    656 S   0.0  0.0   0:00.00 timeout
26960 root      20   0    4320    756    592 S   0.0  0.0   0:00.00 crash_send+
26962 root      20   0    4320    472    300 S   0.0  0.0   0:00.00 crash_send+
27000 root      20   0    9388    764    612 S   0.0  0.0   0:00.00 sleep
27004 root      20   0    9388    760    612 S   0.0  0.0   0:00.00 sleep
27036 root      20   0       0      0      0 S   0.0  0.0   0:00.17 kworker/1:2
27054 root      20   0    3088   1012    876 S   0.0  0.0   0:00.00 systemd-ho+
27082 root      20   0       0      0      0 S   0.0  0.0   0:00.01 kworker/0:0
27136 root      20   0       0      0      0 S   0.0  0.0   0:00.02 kworker/u:1
27237 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:2
27238 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:3
27239 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:5
27240 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:6
27241 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:7
27242 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:8
27243 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:9
27244 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27245 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27246 root      20   0       0      0      0 S   0.0  0.0   0:00.01 kworker/u:+
27247 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27248 root      20   0       0      0      0 S   0.0  0.0   0:00.01 kworker/u:+
27250 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27251 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27252 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27253 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27254 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27255 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27256 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27257 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27258 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27259 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27260 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27261 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27262 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27263 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27264 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27265 root      20   0       0      0      0 S   0.0  0.0   0:00.01 kworker/u:+
27266 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27267 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27268 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27269 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27270 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27271 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27272 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27273 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27274 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27275 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27276 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27277 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27278 root      20   0       0      0      0 S   0.0  0.0   0:00.04 kworker/u:+
27279 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27280 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27281 root      20   0       0      0      0 S   0.0  0.0   0:00.15 kworker/u:+
27282 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27283 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27284 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27285 root      20   0       0      0      0 S   0.0  0.0   0:00.01 kworker/u:+
27286 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27287 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27288 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
27289 root      20   0       0      0      0 S   0.0  0.0   0:00.06 kworker/0:3
27290 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/0:4
27291 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/0:5
27542 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/1:3
27555 root      20   0       0      0      0 S   0.0  0.0   0:00.05 kworker/1:4
28108 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/u:+
28109 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 migration/1
29008 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 hci0
29009 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 hci0



```

---

### Post by vasa1 on 2014-10-14
What do you see with the commands below?
```
11:38 AM ~ $ which google-chrome
/usr/bin/google-chrome
11:38 AM ~ $ which chromium-browser
11:38 AM ~ $ 
```Anyone else can help here?

---

### Post by mc4man on 2014-10-14
from github, may explain, may not..
> Like virtualization, chroots provide the guest OS with their own, segregated file system to run in, allowing applications to run in a different binary environment from the host OS. Unlike virtualization, you are not booting a second OS; instead, the guest OS is running using the Chromium OS system. The benefit to this is that there is zero speed penalty since everything is run natively, and you aren't wasting RAM to boot two OSes at the same time. The downside is that you must be running the correct chroot for your hardware, the software must be compatible with Chromium OS's kernel, and machine resources are inextricably tied between the host Chromium OS and the guest OS.

---

### Post by vasa1 on 2014-10-14
> **mc4man said:**
> from github, may explain, may not..Seems to be the answer :)

So the user "sup3rca+" is because of the chroot and OP will just have to live with that?

Link: [https://github.com/dnschneid/crouton](https://github.com/dnschneid/crouton)

And this probably doesn't belong here but [http://www.groklaw.net/articlebasic.php?story=20130707160346164](http://www.groklaw.net/articlebasic.php?story=20130707160346164) is an ordinary person's experience. BTW, I've saved that article because it may disappear. (PJ is far from ordinary in other matters.)

---

### Post by tom140 on 2014-10-14
> **vasa1 said:**
> What do you see with the commands below?
```
11:38 AM ~ $ which google-chrome
/usr/bin/google-chrome
11:38 AM ~ $ which chromium-browser
11:38 AM ~ $ 
```Anyone else can help here?


I get no response when I type 'which google-chrome' but when I type 'which chromium-browser' i get back a response /usr/bin/chromium-browser. I'm guessing this means the Chrome folder is deleted already when I uninstalled and purged.

---

### Post by vasa1 on 2014-10-14
I think you should mark this thread "solved"; see [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") for how to do so. mc4man's answer explains why you see what you see.

---

### Post by tom140 on 2014-10-14
> **vasa1 said:**
> I think you should mark this thread "solved"; see [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") for how to do so. mc4man's answer explains why you see what you see.

Oops must have overlooked his response. Why is it that when I re-install Chrome though, it doesn't start? I think it's something else related to the original chrome-stable browser I installed... :mad:

---

### Post by vasa1 on 2014-10-15
> **tom140 said:**
> Oops must have overlooked his response. Why is it that when I re-install Chrome though, it doesn't start? I think it's something else related to the original chrome-stable browser I installed... :mad:
Your original question has been asked and satisfactorily answered, in my opinion. Marking a thread "solved" is the way we show our appreciation to those who help us voluntarily.

---

