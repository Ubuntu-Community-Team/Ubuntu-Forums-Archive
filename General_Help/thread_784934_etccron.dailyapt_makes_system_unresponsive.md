---
title: "/etc/cron.daily/apt makes system unresponsive"
date: 2008-05-06
forum: General Help
---

### Post by bcrowell on 2008-05-06
After upgrading to Hardy Heron, I noticed that my system was unresponsive for about 15 minutes every day after I booted it up. E.g., I would open firefox, click on a menu, and it would take 10 seconds or something for the menu to pop up. The hard disk was chittering like crazy the whole time. Using the "top" command didn't reveal the offending process, presumably since it was killing my system with disk I/O rather than CPU hogging. I finally tried logging in as root and doing a "ps aux", and comparing the results when the system was unresponsive and when it wasn't. I can't be totally sure, but it looks to me like the offender is /etc/cron.daily/apt, which is run by anacron.

As far as I can tell without thoroughly going over the (uncommented) code, the script is doing things like apt-get updates. I don't understand (a) why it would do this when I didn't ask it to, or (b) why it would bring my system to its knees for 15 minutes. Can anyone verify my interpretation of what's going on, or shed any light on this? I run fluxbox, not Gnome. I know that Gnome pops up an icon and a word balloon when there are updates available, but from the occasions when I used Gnome, I don't recall that it ever made my system unusable for 15 minutes.

I'm guessing that I won't do any harm by moving this script out of /etc/cron.daily, so that it won't be run.

