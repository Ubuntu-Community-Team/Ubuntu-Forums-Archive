---
title: "Duplicate processes in Ubuntu 12.04"
date: 2012-10-26
forum: General Help
---

### Post by lguigui58 on 2012-10-26
Hi all,

I am running Ubuntu 12.04 LTS just freshly installed. I found out that I had plenty of duplicate processes. Usually they are repeated 5 times. I attached a print screen (see attachement) in order to illustrate the problem but also the result of *ps aux* command.

I would like to avoid to re-install everything so if anybody have a suggestion, I would really appreciate.

```
root         1  0.1  0.0  24428  2400 ?        Ss   10:49   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    10:49   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    10:49   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    10:49   0:00 [kworker/0:0]
root         6  0.0  0.0      0     0 ?        S    10:49   0:00 [migration/0]
root         7  0.0  0.0      0     0 ?        S    10:49   0:00 [watchdog/0]
root         8  0.0  0.0      0     0 ?        S    10:49   0:00 [migration/1]
root         9  0.0  0.0      0     0 ?        R    10:49   0:00 [kworker/1:0]
root        10  0.0  0.0      0     0 ?        S    10:49   0:00 [ksoftirqd/1]
root        11  0.0  0.0      0     0 ?        S    10:49   0:00 [kworker/0:1]
root        12  0.0  0.0      0     0 ?        S    10:49   0:00 [watchdog/1]
root        13  0.0  0.0      0     0 ?        S<   10:49   0:00 [cpuset]
root        14  0.0  0.0      0     0 ?        S<   10:49   0:00 [khelper]
root        15  0.0  0.0      0     0 ?        S    10:49   0:00 [kdevtmpfs]
root        16  0.0  0.0      0     0 ?        S<   10:49   0:00 [netns]
root        18  0.0  0.0      0     0 ?        S    10:49   0:00 [sync_supers]
root        19  0.0  0.0      0     0 ?        S    10:49   0:00 [bdi-default]
root        20  0.0  0.0      0     0 ?        S<   10:49   0:00 [kintegrityd]
root        21  0.0  0.0      0     0 ?        S<   10:49   0:00 [kblockd]
root        22  0.0  0.0      0     0 ?        S<   10:49   0:00 [ata_sff]
root        23  0.0  0.0      0     0 ?        S    10:49   0:00 [khubd]
root        24  0.0  0.0      0     0 ?        S<   10:49   0:00 [md]
root        25  0.0  0.0      0     0 ?        S    10:49   0:00 [kworker/1:1]
root        26  0.0  0.0      0     0 ?        S    10:49   0:00 [khungtaskd]
root        27  0.0  0.0      0     0 ?        S    10:49   0:00 [kswapd0]
root        28  0.0  0.0      0     0 ?        SN   10:49   0:00 [ksmd]
root        29  0.0  0.0      0     0 ?        SN   10:49   0:00 [khugepaged]
root        30  0.0  0.0      0     0 ?        S    10:49   0:00 [fsnotify_mark]
root        31  0.0  0.0      0     0 ?        S    10:49   0:00 [ecryptfs-kthr]
root        32  0.0  0.0      0     0 ?        S<   10:49   0:00 [crypto]
root        40  0.0  0.0      0     0 ?        S<   10:49   0:00 [kthrotld]
root        41  0.0  0.0      0     0 ?        S    10:49   0:00 [scsi_eh_0]
root        42  0.0  0.0      0     0 ?        S    10:49   0:00 [scsi_eh_1]
root        44  0.0  0.0      0     0 ?        S    10:49   0:00 [scsi_eh_2]
root        45  0.0  0.0      0     0 ?        S    10:49   0:00 [scsi_eh_3]
root        46  0.0  0.0      0     0 ?        S    10:49   0:00 [kworker/u:3]
root        47  0.0  0.0      0     0 ?        S    10:49   0:00 [kworker/u:4]
root        67  0.0  0.0      0     0 ?        S<   10:49   0:00 [devfreq_wq]
root       176  0.0  0.0      0     0 ?        S    10:49   0:00 [scsi_eh_4]
root       197  0.0  0.0      0     0 ?        S    10:49   0:00 [scsi_eh_5]
root       238  0.0  0.0      0     0 ?        S    10:49   0:00 [jbd2/sda1-8]
root       239  0.0  0.0      0     0 ?        S<   10:49   0:00 [ext4-dio-unwr]
root       245  0.0  0.0      0     0 ?        S<   10:49   0:00 [firewire]
root       324  0.0  0.0  17364   640 ?        S    10:49   0:00 upstart-udev-br
root       327  0.0  0.0  21984  1820 ?        Ss   10:49   0:00 /sbin/udevd --d
root       553  0.0  0.0      0     0 ?        S<   10:49   0:00 [hci0]
root       568  0.0  0.0      0     0 ?        S<   10:49   0:00 [cfg80211]
root       644  0.0  0.0      0     0 ?        S<   10:49   0:00 [kpsmoused]
root       727  0.0  0.0  15188   396 ?        S    10:49   0:00 upstart-socket-
root       741  0.0  0.0      0     0 ?        S<   10:49   0:00 [hd-audio0]
103        782  0.2  0.1  27544  4160 ?        Ss   10:49   0:00 dbus-daemon --s
root       804  0.0  0.0  79044  3168 ?        Ss   10:49   0:00 /usr/sbin/modem
root       805  0.0  0.0  21316  2096 ?        Ss   10:49   0:00 /usr/sbin/bluet
root       814  0.0  0.1 233584  5540 ?        Ssl  10:49   0:00 NetworkManager
root       818  0.1  0.1 195620  4216 ?        Sl   10:49   0:00 /usr/lib/policy
syslog     823  0.0  0.0 249472  1432 ?        Sl   10:49   0:00 rsyslogd -c5
avahi      825  0.0  0.0  32300  1708 ?        S    10:49   0:00 avahi-daemon: r
avahi      827  0.0  0.0  32180   472 ?        S    10:49   0:00 avahi-daemon: c
root       828  0.0  0.0      0     0 ?        S<   10:49   0:00 [krfcommd]
root       896  0.0  0.1 104244  4204 ?        Ss   10:49   0:00 /usr/sbin/cupsd
lp         926  0.0  0.0  52144  1700 ?        S    10:49   0:00 /usr/lib/cups/n
lp         927  0.0  0.0  52144  1700 ?        S    10:49   0:00 /usr/lib/cups/n
lp         928  0.0  0.0  52144  1700 ?        S    10:49   0:00 /usr/lib/cups/n
lp         929  0.0  0.0  52144  1700 ?        S    10:49   0:00 /usr/lib/cups/n
lp         930  0.0  0.0  52144  1696 ?        S    10:49   0:00 /usr/lib/cups/n
root       934  0.0  0.0  31708  2332 ?        Ss   10:49   0:00 /sbin/wpa_suppl
root       935  0.0  0.0   7264  1540 ?        S    10:49   0:00 /sbin/dhclient
root       977  0.0  0.0  15796   972 tty4     Ss+  10:49   0:00 /sbin/getty -8
root       981  0.0  0.0  15796   972 tty5     Ss+  10:49   0:00 /sbin/getty -8
root       995  0.0  0.0  15796   972 tty2     Ss+  10:49   0:00 /sbin/getty -8
root       999  0.0  0.0  15796   964 tty3     Ss+  10:49   0:00 /sbin/getty -8
root      1003  0.0  0.0  15796   980 tty6     Ss+  10:49   0:00 /sbin/getty -8
root      1025  0.0  0.0  23352  1380 ?        Ss   10:49   0:00 /usr/sbin/vsftp
whoopsie  1028  0.0  0.1 204396  5248 ?        Ssl  10:49   0:00 whoopsie
root      1030  0.0  0.0   4460   816 ?        Ss   10:49   0:00 acpid -c /etc/a
root      1032  0.0  0.0 103652  2728 ?        Ss   10:49   0:00 /usr/sbin/winbi
root      1036  0.0  0.0  15980   680 ?        Ss   10:49   0:00 /usr/sbin/irqba
root      1044  0.0  0.0  19112  1008 ?        Ss   10:49   0:00 cron
daemon    1045  0.0  0.0  16908   376 ?        Ss   10:49   0:00 atd
root      1047  0.0  0.0 270664  3488 ?        Ssl  10:49   0:00 lightdm
root      1092  8.6  2.1 977468 87604 tty7     Ss+  10:49   0:29 /usr/bin/X :0 -
root      1124  0.0  0.0 103652  1768 ?        S    10:49   0:00 /usr/sbin/winbi
root      1248  0.0  0.0  15796   972 tty1     Ss+  10:49   0:00 /sbin/getty -8
root      1327  0.0  0.0 121532  3744 ?        Sl   10:49   0:00 /usr/lib/accoun
root      1344  0.0  0.0 1043060 3824 ?        Sl   10:49   0:00 /usr/sbin/conso
root      1463  0.0  0.1 219876  4288 ?        Sl   10:49   0:00 /usr/lib/upower
colord    1612  0.0  0.2 491748 11720 ?        Sl   10:49   0:00 /usr/lib/x86_64
root      1626  0.0  0.0 163220  3684 ?        Sl   10:49   0:00 lightdm --sessi
root      1642  0.0  0.0   7264  1548 ?        S    10:49   0:00 /sbin/dhclient
root      1663  0.0  0.0      0     0 ?        S    10:49   0:00 [flush-8:0]
rtkit     1667  0.0  0.0 168872  1316 ?        SNl  10:49   0:00 /usr/lib/rtkit/
nobody    1682  0.0  0.0  28832  1292 ?        S    10:49   0:00 /usr/sbin/dnsma
root      1727  0.1  0.0      0     0 ?        S<   10:49   0:00 [khidpd_05ac03]
root      1730  0.0  0.0  21980  1408 ?        S    10:49   0:00 /sbin/udevd --d
root      1732  0.0  0.0      0     0 ?        S<   10:49   0:00 [khidpd_05ac02]
root      1735  0.0  0.0  21980  1304 ?        S    10:49   0:00 /sbin/udevd --d
lemaitre  1769  0.0  0.0 371720  3768 ?        Sl   10:49   0:00 /usr/bin/gnome-
lemaitre  1780  0.0  0.2 391156 10436 ?        Ssl  10:49   0:00 gnome-session -
lemaitre  1817  0.0  0.0  12492   316 ?        Ss   10:49   0:00 /usr/bin/ssh-ag
lemaitre  1820  0.0  0.0  26556   788 ?        S    10:49   0:00 /usr/bin/dbus-l
lemaitre  1821  0.2  0.0  26556  2384 ?        Ss   10:49   0:00 //bin/dbus-daem
lemaitre  1825  0.0  0.0  48192  2456 ?        S    10:49   0:00 /usr/lib/gvfs/g
lemaitre  1827  0.0  0.0 273444  2824 ?        Sl   10:49   0:00 /usr/lib/gvfs//
lemaitre  1842  0.1  0.9 936972 38068 ?        Sl   10:49   0:00 /usr/lib/gnome-
lemaitre  1852  0.0  0.1 365432  4676 ?        Sl   10:49   0:00 /usr/lib/gnome-
lemaitre  1856  1.7  0.9 319288 38980 ?        Sl   10:49   0:05 compiz
lemaitre  1859  0.1  0.1  54572  4436 ?        S    10:49   0:00 /usr/lib/x86_64
lemaitre  1867  0.0  0.1  45636  5344 ?        S    10:49   0:00 /usr/lib/gvfs/g
lemaitre  1871  0.0  0.1 362976  5968 ?        S<l  10:49   0:00 /usr/bin/pulsea
lemaitre  1874  0.0  0.0  95956  2976 ?        S    10:49   0:00 /usr/lib/pulsea
lemaitre  1882  0.0  0.4 645828 17128 ?        Sl   10:50   0:00 nm-applet
lemaitre  1883  0.2  0.9 851660 39488 ?        Sl   10:50   0:00 nautilus -n
lemaitre  1884  0.0  0.2 303416  8572 ?        Sl   10:50   0:00 /usr/lib/policy
lemaitre  1887  0.0  0.3 495772 12532 ?        Sl   10:50   0:00 bluetooth-apple
lemaitre  1894  0.0  0.2 450944  8824 ?        Sl   10:50   0:00 /usr/lib/gnome-
lemaitre  1896  0.0  0.0  12316  1392 ?        S    10:50   0:00 /bin/bash /usr/
lemaitre  1898  0.6  1.6 945516 68108 ?        Sl   10:50   0:01 cairo-dock
lemaitre  1899  4.0  4.9 776504 198956 ?       Sl   10:50   0:12 ./insync
lemaitre  1901  0.0  0.0  54036  3444 ?        S    10:50   0:00 /usr/bin/vncser
lemaitre  1903  0.6  0.2 479156 11676 ?        Sl   10:50   0:01 indicator-multi
root      1904  0.0  0.0  16312   368 ?        S    10:50   0:00 vncserver-x11 -
lemaitre  1908  0.1  0.7 551608 30596 ?        Sl   10:50   0:00 guake -OO /usr/
lemaitre  1913  0.0  0.1 120872  7396 ?        S    10:50   0:00 /usr/bin/vncser
lemaitre  1916  0.0  0.2 479580 10768 ?        Sl   10:50   0:00 /usr/bin/vncser
lemaitre  1941  0.0  0.0  66112  3664 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  1942  0.5  0.5  56340 23080 ?        S    10:50   0:01 /usr/bin/Xvnc-c
root      1943  0.0  0.0  16312   356 ?        S    10:50   0:00 /usr/bin/Xvnc :
root      1945  0.0  0.0 193372  3856 ?        Sl   10:50   0:00 /usr/lib/udisks
root      1947  0.0  0.0  45520   808 ?        S    10:50   0:00 udisks-daemon: 
lemaitre  1948  0.0  0.1 120376  6944 ?        S    10:50   0:00 /usr/bin/vncser
lemaitre  1988  0.0  0.2 470768 10236 ?        Sl   10:50   0:00 /usr/bin/vncser
lemaitre  1993  0.0  0.0  26556   536 ?        S    10:50   0:00 dbus-launch --a
lemaitre  1994  0.0  0.0  23816   692 ?        Ss   10:50   0:00 //bin/dbus-daem
lemaitre  1996  0.0  0.0  56148  2492 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  2003  0.0  0.0 137888  2512 ?        Sl   10:50   0:00 /usr/lib/gvfs/g
lemaitre  2033  0.0  0.2  80492 10268 ?        S    10:50   0:00 /usr/bin/python
lemaitre  2037  0.0  0.0  52688  3228 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  2044  0.0  0.0  48352  2616 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  2049  0.0  0.0  54808  3232 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  2050  0.0  0.0   4400   608 ?        S    10:50   0:00 /bin/sh /etc/vn
lemaitre  2060  0.0  0.2 391192 10360 ?        Sl   10:50   0:00 /usr/bin/gnome-
lemaitre  2086  0.0  0.0  26556   536 ?        S    10:50   0:00 /usr/bin/dbus-l
lemaitre  2087  0.3  0.0  27388  3100 ?        Ss   10:50   0:01 //bin/dbus-daem
lemaitre  2091  0.0  0.0  48192  2452 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  2099  0.0  0.0 371712  3500 ?        Sl   10:50   0:00 /usr/bin/gnome-
lemaitre  2105  0.1  0.6 711948 27076 ?        Sl   10:50   0:00 /usr/lib/gnome-
lemaitre  2112  0.0  0.3 413108 12548 ?        Sl   10:50   0:00 metacity
lemaitre  2116  0.0  0.0  53948  3804 ?        S    10:50   0:00 /usr/lib/x86_64
lemaitre  2118  0.2  0.9 631484 37264 ?        Sl   10:50   0:00 unity-2d-panel
lemaitre  2119  0.4  1.9 1261844 77804 ?       Sl   10:50   0:01 unity-2d-shell
lemaitre  2122  0.0  0.0      0     0 ?        Z    10:50   0:00 [pyt] <defunct>
lemaitre  2123  0.0  0.1  23276  4468 pts/1    Ss+  10:50   0:00 /bin/bash
lemaitre  2146  0.0  0.3 411544 13540 ?        Sl   10:50   0:00 /usr/lib/notify
lemaitre  2155  0.0  0.0 262088  2756 ?        Sl   10:50   0:00 /usr/lib/dconf/
lemaitre  2159  0.0  0.0   4400   612 ?        Ss   10:50   0:00 /bin/sh -c /usr
lemaitre  2160  0.0  0.3 314800 12436 ?        Sl   10:50   0:00 /usr/bin/gtk-wi
lemaitre  2206  0.0  0.2 305888  9136 ?        Sl   10:50   0:00 /usr/bin/gnome-
lemaitre  2216  0.0  0.4 711404 16952 ?        Sl   10:50   0:00 nm-applet
lemaitre  2218  0.2  0.9 1064852 39652 ?       Sl   10:50   0:00 nautilus -n
lemaitre  2221  0.0  0.2 450804  8760 ?        Sl   10:50   0:00 /usr/lib/gnome-
lemaitre  2225  0.0  0.3 503960 12444 ?        Sl   10:50   0:00 bluetooth-apple
lemaitre  2231  0.2  0.9 921296 38528 ?        Sl   10:50   0:00 cairo-dock
lemaitre  2234  0.5  0.2 479116 11580 ?        Sl   10:50   0:01 indicator-multi
lemaitre  2240  0.0  0.6 536224 26904 ?        Sl   10:50   0:00 guake -OO /usr/
lemaitre  2265  0.1  0.2 481224 10816 ?        Sl   10:50   0:00 /usr/lib/bamf/b
lemaitre  2278  0.0  0.0  66120  3664 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  2282  0.0  0.0  56148  2496 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  2284  0.0  0.0 137888  2512 ?        Sl   10:50   0:00 /usr/lib/gvfs/g
lemaitre  2320  0.0  0.0  52688  3232 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  2322  0.0  0.0  48352  2612 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  2328  0.0  0.0      0     0 ?        Z    10:50   0:00 [pyt] <defunct>
lemaitre  2329  0.0  0.1  23272  4396 pts/2    Ss+  10:50   0:00 /bin/bash
lemaitre  2344  0.0  0.3 411528 13460 ?        Sl   10:50   0:00 /usr/lib/notify
lemaitre  2387  0.0  0.2 305868  8828 ?        Sl   10:50   0:00 /usr/bin/gnome-
lemaitre  2395  0.0  0.0  54808  3232 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  2396  0.3  0.5  54984 21660 ?        S    10:50   0:01 /usr/bin/Xvnc-c
root      2397  0.0  0.0  16312   360 ?        S    10:50   0:00 /usr/bin/Xvnc :
lemaitre  2399  0.0  0.1 120376  6944 ?        S    10:50   0:00 /usr/bin/vncser
lemaitre  2433  0.0  0.2 470772 10392 ?        Sl   10:50   0:00 /usr/bin/vncser
lemaitre  2440  0.0  0.0  26556   532 ?        S    10:50   0:00 dbus-launch --a
lemaitre  2441  0.0  0.0  23816   688 ?        Ss   10:50   0:00 //bin/dbus-daem
lemaitre  2445  0.0  0.0   4400   616 ?        S    10:50   0:00 /bin/sh /etc/vn
lemaitre  2450  0.0  0.2 391192 10368 ?        Sl   10:50   0:00 /usr/bin/gnome-
lemaitre  2479  0.0  0.0  26556   532 ?        S    10:50   0:00 /usr/bin/dbus-l
lemaitre  2480  0.3  0.0  27404  3060 ?        Ss   10:50   0:01 //bin/dbus-daem
lemaitre  2484  0.0  0.0  48192  2456 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  2492  0.0  0.0 371712  3500 ?        Sl   10:50   0:00 /usr/bin/gnome-
lemaitre  2495  0.1  0.4 777964 19188 ?        Sl   10:50   0:00 /usr/lib/gnome-
lemaitre  2506  0.0  0.2 327556  9248 ?        Sl   10:50   0:00 /usr/lib/gnome-
lemaitre  2509  0.0  0.3 413100 12536 ?        Sl   10:50   0:00 metacity
lemaitre  2511  0.0  0.0  53944  3836 ?        S    10:50   0:00 /usr/lib/x86_64
lemaitre  2515  0.9  0.4 592724 19468 ?        Sl   10:50   0:02 /usr/lib/unity/
lemaitre  2519  0.2  0.9 631180 36944 ?        Sl   10:50   0:00 unity-2d-panel
lemaitre  2520  0.5  1.9 1065240 77732 ?       Sl   10:50   0:01 unity-2d-shell
lemaitre  2540  0.0  0.4 637672 16944 ?        Sl   10:50   0:00 nm-applet
lemaitre  2542  0.2  0.9 851828 39700 ?        Sl   10:50   0:00 nautilus -n
lemaitre  2547  0.1  0.2 481232 10860 ?        Sl   10:50   0:00 /usr/lib/bamf/b
lemaitre  2552  0.0  0.2 450936  8916 ?        Sl   10:50   0:00 /usr/lib/gnome-
lemaitre  2554  0.0  0.3 495772 12612 ?        Sl   10:50   0:00 bluetooth-apple
lemaitre  2556  0.0  0.0 262088  2732 ?        Sl   10:50   0:00 /usr/lib/dconf/
lemaitre  2563  0.2  0.9 921224 38360 ?        Sl   10:50   0:00 cairo-dock
lemaitre  2566  0.5  0.2 386220 10304 ?        Sl   10:50   0:01 indicator-multi
lemaitre  2584  0.1  0.6 536240 26776 ?        Sl   10:50   0:00 guake -OO /usr/
lemaitre  2606  0.0  0.1 553088  7404 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  2612  0.0  0.1 598116  6084 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  2615  0.0  0.1 380340  6488 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  2616  0.3  0.5  54976 21428 ?        S    10:50   0:01 /usr/bin/Xvnc-c
root      2617  0.0  0.0  16312   360 ?        S    10:50   0:00 /usr/bin/Xvnc :
lemaitre  2619  0.0  0.1 120376  6948 ?        S    10:50   0:00 /usr/bin/vncser
lemaitre  2632  0.0  0.1 533772  6968 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  2635  0.0  0.2 419528 10040 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  2661  0.2  0.1 347936  5128 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  2666  0.0  0.2 544508 10244 ?        Sl   10:50   0:00 /usr/bin/vncser
lemaitre  2673  0.0  0.0  26556   532 ?        S    10:50   0:00 dbus-launch --a
lemaitre  2679  0.0  0.0  66116  3660 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  2681  0.0  0.0  23816   684 ?        Ss   10:50   0:00 //bin/dbus-daem
lemaitre  2685  0.0  0.0  47860  2712 ?        S    10:50   0:00 /usr/lib/geoclu
lemaitre  2694  0.0  0.1 160644  5252 ?        S    10:50   0:00 /usr/lib/ubuntu
lemaitre  2697  0.0  0.0  56148  2496 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  2702  0.0  0.0 137888  2512 ?        Sl   10:50   0:00 /usr/lib/gvfs/g
lemaitre  2727  0.9  0.4 592844 19568 ?        Sl   10:50   0:02 /usr/lib/unity/
lemaitre  2732  0.0  0.0   4400   612 ?        S    10:50   0:00 /bin/sh /etc/vn
lemaitre  2740  0.0  0.2 391204 10404 ?        Sl   10:50   0:00 /usr/bin/gnome-
lemaitre  2768  0.0  0.0  26556   532 ?        S    10:50   0:00 /usr/bin/dbus-l
lemaitre  2769  0.3  0.0  27408  3052 ?        Ss   10:50   0:01 //bin/dbus-daem
lemaitre  2772  0.0  0.1 553084  7388 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  2778  0.0  0.0  48192  2456 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  2779  0.0  0.1 532580  6084 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  2780  0.0  0.1 642480  6580 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  2785  0.0  0.1 451844  6968 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  2790  0.0  0.2 419528 10032 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  2793  0.2  0.1 421664  5140 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  2798  0.0  0.0  47860  2712 ?        S    10:50   0:00 /usr/lib/geoclu
lemaitre  2817  0.0  0.0 371712  3496 ?        Sl   10:50   0:00 /usr/bin/gnome-
lemaitre  2823  0.1  0.4 704236 19340 ?        Sl   10:50   0:00 /usr/lib/gnome-
lemaitre  2842  0.0  0.1 160644  5244 ?        S    10:50   0:00 /usr/lib/ubuntu
lemaitre  2846  0.0  0.3 413112 12544 ?        Sl   10:50   0:00 metacity
lemaitre  2852  0.0  0.0  53948  3800 ?        S    10:50   0:00 /usr/lib/x86_64
lemaitre  2867  0.2  0.9 631092 37144 ?        Sl   10:50   0:00 unity-2d-panel
lemaitre  2868  0.5  1.9 1065240 77672 ?       Sl   10:50   0:01 unity-2d-shell
lemaitre  2895  0.0  0.0 262092  2720 ?        Sl   10:50   0:00 /usr/lib/dconf/
lemaitre  2902  0.0  0.0  54808  3236 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  2904  0.0  0.4 637664 17096 ?        Sl   10:50   0:00 nm-applet
lemaitre  2906  0.1  0.9 851828 39656 ?        Sl   10:50   0:00 nautilus -n
lemaitre  2909  0.0  0.0  52688  3240 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  2911  0.0  0.2 450808  8968 ?        Sl   10:50   0:00 /usr/lib/gnome-
lemaitre  2914  0.0  0.3 495728 12608 ?        Sl   10:50   0:00 bluetooth-apple
lemaitre  2921  0.1  0.9 921296 38364 ?        Sl   10:50   0:00 cairo-dock
lemaitre  2925  0.1  0.2 481232 10812 ?        Sl   10:50   0:00 /usr/lib/bamf/b
lemaitre  2928  0.5  0.2 479120 11572 ?        Sl   10:50   0:01 indicator-multi
lemaitre  2936  0.1  0.6 536248 26780 ?        Sl   10:50   0:00 guake -OO /usr/
lemaitre  2961  0.0  0.0  48352  2612 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  2976  0.3  0.4  51504 18308 ?        S    10:50   0:01 /usr/bin/Xvnc-c
root      2977  0.0  0.0  16312   360 ?        S    10:50   0:00 /usr/bin/Xvnc :
lemaitre  2979  0.0  0.1 120376  6948 ?        S    10:50   0:00 /usr/bin/vncser
lemaitre  3018  0.0  0.0  66120  3660 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  3020  0.0  0.2 544508 10260 ?        Sl   10:50   0:00 /usr/bin/vncser
lemaitre  3025  0.0  0.0  26556   532 ?        S    10:50   0:00 dbus-launch --a
lemaitre  3026  0.0  0.0  23816   688 ?        Ss   10:50   0:00 //bin/dbus-daem
lemaitre  3030  0.0  0.0  56148  2496 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  3032  0.0  0.0 137888  2512 ?        Sl   10:50   0:00 /usr/lib/gvfs/g
lemaitre  3038  0.0  0.0      0     0 ?        Z    10:50   0:00 [pyt] <defunct>
lemaitre  3039  0.0  0.1  23276  4480 pts/5    Ss+  10:50   0:00 /bin/bash
lemaitre  3057  0.0  0.3 413504 13436 ?        Sl   10:50   0:00 /usr/lib/notify
lemaitre  3060  0.0  0.2 425324 11056 ?        Sl   10:50   0:00 telepathy-indic
lemaitre  3095  0.0  0.2 305856  8820 ?        Sl   10:50   0:00 /usr/bin/gnome-
lemaitre  3110  0.0  0.0   4400   616 ?        S    10:50   0:00 /bin/sh /etc/vn
lemaitre  3116  0.0  0.2 391204 10404 ?        Sl   10:50   0:00 /usr/bin/gnome-
lemaitre  3145  0.0  0.0  26556   532 ?        S    10:50   0:00 /usr/bin/dbus-l
lemaitre  3146  0.3  0.0  27416  3148 ?        Ss   10:50   0:01 //bin/dbus-daem
lemaitre  3148  0.9  0.4 518828 19216 ?        Sl   10:50   0:02 /usr/lib/unity/
lemaitre  3154  0.0  0.0  48192  2452 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  3160  0.0  0.1 321520  6912 ?        Sl   10:50   0:00 /usr/lib/telepa
lemaitre  3165  0.0  0.3 400172 13744 ?        Sl   10:50   0:00 /usr/lib/gnome-
lemaitre  3174  0.0  0.0 371712  3500 ?        Sl   10:50   0:00 /usr/bin/gnome-
lemaitre  3175  0.1  0.4 704260 19088 ?        Sl   10:50   0:00 /usr/lib/gnome-
lemaitre  3182  0.0  0.1 524384  6072 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  3183  0.0  0.1 626816  7384 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  3191  0.0  0.1 642480  6568 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  3194  0.0  0.1 525580  6964 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  3200  0.0  0.2 419524 10032 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  3201  0.2  0.1 560936  5164 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  3223  0.0  0.0  47860  2712 ?        S    10:50   0:00 /usr/lib/geoclu
lemaitre  3237  0.0  0.2 327560  9176 ?        Sl   10:50   0:00 /usr/lib/gnome-
lemaitre  3244  0.0  0.3 413072 12508 ?        Sl   10:50   0:00 metacity
lemaitre  3257  0.0  0.1 160644  5244 ?        S    10:50   0:00 /usr/lib/ubuntu
lemaitre  3260  0.0  0.0  53948  3800 ?        S    10:50   0:00 /usr/lib/x86_64
lemaitre  3263  0.2  0.9 631224 37088 ?        Sl   10:50   0:00 unity-2d-panel
lemaitre  3265  0.5  1.9 1327384 77884 ?       Sl   10:50   0:01 unity-2d-shell
lemaitre  3289  0.0  0.0 262092  2724 ?        Sl   10:50   0:00 /usr/lib/dconf/
lemaitre  3300  0.7  0.1 697100  4588 ?        Sl   10:50   0:02 /usr/lib/indica
lemaitre  3313  0.0  0.4 711312 16976 ?        Sl   10:50   0:00 nm-applet
lemaitre  3315  0.1  0.9 851760 39712 ?        Sl   10:50   0:00 nautilus -n
lemaitre  3317  0.1  0.2 481172 10792 ?        Sl   10:50   0:00 /usr/lib/bamf/b
lemaitre  3321  0.0  0.2 450936  8948 ?        Sl   10:50   0:00 /usr/lib/gnome-
lemaitre  3323  0.0  0.3 495732 12440 ?        Sl   10:50   0:00 bluetooth-apple
lemaitre  3326  0.2  0.9 921280 38520 ?        Sl   10:50   0:00 cairo-dock
lemaitre  3335  0.5  0.2 479120 11740 ?        Sl   10:50   0:01 indicator-multi
lemaitre  3345  0.1  0.6 536236 26912 ?        Sl   10:50   0:00 guake -OO /usr/
lemaitre  3383  0.0  0.3 510600 16104 ?        Sl   10:50   0:00 /usr/bin/python
lemaitre  3385  0.0  0.2 341012  8280 ?        Sl   10:50   0:00 /usr/lib/unity-
lemaitre  3386  0.0  0.1 479152  6152 ?        Sl   10:50   0:00 /usr/lib/unity-
lemaitre  3387  0.1  0.3 413572 12368 ?        Sl   10:50   0:00 /usr/lib/unity-
lemaitre  3391  0.0  0.0  54808  3228 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  3395  0.0  0.0  52688  3228 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  3409  0.0  0.0  66120  3660 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  3416  0.0  0.0  56148  2500 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  3425  0.0  0.0 137888  2512 ?        Sl   10:50   0:00 /usr/lib/gvfs/g
lemaitre  3444  0.0  0.0 339184  3912 ?        Sl   10:50   0:00 /usr/bin/zeitge
lemaitre  3455  0.0  0.0  48352  2612 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  3476  0.9  0.4 592748 19536 ?        Sl   10:50   0:02 /usr/lib/unity/
lemaitre  3480  0.0  0.0      0     0 ?        Z    10:50   0:00 [pyt] <defunct>
lemaitre  3481  0.0  0.1  23276  4392 pts/6    Ss+  10:50   0:00 /bin/bash
lemaitre  3498  0.0  0.3 413508 13436 ?        Sl   10:50   0:00 /usr/lib/notify
lemaitre  3506  0.0  0.1 479356  7372 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  3511  0.0  0.1 524384  6080 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  3514  0.0  0.1 235564  5356 ?        Sl   10:50   0:00 /usr/lib/zeitge
lemaitre  3516  0.0  0.1 417580  5704 ?        Sl   10:50   0:00 zeitgeist-datah
lemaitre  3517  0.0  0.1 642484  6788 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  3519  0.0  0.1 533772  6928 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  3521  0.0  0.2 419528 10024 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  3524  0.0  0.0   7192   360 ?        S    10:50   0:00 /bin/cat
lemaitre  3525  0.2  0.1 421660  5140 ?        Sl   10:50   0:00 /usr/lib/indica
lemaitre  3530  0.0  0.2 305856  8872 ?        Sl   10:50   0:00 /usr/bin/gnome-
lemaitre  3542  0.0  0.1 417576  5780 ?        Sl   10:50   0:00 zeitgeist-datah
lemaitre  3614  0.0  0.1 348100  4576 ?        Sl   10:50   0:00 /usr/bin/zeitge
lemaitre  3617  0.7  0.1 697104  4484 ?        Sl   10:50   0:02 /usr/lib/indica
lemaitre  3636  0.0  0.0  47860  2712 ?        S    10:50   0:00 /usr/lib/geoclu
lemaitre  3668  0.0  0.1 160644  5252 ?        S    10:50   0:00 /usr/lib/ubuntu
lemaitre  3675  0.0  0.2 425320 10968 ?        Sl   10:50   0:00 telepathy-indic
lemaitre  3677  0.0  0.2 327544  9176 ?        Sl   10:50   0:00 /usr/lib/gnome-
lemaitre  3691  0.0  0.1 321524  6944 ?        Sl   10:50   0:00 /usr/lib/telepa
lemaitre  3699  0.0  0.0  52688  3228 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  3703  0.0  0.3 400172 13744 ?        Sl   10:50   0:00 /usr/lib/gnome-
lemaitre  3713  0.0  0.1 320080  4304 ?        Sl   10:50   0:00 /usr/lib/unity-
lemaitre  3714  0.0  0.4 541120 17584 ?        Sl   10:50   0:00 /usr/bin/python
lemaitre  3716  0.1  0.3 413588 12396 ?        Sl   10:50   0:00 /usr/lib/unity-
lemaitre  3718  0.0  0.1 479116  6140 ?        Sl   10:50   0:00 /usr/lib/unity-
lemaitre  3721  0.0  0.2 406544  8500 ?        Sl   10:50   0:00 /usr/lib/unity-
lemaitre  3729  0.0  0.3 510592 16104 ?        Sl   10:50   0:00 /usr/bin/python
lemaitre  3763  0.0  0.0 339184  3988 ?        Sl   10:50   0:00 /usr/bin/zeitge
lemaitre  3765  0.0  0.0  48352  2612 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  3776  0.0  0.1 417576  5704 ?        Sl   10:50   0:00 zeitgeist-datah
lemaitre  3790  0.0  0.0  54808  3232 ?        S    10:50   0:00 /usr/lib/gvfs/g
lemaitre  3819  0.0  0.2 327548  9180 ?        Sl   10:50   0:00 /usr/lib/gnome-
lemaitre  3834  0.0  0.0      0     0 ?        Z    10:50   0:00 [pyt] <defunct>
lemaitre  3835  0.0  0.1  23276  4484 pts/7    Ss+  10:50   0:00 /bin/bash
lemaitre  3850  0.0  0.3 413596 13476 ?        Sl   10:50   0:00 /usr/lib/notify
lemaitre  3894  0.0  0.2 305856  8868 ?        Sl   10:50   0:00 /usr/bin/gnome-
lemaitre  3918  0.0  0.1 320080  4308 ?        Sl   10:50   0:00 /usr/lib/unity-
lemaitre  3969  0.7  0.1 631560  4848 ?        Sl   10:50   0:01 /usr/lib/indica
lemaitre  3987  0.0  0.4 541120 17584 ?        Sl   10:50   0:00 /usr/bin/python
lemaitre  3988  0.0  0.2 425320 10976 ?        Sl   10:50   0:00 telepathy-indic
lemaitre  4001  0.1  0.3 413580 12412 ?        Sl   10:50   0:00 /usr/lib/unity-
lemaitre  4009  0.0  0.2 734224  8536 ?        Sl   10:50   0:00 /usr/lib/unity-
lemaitre  4010  0.0  0.1 610208  6204 ?        Sl   10:50   0:00 /usr/lib/unity-
lemaitre  4012  0.0  0.3 510596 16108 ?        Sl   10:50   0:00 /usr/bin/python
lemaitre  4014  0.0  0.1 321524  6928 ?        Sl   10:50   0:00 /usr/lib/telepa
lemaitre  4048  0.0  0.3 400172 13740 ?        Sl   10:50   0:00 /usr/lib/gnome-
lemaitre  4055  0.0  0.0 339184  3888 ?        Sl   10:50   0:00 /usr/bin/zeitge
lemaitre  4067  0.0  0.1 417576  5696 ?        Sl   10:50   0:00 zeitgeist-datah
lemaitre  4083  0.0  0.2 327552  9188 ?        Sl   10:50   0:00 /usr/lib/gnome-
lemaitre  4086  0.0  0.2 425312 10996 ?        Sl   10:50   0:00 telepathy-indic
lemaitre  4093  0.0  0.1 321524  6924 ?        Sl   10:50   0:00 /usr/lib/telepa
lemaitre  4098  0.0  0.3 400172 13744 ?        Sl   10:50   0:00 /usr/lib/gnome-
lemaitre  4103  0.0  0.1 320084  4308 ?        Sl   10:50   0:00 /usr/lib/unity-
lemaitre  4120  0.7  0.1 566016  4548 ?        Sl   10:50   0:01 /usr/lib/indica
lemaitre  4168  0.0  0.4 541128 17588 ?        Sl   10:50   0:00 /usr/bin/python
lemaitre  4206  0.1  0.3 413576 12396 ?        Sl   10:50   0:00 /usr/lib/unity-
lemaitre  4211  0.0  0.3 510600 16108 ?        Sl   10:50   0:00 /usr/bin/python
lemaitre  4215  0.0  0.2 406552  8360 ?        Sl   10:50   0:00 /usr/lib/unity-
lemaitre  4216  0.0  0.1 479156  6152 ?        Sl   10:50   0:00 /usr/lib/unity-
lemaitre  4268  0.0  0.0 273648  3884 ?        Sl   10:50   0:00 /usr/bin/zeitge
lemaitre  4291  0.0  0.1 417576  5700 ?        Sl   10:50   0:00 zeitgeist-datah
lemaitre  4409  0.0  0.2 425308 10976 ?        Sl   10:50   0:00 telepathy-indic
lemaitre  4453  0.0  0.1 321528  6924 ?        Sl   10:50   0:00 /usr/lib/telepa
lemaitre  4466  0.0  0.3 400172 13744 ?        Sl   10:50   0:00 /usr/lib/gnome-
lemaitre  4513  0.0  0.1 582228  4340 ?        Sl   10:50   0:00 /usr/lib/unity-
lemaitre  4635  0.0  0.4 541116 17584 ?        Sl   10:50   0:00 /usr/bin/python
lemaitre  5696 34.9  0.7 613280 30480 ?        Sl   10:50   1:28 gnome-system-mo
lemaitre  5705  0.0  0.3 496368 14648 ?        Sl   10:51   0:00 update-notifier
root      5717  0.0  0.3  95332 12304 ?        S    10:51   0:00 /usr/bin/python
lemaitre  5720  2.6  2.1 693448 88080 ?        SLl  10:51   0:06 /opt/google/chr
lemaitre  5725  0.0  0.1 253844  7452 ?        S    10:51   0:00 /opt/google/chr
lemaitre  5726  0.0  0.0   6460   396 ?        S    10:51   0:00 /opt/google/chr
lemaitre  5727  0.0  0.5 292828 20948 ?        S    10:51   0:00 /opt/google/chr
lemaitre  5731  0.0  0.1 131956  4352 ?        S    10:51   0:00 /opt/google/chr
lemaitre  5733  0.0  0.1 301024  6492 ?        S    10:51   0:00 /opt/google/chr
lemaitre  5735  0.0  0.3 477220 13392 ?        Sl   10:51   0:00 update-notifier
lemaitre  5793  0.0  0.6 881396 26976 ?        Sl   10:51   0:00 /opt/google/chr
lemaitre  5835  0.0  0.6 881396 27132 ?        Sl   10:51   0:00 /opt/google/chr
lemaitre  5841  0.0  0.7 885816 32292 ?        Sl   10:51   0:00 /opt/google/chr
lemaitre  5847  0.0  0.6 884468 27268 ?        Sl   10:51   0:00 /opt/google/chr
lemaitre  5854  0.0  0.7 882744 29988 ?        Sl   10:51   0:00 /opt/google/chr
lemaitre  5871  0.0  0.3 403460 13300 ?        Sl   10:51   0:00 update-notifier
root      5878  2.7  2.0 192328 83108 ?        SN   10:51   0:06 /usr/bin/python
lemaitre  5921  0.0  0.3 403468 13288 ?        Sl   10:51   0:00 update-notifier
lemaitre  5957  0.0  0.3 403468 13300 ?        Sl   10:51   0:00 update-notifier
lemaitre  5964  1.7  1.5 920716 61776 ?        Sl   10:51   0:03 /opt/google/chr
lemaitre  5998  0.0  0.0 289488  4012 ?        Sl   10:52   0:00 /usr/lib/deja-d
lemaitre  6003  0.0  0.0 289516  3892 ?        Sl   10:52   0:00 /usr/lib/deja-d
lemaitre  6008  0.0  0.0 289488  4004 ?        Sl   10:52   0:00 /usr/lib/deja-d
lemaitre  6013  0.0  0.0 289516  3892 ?        Sl   10:52   0:00 /usr/lib/deja-d
lemaitre  6025  0.0  0.0 289516  3896 ?        Sl   10:52   0:00 /usr/lib/deja-d
root      6053  0.0  0.0      0     0 ?        S    10:54   0:00 [kworker/0:2]
root      6061  0.0  0.0      0     0 ?        S    10:54   0:00 [kworker/u:0]
lemaitre  6071  0.0  0.0   4400   616 ?        Ss   10:55   0:00 /bin/sh -c gnom
lemaitre  6072  4.6  0.4 576956 16936 ?        Sl   10:55   0:00 gnome-terminal
lemaitre  6076  0.0  0.0  14788   828 ?        S    10:55   0:00 gnome-pty-helpe
lemaitre  6077  4.0  0.1  23280  4460 pts/8    Ss   10:55   0:00 bash
lemaitre  6130  0.0  0.0  18172  1264 pts/8    R+   10:55   0:00 ps aux
```

