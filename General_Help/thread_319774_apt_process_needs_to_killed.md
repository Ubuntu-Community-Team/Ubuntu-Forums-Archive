---
title: "apt process needs to killed"
date: 2006-12-16
forum: General Help
---

### Post by newsman on 2006-12-16
I was running update for apt,, but i got error for some broken packages and it exited..i thought,, no problem, i will just run it again and tell it not to update that one package that was broken...

but now even after i reset and try use adept or update icon, i get error saying "Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one."

But i am not using any apps,...

When i do ps aux in terminal i get

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.4  0.1   1692   544 ?        Ss   12:17   0:01 /sbin/init spla
root         2  0.0  0.0      0     0 ?        S    12:17   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   12:17   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    12:17   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S<   12:17   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        S<   12:17   0:00 [khelper]
root         7  0.0  0.0      0     0 ?        S<   12:17   0:00 [kthread]
root        28  0.0  0.0      0     0 ?        S<   12:17   0:00 [kblockd/0]
root        29  0.0  0.0      0     0 ?        S<   12:17   0:00 [kacpid]
root       127  0.0  0.0      0     0 ?        S<   12:17   0:00 [kseriod]
root       147  0.0  0.0      0     0 ?        S    12:17   0:00 [pdflush]
root       148  0.0  0.0      0     0 ?        S    12:17   0:00 [pdflush]
root       149  0.0  0.0      0     0 ?        S<   12:17   0:00 [kswapd0]
root       150  0.0  0.0      0     0 ?        S<   12:17   0:00 [aio/0]
root      1651  0.0  0.0      0     0 ?        S<   12:17   0:00 [ksuspend_usbd]
root      1652  0.0  0.0      0     0 ?        S<   12:17   0:00 [khubd]
root      1828  0.0  0.0      0     0 ?        S<   12:17   0:00 [ata/0]
root      1829  0.0  0.0      0     0 ?        S<   12:17   0:00 [ata_aux]
root      1972  0.0  0.0      0     0 ?        S<   12:17   0:00 [kjournald]
root      2017  0.0  0.1   1664   552 ?        Ss   12:17   0:00 /sbin/logd
root      2169  0.0  0.2   2788  1192 ?        S<s  12:18   0:00 /sbin/udevd --d
root      3052  0.0  0.0      0     0 ?        S<   12:18   0:00 [pccardd]
root      3062  0.0  0.0      0     0 ?        S<   12:18   0:00 [ipw2200/0]
root      3073  0.0  0.0      0     0 ?        S<   12:18   0:00 [kpsmoused]
root      3511  0.0  0.0      0     0 ?        S<   12:18   0:00 [kjournald]
root      3513  0.0  0.0      0     0 ?        S<   12:18   0:00 [kjournald]
root      3890  0.0  0.0   1656   504 tty1     Ss+  12:18   0:00 /sbin/getty 384
root      3891  0.0  0.0   1660   504 tty2     Ss+  12:18   0:00 /sbin/getty 384
root      3892  0.0  0.0   1656   504 tty3     Ss+  12:18   0:00 /sbin/getty 384
root      3893  0.0  0.0   1656   504 tty4     Ss+  12:18   0:00 /sbin/getty 384
root      3894  0.0  0.1   1660   508 tty5     Ss+  12:18   0:00 /sbin/getty 384
root      3895  0.0  0.1   1660   508 tty6     Ss+  12:18   0:00 /sbin/getty 384
root      4089  0.0  0.2   2264  1176 ?        Ss   12:18   0:00 /usr/sbin/acpid
root      4180  0.0  0.1   1708   656 ?        Ss   12:18   0:00 /sbin/syslogd
root      4207  0.0  0.1   1800   520 ?        Ss   12:18   0:00 /bin/dd bs 1 if
klog      4209  0.0  0.2   2484  1352 ?        Ss   12:18   0:00 /sbin/klogd -P
cupsys    4241  0.0  0.3   4648  1800 ?        Ss   12:18   0:00 /usr/sbin/cupsd
root      4259  0.0  0.1   5028   792 ?        Ss   12:18   0:00 /usr/sbin/hpiod
hplip     4262  0.0  0.9   9824  4888 ?        S    12:18   0:00 python /usr/sbi
root      4309  0.0  0.4   5692  2268 ?        Ss   12:18   0:00 /usr/sbin/apt-i
103       4329  0.0  0.1   2712  1004 ?        Ss   12:18   0:00 /usr/bin/dbus-d
106       4345  0.3  1.7  10516  8908 ?        Ss   12:18   0:00 /usr/sbin/hald
root      4346  0.0  0.2   2996  1100 ?        S    12:18   0:00 hald-runner
106       4352  0.0  0.1   2108   932 ?        S    12:18   0:00 hald-addon-acpi
root      4353  0.0  0.2   3048  1032 ?        S    12:18   0:00 /usr/lib/hal/ha
106       4363  0.0  0.1   2104   900 ?        S    12:18   0:00 hald-addon-keyb
106       4379  0.0  0.1   2104   904 ?        S    12:18   0:00 hald-addon-stor
root      4400  0.0  0.1   1944   852 ?        Ss   12:18   0:00 /usr/sbin/dhcdb
root      4417  0.0  0.4  20496  2076 ?        Ssl  12:18   0:00 /usr/sbin/Netwo
avahi     4441  0.0  0.2   2664  1360 ?        Ss   12:18   0:00 avahi-daemon: r
avahi     4442  0.0  0.0   2664   472 ?        Ss   12:18   0:00 avahi-daemon: c
root      4455  0.0  0.2   3040  1280 ?        Ss   12:18   0:00 /usr/sbin/Netwo
dhcp      4474  0.0  0.2   2460  1184 ?        S    12:18   0:00 /sbin/dhclient
root      4498  0.0  0.0      0     0 ?        S<   12:18   0:00 [kondemand/0]
root      4541  0.0  0.1   2052   784 ?        Ss   12:18   0:00 /usr/sbin/hcid
root      4545  0.0  0.1   1724   516 ?        Ss   12:18   0:00 /usr/sbin/sdpd
root      4563  0.0  0.0      0     0 ?        S<   12:18   0:00 [krfcommd]
daemon    4598  0.0  0.0   1920   428 ?        Ss   12:18   0:00 /usr/sbin/atd
root      4612  0.0  0.1   2284   900 ?        Ss   12:18   0:00 /usr/sbin/cron
root      4718  0.0  0.1   2748   656 ?        Ss   12:18   0:00 /usr/bin/kdm
root      4737  3.4  3.7  25092 19044 tty7     Ss+  12:18   0:08 /usr/bin/X -br
dhcp      4922  0.0  0.1   2460   748 ?        S<s  12:18   0:00 dhclient3 -pf /
root      5113  0.0  0.2   3744  1440 ?        S    12:19   0:00 -:0
umar      5121  0.0  0.1   1724   532 ?        Ss   12:19   0:00 /bin/sh /usr/bi
umar      5166  0.0  0.1   4220   632 ?        Ss   12:19   0:00 /usr/bin/ssh-ag
umar      5169  0.0  0.1   2512   628 ?        S    12:19   0:00 /usr/bin/dbus-l
umar      5170  0.0  0.1   2712   528 ?        Ss   12:19   0:00 /usr/bin/dbus-d
root      5200  0.0  0.0   1508   140 ?        S    12:19   0:00 start_kdeinit -
umar      5201  0.0  1.4  25400  7436 ?        Ss   12:19   0:00 kdeinit Running
umar      5204  0.0  0.6  25032  3132 ?        S    12:19   0:00 dcopserver [kde
umar      5207  0.0  1.6  26792  8532 ?        S    12:19   0:00 klauncher [kdei
umar      5209  0.2  2.9  31044 14920 ?        S    12:19   0:00 kded [kdeinit]
umar      5214  0.0  0.0   1640   360 ?        S    12:19   0:00 kwrapper ksmser
umar      5216  0.0  2.1  27660 11056 ?        S    12:19   0:00 ksmserver [kdei
umar      5217  0.3  2.7  29716 14208 ?        S    12:19   0:00 kwin [kdeinit]
umar      5219  0.5  3.1  30240 15952 ?        S    12:19   0:00 kdesktop [kdein
umar      5221  0.0  1.5  25796  8012 ?        S    12:19   0:00 kio_file [kdein
umar      5222  1.7  5.2  43868 26592 ?        S    12:19   0:02 kicker [kdeinit
umar      5223  0.0  1.6  26908  8148 ?        S    12:19   0:00 kio_file [kdein
umar      5224  0.0  1.6  26908  8148 ?        S    12:19   0:00 kio_file [kdein
umar      5225  0.0  1.6  26908  8148 ?        S    12:19   0:00 kio_file [kdein
umar      5226  0.0  1.6  26908  8148 ?        S    12:19   0:00 kio_file [kdein
umar      5227  0.0  1.6  26908  8148 ?        S    12:19   0:00 kio_file [kdein
umar      5229  0.1  2.9  30392 15180 ?        S    12:19   0:00 kio_uiserver [k
umar      5230  0.0  1.4  26868  7388 ?        S    12:19   0:00 kio_system [kde
umar      5231  0.0  1.6  26912  8148 ?        S    12:19   0:00 kio_trash [kdei
umar      5244  0.6  1.3  20096  6612 ?        S    12:19   0:00 /usr/bin/artsd
umar      5248  0.0  2.0  27272 10604 ?        S    12:19   0:00 kaccess [kdeini
umar      5251  0.1  3.0  30844 15724 ?        S    12:19   0:00 kmix [kdeinit]
umar      5254  0.1  3.3  29160 16988 ?        S    12:19   0:00 katapult -sessi
umar      5258  0.0  0.4   7996  2272 ?        S    12:19   0:00 aspell -a -S -C
umar      5263  0.3  4.1  57080 21296 ?        S    12:19   0:00 /usr/bin/python
umar      5264  0.0  2.6  34768 13672 ?        S    12:19   0:00 knotify [kdeini
umar      5265  0.2  3.9  39248 20088 ?        S    12:19   0:00 konqueror [kdei
umar      5268  1.7  3.0  30728 15432 ?        S    12:19   0:02 adept_notifier
umar      5269  0.0  0.1   1840   624 ?        S    12:19   0:00 /usr/bin/passke
umar      5270  0.2  3.9  39248 20088 ?        S    12:19   0:00 konqueror [kdei
umar      5271  0.0  2.6  28488 13524 ?        S    12:19   0:00 /usr/bin/kbluet
umar      5273  0.0  2.5  28484 12724 ?        S    12:19   0:00 klipper [kdeini
umar      5276  0.0  0.5  17028  2744 ?        S    12:19   0:00 /usr/bin/kdesud
umar      5347 13.2  9.3 192780 47248 ?        Sl   12:21   0:10 /usr/lib/firefo
umar      5356  0.0  0.4   5036  2316 ?        S    12:21   0:00 /usr/lib/libgco
umar      5381  0.0  1.5  25796  8008 ?        S    12:21   0:00 kio_file [kdein
umar      5406  6.3  3.2  33068 16496 ?        R    12:22   0:00 konsole [kdeini
umar      5409  4.0  0.6   5844  3228 pts/1    Ss   12:22   0:00 /bin/bash
umar      5425  1.0  0.1   2568   988 pts/1    R+   12:22   0:00 ps aux


and if do sudo ps aux i get the following:

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.2  0.1   1692   544 ?        Ss   12:17   0:01 /sbin/init spla
root         2  0.0  0.0      0     0 ?        S    12:17   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   12:17   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    12:17   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S<   12:17   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        S<   12:17   0:00 [khelper]
root         7  0.0  0.0      0     0 ?        S<   12:17   0:00 [kthread]
root        28  0.0  0.0      0     0 ?        S<   12:17   0:00 [kblockd/0]
root        29  0.0  0.0      0     0 ?        S<   12:17   0:00 [kacpid]
root       127  0.0  0.0      0     0 ?        S<   12:17   0:00 [kseriod]
root       147  0.0  0.0      0     0 ?        S    12:17   0:00 [pdflush]
root       148  0.0  0.0      0     0 ?        S    12:17   0:00 [pdflush]
root       149  0.0  0.0      0     0 ?        S<   12:17   0:00 [kswapd0]
root       150  0.0  0.0      0     0 ?        S<   12:17   0:00 [aio/0]
root      1651  0.0  0.0      0     0 ?        S<   12:17   0:00 [ksuspend_usbd]
root      1652  0.0  0.0      0     0 ?        S<   12:17   0:00 [khubd]
root      1828  0.0  0.0      0     0 ?        S<   12:17   0:00 [ata/0]
root      1829  0.0  0.0      0     0 ?        S<   12:17   0:00 [ata_aux]
root      1972  0.0  0.0      0     0 ?        S<   12:17   0:00 [kjournald]
root      2017  0.0  0.1   1664   552 ?        Ss   12:17   0:00 /sbin/logd
root      2169  0.0  0.2   2788  1192 ?        S<s  12:18   0:00 /sbin/udevd --d
root      3052  0.0  0.0      0     0 ?        S<   12:18   0:00 [pccardd]
root      3062  0.0  0.0      0     0 ?        S<   12:18   0:00 [ipw2200/0]
root      3073  0.0  0.0      0     0 ?        S<   12:18   0:00 [kpsmoused]
root      3511  0.0  0.0      0     0 ?        S<   12:18   0:00 [kjournald]
root      3513  0.0  0.0      0     0 ?        S<   12:18   0:00 [kjournald]
root      3890  0.0  0.0   1656   504 tty1     Ss+  12:18   0:00 /sbin/getty 384
root      3891  0.0  0.0   1660   504 tty2     Ss+  12:18   0:00 /sbin/getty 384
root      3892  0.0  0.0   1656   504 tty3     Ss+  12:18   0:00 /sbin/getty 384
root      3893  0.0  0.0   1656   504 tty4     Ss+  12:18   0:00 /sbin/getty 384
root      3894  0.0  0.1   1660   508 tty5     Ss+  12:18   0:00 /sbin/getty 384
root      3895  0.0  0.1   1660   508 tty6     Ss+  12:18   0:00 /sbin/getty 384
root      4089  0.0  0.2   2264  1176 ?        Ss   12:18   0:00 /usr/sbin/acpid
root      4180  0.0  0.1   1708   656 ?        Rs   12:18   0:00 /sbin/syslogd
root      4207  0.0  0.1   1800   520 ?        Ss   12:18   0:00 /bin/dd bs 1 if
klog      4209  0.0  0.2   2484  1352 ?        Ss   12:18   0:00 /sbin/klogd -P
cupsys    4241  0.0  0.3   4648  1800 ?        Ss   12:18   0:00 /usr/sbin/cupsd
root      4259  0.0  0.1   5028   792 ?        Ss   12:18   0:00 /usr/sbin/hpiod
hplip     4262  0.0  0.9   9824  4888 ?        S    12:18   0:00 python /usr/sbi
root      4309  0.0  0.4   5692  2268 ?        Ss   12:18   0:00 /usr/sbin/apt-i
103       4329  0.0  0.1   2712  1004 ?        Ss   12:18   0:00 /usr/bin/dbus-d
106       4345  0.2  1.7  10516  8908 ?        Ss   12:18   0:00 /usr/sbin/hald
root      4346  0.0  0.2   2996  1100 ?        S    12:18   0:00 hald-runner
106       4352  0.0  0.1   2108   932 ?        S    12:18   0:00 hald-addon-acpi
root      4353  0.0  0.2   3048  1032 ?        S    12:18   0:00 /usr/lib/hal/ha
106       4363  0.0  0.1   2104   900 ?        S    12:18   0:00 hald-addon-keyb
106       4379  0.0  0.1   2104   904 ?        S    12:18   0:00 hald-addon-stor
root      4400  0.0  0.1   1944   852 ?        Ss   12:18   0:00 /usr/sbin/dhcdb
root      4417  0.0  0.4  20496  2076 ?        Ssl  12:18   0:00 /usr/sbin/Netwo
avahi     4441  0.0  0.2   2664  1360 ?        Ss   12:18   0:00 avahi-daemon: r
avahi     4442  0.0  0.0   2664   472 ?        Ss   12:18   0:00 avahi-daemon: c
root      4455  0.0  0.2   3040  1280 ?        Ss   12:18   0:00 /usr/sbin/Netwo
dhcp      4474  0.0  0.2   2460  1184 ?        S    12:18   0:00 /sbin/dhclient
root      4498  0.0  0.0      0     0 ?        S<   12:18   0:00 [kondemand/0]
root      4541  0.0  0.1   2052   784 ?        Ss   12:18   0:00 /usr/sbin/hcid
root      4545  0.0  0.1   1724   516 ?        Ss   12:18   0:00 /usr/sbin/sdpd
root      4563  0.0  0.0      0     0 ?        S<   12:18   0:00 [krfcommd]
daemon    4598  0.0  0.0   1920   428 ?        Ss   12:18   0:00 /usr/sbin/atd
root      4612  0.0  0.1   2284   900 ?        Ss   12:18   0:00 /usr/sbin/cron
root      4718  0.0  0.1   2748   656 ?        Ss   12:18   0:00 /usr/bin/kdm
root      4737  3.4  3.8  25484 19336 tty7     Rs+  12:18   0:16 /usr/bin/X -br
dhcp      4922  0.0  0.1   2460   748 ?        S<s  12:18   0:00 dhclient3 -pf /
root      5113  0.0  0.2   3744  1440 ?        S    12:19   0:00 -:0
umar      5121  0.0  0.1   1724   532 ?        Ss   12:19   0:00 /bin/sh /usr/bi
umar      5166  0.0  0.1   4220   632 ?        Ss   12:19   0:00 /usr/bin/ssh-ag
umar      5169  0.0  0.1   2512   628 ?        S    12:19   0:00 /usr/bin/dbus-l
umar      5170  0.0  0.1   2712   528 ?        Ss   12:19   0:00 /usr/bin/dbus-d
root      5200  0.0  0.0   1508   140 ?        S    12:19   0:00 start_kdeinit -
umar      5201  0.0  1.4  25400  7436 ?        Ss   12:19   0:00 kdeinit Running
umar      5204  0.0  0.6  25032  3132 ?        S    12:19   0:00 dcopserver [kde
umar      5207  0.0  1.6  26928  8608 ?        S    12:19   0:00 klauncher [kdei
umar      5209  0.0  2.9  31044 14920 ?        S    12:19   0:00 kded [kdeinit]
umar      5214  0.0  0.0   1640   360 ?        S    12:19   0:00 kwrapper ksmser
umar      5216  0.0  2.1  27660 11056 ?        S    12:19   0:00 ksmserver [kdei
umar      5217  0.3  2.8  29716 14256 ?        S    12:19   0:01 kwin [kdeinit]
umar      5219  0.2  3.1  30216 15928 ?        S    12:19   0:01 kdesktop [kdein
umar      5222  0.7  5.2  43808 26592 ?        S    12:19   0:02 kicker [kdeinit
umar      5225  0.0  1.6  26908  8148 ?        S    12:19   0:00 kio_file [kdein
umar      5229  0.0  2.9  30392 15180 ?        S    12:19   0:00 kio_uiserver [k
umar      5244  0.2  1.3  20096  6612 ?        S    12:19   0:00 /usr/bin/artsd
umar      5248  0.0  2.0  27272 10604 ?        S    12:19   0:00 kaccess [kdeini
umar      5251  0.0  3.0  30844 15724 ?        S    12:19   0:00 kmix [kdeinit]
umar      5254  0.0  3.3  29160 16988 ?        S    12:19   0:00 katapult -sessi
umar      5258  0.0  0.4   7996  2272 ?        S    12:19   0:00 aspell -a -S -C
umar      5263  0.1  4.2  57080 21316 ?        S    12:19   0:00 /usr/bin/python
umar      5264  0.0  2.6  34768 13672 ?        S    12:19   0:00 knotify [kdeini
umar      5265  0.1  3.9  39248 20088 ?        S    12:19   0:00 konqueror [kdei
umar      5268  1.3  3.1  31548 16184 ?        S    12:19   0:05 adept_notifier
umar      5269  0.0  0.1   1840   624 ?        S    12:19   0:00 /usr/bin/passke
umar      5270  0.1  3.9  39248 20088 ?        S    12:19   0:00 konqueror [kdei
umar      5271  0.0  2.6  28488 13524 ?        S    12:19   0:00 /usr/bin/kbluet
umar      5273  0.0  2.5  28484 12744 ?        S    12:19   0:00 klipper [kdeini
umar      5276  0.0  0.5  17028  2976 ?        S    12:19   0:00 /usr/bin/kdesud
umar      5347  4.9 10.3 173244 52688 ?        Sl   12:21   0:15 /usr/lib/firefo
umar      5356  0.0  0.4   5036  2316 ?        S    12:21   0:00 /usr/lib/libgco
umar      5381  0.0  1.5  25796  8008 ?        S    12:21   0:00 kio_file [kdein
umar      5406  0.5  3.3  33380 17132 ?        R    12:22   0:01 konsole [kdeini
umar      5409  0.0  0.6   5844  3236 pts/1    Ss   12:22   0:00 /bin/bash
umar      5464  0.1  2.4  26456 12568 ?        S    12:24   0:00 kdesu -u root -
root      5467  0.0  0.0   1516   316 pts/2    Ss+  12:24   0:00 /usr/bin/kdesu_
root      5470  0.0  0.2   2632  1028 pts/3    Ss+  12:24   0:00 /usr/bin/sudo -
root      5549  1.0  0.1   2572   992 pts/1    R+   12:26   0:00 ps aux





where is adept application that I am running????

---

### Post by newsman on 2006-12-16
i just rebooted after the night... and still it claims i am running some adept based app, but where???

The following is output of sudo ps aux,,, 

[PHP]umar@umar-laptop:~$ sudo ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.1   1688   540 ?        Ss   13:54   0:01 /sbin/init splash
root         2  0.0  0.0      0     0 ?        S    13:54   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   13:54   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    13:54   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S<   13:54   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        S<   13:54   0:00 [khelper]
root         7  0.0  0.0      0     0 ?        S<   13:54   0:00 [kthread]
root        28  0.0  0.0      0     0 ?        S<   13:54   0:00 [kblockd/0]
root        29  0.0  0.0      0     0 ?        S<   13:54   0:00 [kacpid]
root       127  0.0  0.0      0     0 ?        S<   13:54   0:00 [kseriod]
root       147  0.0  0.0      0     0 ?        S    13:54   0:00 [pdflush]
root       148  0.0  0.0      0     0 ?        S    13:54   0:00 [pdflush]
root       149  0.0  0.0      0     0 ?        S<   13:54   0:00 [kswapd0]
root       150  0.0  0.0      0     0 ?        S<   13:54   0:00 [aio/0]
root      1652  0.0  0.0      0     0 ?        S<   13:54   0:00 [ksuspend_usbd]
root      1653  0.0  0.0      0     0 ?        S<   13:54   0:00 [khubd]
root      1832  0.0  0.0      0     0 ?        S<   13:54   0:00 [ata/0]
root      1833  0.0  0.0      0     0 ?        S<   13:54   0:00 [ata_aux]
root      1974  0.0  0.0      0     0 ?        S<   13:54   0:00 [kjournald]
root      2019  0.0  0.1   1668   556 ?        Ss   13:54   0:00 /sbin/logd
root      2171  0.0  0.2   2792  1200 ?        S<s  13:54   0:00 /sbin/udevd --daemon
root      3068  0.0  0.0      0     0 ?        S<   13:54   0:00 [kpsmoused]
root      3081  0.0  0.0      0     0 ?        S<   13:54   0:00 [pccardd]
root      3083  0.0  0.0      0     0 ?        S<   13:54   0:00 [ipw2200/0]
dhcp      3482  0.0  0.1   2460   568 ?        S<s  13:54   0:00 dhclient3 -pf /var/run/dhclient.eth1.pid -lf /var/lib/dhcp3/dhclient.eth1.lea
root      3538  0.0  0.0      0     0 ?        S<   13:54   0:00 [kjournald]
root      3540  0.0  0.0      0     0 ?        S<   13:54   0:00 [kjournald]
root      3917  0.0  0.1   1660   508 tty1     Ss+  13:54   0:00 /sbin/getty 38400 tty1
root      3918  0.0  0.1   1660   508 tty2     Ss+  13:54   0:00 /sbin/getty 38400 tty2
root      3919  0.0  0.1   1660   508 tty3     Ss+  13:54   0:00 /sbin/getty 38400 tty3
root      3920  0.0  0.1   1660   508 tty4     Ss+  13:54   0:00 /sbin/getty 38400 tty4
root      3921  0.0  0.0   1656   500 tty5     Ss+  13:54   0:00 /sbin/getty 38400 tty5
root      3922  0.0  0.0   1656   504 tty6     Ss+  13:54   0:00 /sbin/getty 38400 tty6
root      4118  0.0  0.2   2268  1168 ?        Ss   13:54   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4209  0.0  0.1   1712   656 ?        Rs   13:54   0:00 /sbin/syslogd
root      4236  0.0  0.1   1804   524 ?        Ss   13:54   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4238  0.0  0.2   2480  1348 ?        Ss   13:54   0:00 /sbin/klogd -P /var/run/klogd/kmsg
cupsys    4270  0.0  0.3   4656  1924 ?        Ss   13:54   0:00 /usr/sbin/cupsd
root      4288  0.0  0.1   5028   792 ?        Ss   13:54   0:00 /usr/sbin/hpiod
hplip     4291  0.0  0.9   9832  4896 ?        S    13:54   0:00 python /usr/sbin/hpssd
root      4338  0.0  0.4   5688  2268 ?        Ss   13:54   0:00 /usr/sbin/apt-index-watcher watch --syslog
103       4356  0.0  0.1   2716  1012 ?        Ss   13:54   0:00 /usr/bin/dbus-daemon --system
106       4374  0.1  1.7  10512  8904 ?        Ss   13:54   0:01 /usr/sbin/hald
root      4375  0.0  0.2   2996  1100 ?        S    13:54   0:00 hald-runner
106       4381  0.0  0.1   2108   888 ?        S    13:54   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      4382  0.0  0.2   3048  1036 ?        S    13:54   0:00 /usr/lib/hal/hald-addon-cpufreq
106       4392  0.0  0.1   2108   904 ?        S    13:54   0:00 hald-addon-keyboard: listening on /dev/input/event0
106       4402  0.0  0.1   2108   904 ?        S    13:54   0:00 hald-addon-storage: polling /dev/hdb
root      4423  0.0  0.1   1944   844 ?        Ss   13:54   0:00 /usr/sbin/dhcdbd --system
root      4440  0.0  0.4  20496  2072 ?        Ssl  13:54   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pi
avahi     4459  0.0  0.2   2660  1344 ?        Ss   13:54   0:00 avahi-daemon: registering [umar-laptop.local]
avahi     4460  0.0  0.0   2660   468 ?        Ss   13:54   0:00 avahi-daemon: chroot helper
root      4478  0.0  0.2   3040  1280 ?        Ss   13:54   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/Network
dhcp      4497  0.0  0.2   2460  1180 ?        S    13:54   0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth0.leases -pf /var/run/dhclie
root      4521  0.0  0.0      0     0 ?        S<   13:54   0:00 [kondemand/0]
root      4564  0.0  0.1   2052   784 ?        Ss   13:54   0:00 /usr/sbin/hcid -x
root      4572  0.0  0.1   1728   520 ?        Ss   13:54   0:00 /usr/sbin/sdpd
root      4582  0.0  0.0      0     0 ?        S<   13:54   0:00 [krfcommd]
daemon    4616  0.0  0.0   1916   424 ?        Ss   13:54   0:00 /usr/sbin/atd
root      4630  0.0  0.1   2284   900 ?        Ss   13:54   0:00 /usr/sbin/cron
root      4766  0.0  0.1   2744   668 ?        Ss   13:54   0:00 /usr/bin/kdm
root      4785  2.3  4.5  29056 23084 tty7     Ss+  13:54   0:25 /usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-GMfpPt
root      5652  0.0  0.2   3740  1444 ?        S    14:01   0:00 -:0
umar      5662  0.0  0.1   1720   528 ?        Ss   14:02   0:00 /bin/sh /usr/bin/x-session-manager
umar      5707  0.0  0.1   4220   636 ?        Ss   14:02   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
umar      5710  0.0  0.1   2712   528 ?        Ss   14:02   0:00 /usr/bin/dbus-daemon --fork --print-pid 4 --print-address 7 --session
umar      5711  0.0  0.1   2508   628 ?        S    14:02   0:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
root      5741  0.0  0.0   1508   140 ?        S    14:02   0:00 start_kdeinit --new-startup +kcminit_startup
umar      5742  0.0  1.4  25400  7432 ?        Ss   14:02   0:00 kdeinit Running...
umar      5745  0.0  0.6  25032  3136 ?        S    14:02   0:00 dcopserver [kdeinit] --nosid
umar      5748  0.0  1.6  26924  8580 ?        S    14:02   0:00 klauncher [kdeinit] --new-startup
umar      5750  0.0  2.9  31044 14924 ?        S    14:02   0:00 kded [kdeinit] --new-startup
umar      5755  0.0  0.0   1640   368 ?        S    14:02   0:00 kwrapper ksmserver
umar      5757  0.0  2.1  27660 11052 ?        S    14:02   0:00 ksmserver [kdeinit]
umar      5760  0.1  2.8  29752 14248 ?        S    14:02   0:00 kwin [kdeinit] -session 10116148132e2000116588518100000052100000_1166277710_7
umar      5762  0.1  3.1  30216 15928 ?        S    14:02   0:01 kdesktop [kdeinit]
umar      5764  0.2  3.6  33768 18656 ?        S    14:02   0:01 kicker [kdeinit]
umar      5767  0.0  1.6  26908  8144 ?        S    14:02   0:00 kio_file [kdeinit] file /tmp/ksocket-umar/klauncherE9ha1b.slave-socket /tmp/k
umar      5772  0.0  3.0  30392 15264 ?        S    14:02   0:00 kio_uiserver [kdeinit]
umar      5785  0.4  1.2  20008  6588 ?        S    14:02   0:02 /usr/bin/artsd -F 10 -S 4096 -s 60 -m artsmessage -c drkonqi -l 3 -f
umar      5787  0.0  2.0  27272 10608 ?        S    14:02   0:00 kaccess [kdeinit]
umar      5790  0.0  3.0  30844 15716 ?        S    14:02   0:00 kmix [kdeinit] -session 10d8cecf96000111065458100000063760027_1166277710_6834
umar      5791  0.0  3.3  29156 16996 ?        S    14:02   0:00 katapult -session 10d9d39668000112680660600000081280032_1166277710_683721
umar      5795  0.0  0.4   7992  2272 ?        S    14:02   0:00 aspell -a -S -C -Tutf8 --encoding=utf-8
umar      5804  0.1  4.2  57092 21344 ?        S    14:02   0:00 /usr/bin/python /usr/share/python-support/kde-guidance/guidance-power-manager
umar      5807  0.0  2.7  34900 13720 ?        S    14:02   0:00 knotify [kdeinit]
umar      5808  0.0  3.9  39248 20080 ?        S    14:02   0:00 konqueror [kdeinit] --preload
umar      5815  0.0  3.9  39248 20080 ?        S    14:02   0:00 konqueror [kdeinit] --preload
umar      5816  0.0  0.1   1840   624 ?        S    14:02   0:00 /usr/bin/passkey-agent --default /usr/lib/kdebluetooth/kbluepin
umar      5817  0.0  2.6  28484 13516 ?        S    14:02   0:00 /usr/bin/kbluetoothd.real --dontforceshow
umar      5819  0.0  2.5  28500 12740 ?        S    14:02   0:00 klipper [kdeinit]
umar      5823  0.0  0.5  17032  2980 ?        S    14:02   0:00 /usr/bin/kdesud
umar      5915  5.2 12.0 180820 61140 ?        Sl   14:02   0:31 /usr/lib/firefox/firefox-bin
umar      5924  0.0  0.4   5036  2312 ?        S    14:02   0:00 /usr/lib/libgconf2-4/gconfd-2 13
umar      5968  0.2  3.3  33324 16860 ?        R    14:04   0:01 konsole [kdeinit]
umar      5969  0.0  0.6   5848  3248 pts/1    Ss   14:04   0:00 /bin/bash
root      6178  0.0  0.1   2568   988 pts/1    R+   14:12   0:00 ps aux
[/PHP]

---

### Post by newsman on 2006-12-16
started prodding the system via konsole terminal 

[PHP]umar@umar-laptop:~$ sudo apt-get jedit
E: Invalid operation jedit
umar@umar-laptop:~$ sudo apt-get install jedit
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
umar@umar-laptop:~$ sudo apt-get install ktechlab
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
umar@umar-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
umar@umar-laptop:~$ sudo dpkg --configure -a
umar@umar-laptop:~$ sudo dpkg --configure -a
Setting up mlterm-common (2.9.3-5) ...
Installing new version of config file /etc/mlterm/aafont ...
Installing new version of config file /etc/mlterm/main ...

Setting up python-lxml (1.1.2-1) ...

Setting up libboost-thread1.33.1 (1.33.1-9) ...

Setting up gdb (6.5.dfsg-2ubuntu3) ...

Setting up libgii1-target-x (1.0.1-3) ...
Setting up libjcode-pm-perl (2.06-1) ...
Setting up wpasupplicant (0.5.5-4) ...
Installing new version of config file /etc/wpa_supplicant/ifupdown.sh ...
Installing new version of config file /etc/wpa_supplicant/functions.sh ...

Setting up libdvdread3 (0.9.7-2) ...

Setting up freewnn-common (1.1.0+1.1.1-a021-1.1) ...
Setting up libboost-filesystem1.33.1 (1.33.1-9) ...

Setting up aplus-fsf-doc (4.20.2-5) ...

Setting up libnm-util0 (0.6.4-6ubuntu1) ...

Setting up liba52-0.7.4 (0.7.4-7) ...

Setting up tclxml (3.1-1) ...
Setting up libunicode-map-perl (0.112-10) ...
Setting up libswt3.2-gtk-jni (3.2.1-2ubuntu1) ...
Setting up mlterm (2.9.3-5) ...

Setting up ttf-sil-doulos (4.0.14-6) ...

Setting up motor-common (3.4.0-7) ...

Setting up ttf-sil-charis (4.002-7) ...

Setting up libart2 (1.4.2-34) ...

Setting up aplus-fsf (4.20.2-5) ...

Setting up liblucene-java (1.4.3.dfsg-1.2) ...
Setting up libotf0 (0.9.4-1) ...

Setting up libicu36 (3.6-2) ...

Setting up libmms0 (0.3-1) ...

Setting up libavifile-0.7c2 (0.7.44.20051021-2.2) ...

Setting up libopenal0a (0.0.8-3) ...

Setting up app-install-data (0.3.1) ...
Setting up skkdic (20061130-1) ...

Setting up libcompfaceg1 (1.5.2-4) ...

Setting up ttf-farsiweb (0.4.dfsg-5) ...

Setting up libsvga1 (1.4.3-24) ...
Installing new version of config file /etc/vga/libvga.config ...

Setting up gstreamer0.10-ffmpeg (0.10.2-0ubuntu1) ...
Setting up libxml++2.6c2a (2.17.1-0ubuntu2) ...

Setting up libtheora0 (0.0.0.alpha7.dfsg-1.1ubuntu1) ...

dpkg: dependency problems prevent configuration of scim-bridge:
 scim-bridge depends on scim-bridge-client-gtk; however:
  Package scim-bridge-client-gtk is not installed.
dpkg: error processing scim-bridge (--configure):
 dependency problems - leaving unconfigured
Setting up mined (2000.10-4) ...

Setting up unicode (0.8ubuntu1) ...
Setting up ttf-tmuni (0.0.20040806-1.2) ...
Regenerating fonts cache...            [/PHP]


Can anyone explain what just happened....i think last time i hung up on adept it was updating everything and left due to broken packages....

when in terminal i tried to do use adept it gave me a different error from GUI updater,,,, thus i tried that, i think it is continuing where it left off.... (from when it hung up)

at the end of it all it gave me this error and exited in terminal:

Setting up aplus-fsf-dev (4.20.2-5) ...
Errors were encountered while processing:
 scim-bridge


now i can run adept again.... but i think thats the reason why adept updater hung up as well... i think this may be a bug in the gui version which needs fixing... or is it just me...

---

### Post by taurus on 2006-12-16
Try

```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install jedit
```

---

### Post by newsman on 2006-12-16
it fixed it,,, but why didn't GUI work,,, its a bit strange... (re: my last post)

---