Comments? Is this a bug in hardy that I should report? Is there some better way to diagnose it? I can't seem to find any options in the man page for "top" that would identify high-I/O jobs. Below is the output of "ps aux".

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.1   4016   876 ?        Ss   19:40   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   19:40   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   19:40   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   19:40   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   19:40   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   19:40   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   19:40   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   19:40   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   19:40   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   19:40   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   19:40   0:00 [khelper]
root        45  0.0  0.0      0     0 ?        S<   19:40   0:00 [kblockd/0]
root        46  0.0  0.0      0     0 ?        R<   19:40   0:00 [kblockd/1]
root        49  0.0  0.0      0     0 ?        S<   19:40   0:00 [kacpid]
root        50  0.0  0.0      0     0 ?        S<   19:40   0:00 [kacpi_notify]
root       159  0.0  0.0      0     0 ?        S<   19:40   0:00 [kseriod]
root       209  0.0  0.0      0     0 ?        S    19:40   0:00 [pdflush]
root       210  0.0  0.0      0     0 ?        S    19:40   0:00 [pdflush]
root       211  0.0  0.0      0     0 ?        S<   19:40   0:00 [kswapd0]
root       255  0.0  0.0      0     0 ?        S<   19:40   0:00 [aio/0]
root       256  0.0  0.0      0     0 ?        S<   19:40   0:00 [aio/1]
root      1615  0.0  0.0      0     0 ?        S<   19:40   0:00 [ksuspend_usbd]
root      1621  0.0  0.0      0     0 ?        S<   19:40   0:00 [khubd]
root      1637  0.0  0.0      0     0 ?        S<   19:40   0:00 [ata/0]
root      1647  0.0  0.0      0     0 ?        S<   19:40   0:00 [ata/1]
root      1650  0.0  0.0      0     0 ?        S<   19:40   0:00 [khpsbpkt]
root      1660  0.0  0.0      0     0 ?        S<   19:40   0:00 [ata_aux]
root      2392  0.0  0.0      0     0 ?        S<   19:40   0:00 [knodemgrd_0]
root      2416  0.0  0.0      0     0 ?        S<   19:40   0:00 [scsi_eh_0]
root      2421  0.0  0.0      0     0 ?        S<   19:40   0:00 [scsi_eh_1]
root      2450  0.0  0.0      0     0 ?        S<   19:40   0:00 [scsi_eh_2]
root      2451  0.0  0.0      0     0 ?        S<   19:40   0:00 [scsi_eh_3]
root      2478  0.0  0.0      0     0 ?        S<   19:40   0:00 [scsi_eh_4]
root      2480  0.0  0.0      0     0 ?        S<   19:40   0:00 [scsi_eh_5]
root      2673  0.0  0.0      0     0 ?        S<   19:40   0:00 [kjournald]
root      2886  0.0  0.2  17212  1328 ?        S<s  19:40   0:00 /sbin/udevd --daemon
root      3154  0.0  0.0      0     0 ?        S<   19:40   0:00 [kpsmoused]
root      4695  0.0  0.1   3860   588 tty4     Ss+  19:40   0:00 /sbin/getty 38400 tty4
root      4696  0.0  0.1   3860   588 tty5     Ss+  19:40   0:00 /sbin/getty 38400 tty5
root      4700  0.0  0.1   3860   584 tty2     Ss+  19:40   0:00 /sbin/getty 38400 tty2
root      4701  0.0  0.1   3860   588 tty3     Ss+  19:40   0:00 /sbin/getty 38400 tty3
root      4702  0.0  0.1   3860   584 tty6     Ss+  19:40   0:00 /sbin/getty 38400 tty6
root      4769  0.0  0.0      0     0 ?        S<   19:40   0:00 [kondemand/0]
root      4770  0.0  0.0      0     0 ?        S<   19:40   0:00 [kondemand/1]
root      4976  0.0  0.3  13072  1748 ?        Ss   19:40   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
syslog    5059  0.0  0.1  12292   716 ?        Ss   19:40   0:00 /sbin/syslogd -u syslog
root      5118  0.0  0.1   8128   588 ?        S    19:40   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      5121  0.0  0.6   6156  2916 ?        Ss   19:40   0:00 /sbin/klogd -P /var/run/klogd/kmsg
103       5143  0.0  0.2  21456  1236 ?        Ss   19:40   0:00 /usr/bin/dbus-daemon --system
root      5160  0.0  0.5  60724  2256 ?        Ssl  19:40   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      5174  0.0  0.3  28380  1420 ?        Ss   19:40   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
root      5187  0.0  0.2  35188  1212 ?        Ss   19:40   0:00 /usr/bin/system-tools-backends
106       5206  0.0  0.9  40140  4424 ?        Ss   19:40   0:00 /usr/sbin/hald
root      5209  0.0  0.5  41088  2528 ?        Ssl  19:40   0:00 /usr/sbin/console-kit-daemon
root      5271  0.0  0.2  22044  1280 ?        S    19:40   0:00 hald-runner
root      5289  0.0  0.2  24164  1244 ?        S    19:40   0:00 /usr/lib/hal/hald-addon-cpufreq
106       5290  0.0  0.2  16668   988 ?        S    19:40   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      5301  0.0  0.2  24152  1284 ?        S    19:40   0:00 hald-addon-input: Listening on /dev/input/event1 /dev/input/event3 /dev/input/event4
root      5317  0.0  0.2  24152  1276 ?        S    19:40   0:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)
root      5472  0.0  0.4 116172  1896 ?        Ss   19:40   0:00 /usr/sbin/gdm
root      5475  0.0  0.7 128908  3308 ?        S    19:40   0:00 /usr/sbin/gdm
root      5487  1.0  5.8 102296 26012 tty7     Ss+  19:40   0:04 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      5667  0.0  0.2  50912  1140 ?        Ss   19:40   0:00 /usr/sbin/sshd
avahi     5713  0.0  0.3  29700  1508 ?        Ss   19:40   0:00 avahi-daemon: running [rintintin.local]
avahi     5714  0.0  0.1  29576   504 ?        Ss   19:40   0:00 avahi-daemon: chroot helper
root      5743  0.0  0.5  72408  2396 ?        Ss   19:40   0:00 /usr/sbin/cupsd
root      5911  0.0  0.2   6268   944 ?        Ss   19:40   0:00 /usr/sbin/dhcdbd --system
root      5930  0.0  0.2  17756  1284 ?        Ss   19:40   0:00 /usr/sbin/hcid -x -s
root      5940  0.0  0.0      0     0 ?        S<   19:40   0:00 [btaddconn]
root      5941  0.0  0.0      0     0 ?        S<   19:40   0:00 [btdelconn]
root      5954  0.0  0.0      0     0 ?        S<   19:40   0:00 [krfcommd]
root      5957  0.0  0.2  17576  1172 ?        S    19:40   0:00 /usr/lib/bluetooth/bluetoothd-service-input
root      5970  0.0  0.3  17652  1388 ?        S    19:40   0:00 /usr/lib/bluetooth/bluetoothd-service-audio
mpd       5995  0.0  0.4  97348  2076 ?        S    19:40   0:00 /usr/bin/mpd /etc/mpd.conf
root      6037  0.0  0.2  12280   912 ?        Ss   19:40   0:00 /usr/sbin/anacron -s
daemon    6051  0.0  0.0  16424   432 ?        Ss   19:40   0:00 /usr/sbin/atd
root      6067  0.0  0.2  18612   976 ?        Ss   19:40   0:00 /usr/sbin/cron
dhcp      6090  0.0  0.3  15104  1460 ?        S    19:40   0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth1.leases -pf /var/run/dhclient.eth1.pid -q -e dhc_dbus=31 -d eth1
root      6123  0.0  0.5  59212  2572 ?        Ss   19:40   0:00 /usr/sbin/apache
www-data  6126  0.0  0.2  59212   980 ?        S    19:40   0:00 /usr/sbin/apache
www-data  6130  0.0  0.2  59212   980 ?        S    19:40   0:00 /usr/sbin/apache
www-data  6133  0.0  0.2  59212   980 ?        S    19:40   0:00 /usr/sbin/apache
www-data  6134  0.0  0.2  59212   980 ?        S    19:40   0:00 /usr/sbin/apache
www-data  6135  0.0  0.2  59212   980 ?        S    19:40   0:00 /usr/sbin/apache
root      6237  0.0  1.1  96376  5240 ?        S    19:41   0:00 /usr/bin/timidity -Os -iAD
root      6256  0.0  0.1   3860   588 tty1     Ss+  19:41   0:00 /sbin/getty 38400 tty1
bcrowell  6302  0.1  1.2  43584  5680 ?        S    19:41   0:00 /usr/lib/libgconf2-4/gconfd-2 4
bcrowell  6304  0.0  0.5  62040  2280 ?        S    19:41   0:00 /usr/bin/gnome-keyring-daemon -d --login
bcrowell  6306  0.0  1.2  66008  5576 ?        Ss   19:41   0:00 /usr/bin/fluxbox
bcrowell  6428  0.0  1.5 223300  6952 ?        Ss   19:41   0:00 /usr/bin/seahorse-agent --execute /usr/bin/startfluxbox
bcrowell  6448  0.0  1.0 111876  4492 ?        Ss   19:41   0:00 aterm -sr -sl 2000 -geometry 180x71 -bg white -fg black
bcrowell  6449  0.0  0.5  19436  2316 pts/0    Ss   19:41   0:00 bash
bcrowell  6464  0.0  0.5  44368  2552 pts/0    S+   19:42   0:00 ssh bcrowell@lightandmatter.com
bcrowell  6467  5.1 21.9 514536 98300 ?        Rsl  19:43   0:17 /usr/lib/firefox-3.0b5/firefox
bcrowell  6481  0.0  1.0 111876  4484 ?        Ss   19:43   0:00 aterm -sr -sl 2000 -geometry 180x71 -bg white -fg black
bcrowell  6482  0.0  0.5  19436  2316 pts/1    Ss+  19:43   0:00 bash
root      6493  0.0  0.1   3940   552 ?        S    19:45   0:00 /bin/sh -c nice run-parts --report /etc/cron.daily
root      6494  0.0  0.1   3976   712 ?        SN   19:45   0:00 run-parts --report /etc/cron.daily
root      6505  0.0  0.1   3940   604 ?        SN   19:45   0:00 /bin/sh /etc/cron.daily/apt
root      6526  0.0  0.1   8104   596 ?        SN   19:46   0:00 sleep 806
bcrowell  6529  0.8  1.0 111876  4480 ?        Ss   19:48   0:00 aterm -sr -sl 2000 -geometry 180x71 -bg white -fg black
bcrowell  6530  0.0  0.5  19436  2316 pts/2    Ss   19:48   0:00 bash
root      6535  0.0  0.2  32476  1312 pts/2    S    19:48   0:00 su
root      6537  0.0  0.4  18940  2088 pts/2    S    19:48   0:00 bash
root      6547  0.0  0.2  15060  1088 pts/2    R+   19:48   0:00 ps aux
```

---