Thanks in advance,

Best regards,
--
Guillaume

---

### Post by mikewhatever on 2012-10-26
What's your point, and why would you need to reinstall everything?

---

### Post by lguigui58 on 2012-10-26
> **mikewhatever said:**
> What's your point, and why would you need to reinstall everything?

My point is that I would like to avoid these duplicate processes in order to be less memory consuming.

By reinstalling, I am pretty sure to not have the same problem. I think that I did something wrong which implying this malfunctioning.

Best regards,
--
Guillaume

---

### Post by Wim Sturkenboom on 2012-10-26
I'm not familiar with most processes in your list. But it can be quite normal to see duplicates. Just depends on the application / daemon.

---

### Post by mikewhatever on 2012-10-26
I don't see anything out of the ordinary with your list of processes. What exactly could you have done wrong? Most of the "duplicates" are kernel jobs, stopping which will likely cause problems.

...here's the list of mine:
```
~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   3540  1988 ?        Ss   08:21   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    08:21   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    08:21   0:00 [ksoftirqd/0]
root         6  0.0  0.0      0     0 ?        S    08:21   0:00 [migration/0]
root         7  0.0  0.0      0     0 ?        S    08:21   0:00 [watchdog/0]
root         8  0.0  0.0      0     0 ?        S    08:21   0:00 [migration/1]
root        10  0.0  0.0      0     0 ?        S    08:21   0:00 [ksoftirqd/1]
root        12  0.0  0.0      0     0 ?        S    08:21   0:00 [watchdog/1]
root        13  0.0  0.0      0     0 ?        S<   08:21   0:00 [cpuset]
root        14  0.0  0.0      0     0 ?        S<   08:21   0:00 [khelper]
root        15  0.0  0.0      0     0 ?        S    08:21   0:00 [kdevtmpfs]
root        16  0.0  0.0      0     0 ?        S<   08:21   0:00 [netns]
root        18  0.0  0.0      0     0 ?        S    08:21   0:00 [sync_supers]
root        19  0.0  0.0      0     0 ?        S    08:21   0:00 [bdi-default]
root        20  0.0  0.0      0     0 ?        S<   08:21   0:00 [kintegrityd]
root        21  0.0  0.0      0     0 ?        S<   08:21   0:00 [kblockd]
root        22  0.0  0.0      0     0 ?        S<   08:21   0:00 [ata_sff]
root        23  0.0  0.0      0     0 ?        S    08:21   0:00 [khubd]
root        24  0.0  0.0      0     0 ?        S<   08:21   0:00 [md]
root        25  0.0  0.0      0     0 ?        R    08:21   0:08 [kworker/1:1]
root        26  0.0  0.0      0     0 ?        S    08:21   0:00 [khungtaskd]
root        27  0.0  0.0      0     0 ?        S    08:21   0:00 [kswapd0]
root        28  0.0  0.0      0     0 ?        SN   08:21   0:00 [ksmd]
root        29  0.0  0.0      0     0 ?        SN   08:21   0:00 [khugepaged]
root        30  0.0  0.0      0     0 ?        S    08:21   0:00 [fsnotify_mark]
root        31  0.0  0.0      0     0 ?        S    08:21   0:00 [ecryptfs-kthrea]
root        32  0.0  0.0      0     0 ?        S<   08:21   0:00 [crypto]
root        40  0.0  0.0      0     0 ?        S<   08:21   0:00 [kthrotld]
root        43  0.0  0.0      0     0 ?        S    08:21   0:00 [scsi_eh_0]
root        44  0.0  0.0      0     0 ?        S    08:21   0:00 [scsi_eh_1]
root        45  0.0  0.0      0     0 ?        S    08:21   0:00 [scsi_eh_2]
root        46  0.0  0.0      0     0 ?        S    08:21   0:00 [scsi_eh_3]
root        49  0.0  0.0      0     0 ?        S    08:21   0:00 [scsi_eh_4]
root        50  0.0  0.0      0     0 ?        S    08:21   0:00 [scsi_eh_5]

```

---

### Post by lguigui58 on 2012-10-26
> **Wim Sturkenboom said:**
> I'm not familiar with most processes in your list. But it can be quite normal to see duplicates. Just depends on the application / daemon.

After checking a bit more about the different processes, it seems that when I am logging in, several gnome-session are loading too which have as consequence to load 5 times all the processes. However, I still don't have any clue why the session is loaded 5 times instead of one.
--
Guillaume

---

### Post by westie457 on 2012-10-26
I too see nothing wrong with the output of ps aux.
This is what a normally configured installation does. The same sort of things happen in Windows.

We could fill this thread with screenshots that will all show basically the same things.

Unless your computer has genuine memory issues there is not much to be done in this case.

How much RAM is installed?

---

### Post by lguigui58 on 2012-10-26
> **westie457 said:**
> I too see nothing wrong with the output of ps aux.
This is what a normally configured installation does. The same sort of things happen in Windows.

We could fill this thread with screenshots that will all show basically the same things.

Unless your computer has genuine memory issues there is not much to be done in this case.

How much RAM is installed?

Uhm after watching the result of ps aux, it seems that the process shown are only from the current session which is explaining why you cannot see duplicate processes.

However it is possible to see it using the system manager.
I attached two print screen. The first one is after that I logged in. You can see 5 gnome-session processes which imply that all system processes have been loaded 5 times too -> 1.8 GB RAM.

By killing only 4 of these gnome-session (print screen 2) which are not the one that I am actually using only 800 Mb of RAM.

So I am trying to know why 5 gnome-session are loaded. I tried to see some information about that inside the log file of LightDM but I am still in a blur.

Best,
-- 
Guillaume

---

### Post by mikewhatever on 2012-10-26
Can you reboot, and then post the output of
```
free -m
```

then, expand a terminal window full-screen, and post the outpu of
```
ps aux | grep gnome-session
```

---

### Post by lguigui58 on 2012-10-26
Hey,

After the different command, please find the output (in attachment also):

```

lemaitre@lemaitre-UdG:~$ ps aux | grep gnome-session
lemaitre  1746  0.1  0.2 391064 10344 ?        Ssl  14:14   0:00 gnome-session --session=ubuntu
lemaitre  1783  0.0  0.0  12492   320 ?        Ss   14:14   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session --session=ubuntu
lemaitre  1786  0.0  0.0  26556   784 ?        S    14:14   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session --session=ubuntu
lemaitre  1966  0.1  0.2 391084 10308 ?        Sl   14:14   0:00 /usr/bin/gnome-session --session=ubuntu-2d
lemaitre  2003  0.0  0.0  26556   536 ?        S    14:14   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session --session=ubuntu-2d
lemaitre  2284  0.1  0.2 391040 10252 ?        Sl   14:15   0:00 /usr/bin/gnome-session --session=ubuntu-2d
lemaitre  2312  0.0  0.0  26556   532 ?        S    14:15   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session --session=ubuntu-2d
lemaitre  2602  0.1  0.2 391052 10320 ?        Sl   14:15   0:00 /usr/bin/gnome-session --session=ubuntu-2d
lemaitre  2641  0.0  0.0  26556   536 ?        S    14:15   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session --session=ubuntu-2d
lemaitre  3024  0.1  0.2 391044 10312 ?        Sl   14:15   0:00 /usr/bin/gnome-session --session=ubuntu-2d
lemaitre  3057  0.0  0.0  26556   536 ?        S    14:15   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session --session=ubuntu-2d
lemaitre  3323  0.1  0.2 391040 10272 ?        Sl   14:15   0:00 /usr/bin/gnome-session --session=ubuntu-2d
lemaitre  3354  0.0  0.0  26556   532 ?        S    14:15   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session --session=ubuntu-2d
lemaitre  6303  0.0  0.0   9400   924 pts/8    S+   14:16   0:00 grep --color=auto gnome-session
lemaitre@lemaitre-UdG:~$ 

```

Best,
--
Guillaume

---

### Post by dino99 on 2012-10-26
I agree that something is borked there :(

Is it a fresh install ? or have you made some tweaks and experiments ?

By the way, i propose you open synaptic (sudo apt-get install synaptic), search for:

- ubuntu-desktop : uninstall it for now
- compiz :  uninstall ALL the related packages (*compiz*)
- unity : uninstall them all also

next step:
- install unity  (which is by default the 3D)
- or install unity-2d

Thats it, now logout/in again, and watch the difference (if any)
If the system is loading less gnome-session than previously, and are satisfied, then reinstall ubuntu-desktop.

---

### Post by mikewhatever on 2012-10-26
Yes, you seem to have too many of these:
```
/usr/bin/gnome-session --session=ubuntu-2d
```

Not sure why. It looks like you've been customizing suff quite a bit. What have you installed exactly?

---

### Post by lguigui58 on 2012-10-26
> **dino99 said:**
> I agree that something is borked there :(

Is it a fresh install ? or have you made some tweaks and experiments ?


Basically I installed ubuntu tweak and compiz to change the property of the side launcher and font size. I did the same on my laptop and I didn't have any of these problem. I will try to re-install what you suggested.

Best
--
Guillaume

---

### Post by dino99 on 2012-10-26
> **lguigui58 said:**
> Basically I installed ubuntu tweak and compiz to change the property of the side launcher and font size. I did the same on my laptop and I didn't have any of these problem. I will try to re-install what you suggested.

Best
--
Guillaume

you can use ubuntu-tweak but with care (to me it feels like too dangerous for non techies)

---

### Post by lguigui58 on 2012-10-26
Ok,

Since that it seems that unity2d was loading without any purpose, I removed it (I was using unity). Finally, it is not loading anymore since that I removed it :P.

However I don't know what was the real problem under that.

So we can said that the problem is solved. Thanks to everybody.

Best,
--
Guillaume

---

