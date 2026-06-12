---
title: "What's calling my system bell?"
date: 2006-10-11
forum: General Help
---

### Post by funkiwan on 2006-10-11
My machine specs: 
Linux kubuntu 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux
Qt: 3.3.6
KDE: 3.5.2
kde-config: 1.0

Occasionally my system bell will beep for no noticeable reason. I'd like to track down what program is actually causing it to do this. 

I should preface that the bell I'm talking about is not the "boop" noise I hear in konsole with tab completion. That gets piped through my soundcard and is the same as this:
# printf "\a"

What I'm talking about is the sound that gets piped out of the speaker on my computer. It's the same sound that I hear when I'm doing a type-ahead find in Firefox and encounter "Phrase not found". 

I'm not looking to turn this sound off. I'm just trying to determine what's making the sound. Presumably I'm meant to be alerted to something but I've yet to determine what the alert is. 

Thanks for your help,

Jonathan.

---

### Post by JonahRowley on 2006-10-11
Try looking around in /var/log (specifically /var/log/messages) for anything interesting.  I really don't know what could be beeping, maybe post a list of programs you're running?

---

### Post by funkiwan on 2006-10-12
> **JonahRowley said:**
> Try looking around in /var/log (specifically /var/log/messages) for anything interesting.  I really don't know what could be beeping, maybe post a list of programs you're running?

Thanks Jonah for responding. I had forgotten to post that immediately after hearing the beep I've checked, more than once, if any files have changed in /var/log with:
# sudo find /var/log -mmin -2

And got no matches. An ideal solution for me would be to figure out who is making the call to the beep so I can solve this problem if it occurs with other apps in the futre.

As for what's running? 

The short version:
Running currently is:
- konsole (several sessions). Note: I've checked console for messages and haven't seen any. And as mentioned previously, typical konsole alerts are piped through the soundcard.
- Gwenview (image viewer)
- Kontact
- Adobe Acrobat
- KCalc
- Thunderbird. Note: This is not caused by new mail. But perhaps by a new RSS feed entry? This is a good candidate b/c it's always open and it does make the noise with new mail. I've reconfigured the app to not automatically download new feeds. I'll see if that fixes it.
- vmplayer
- MyPasswordSafe
- Open Office
- Firefox
- Kate
- Gaim
- Kalarm
- Adept Updater

The long version:

# ps auxw

-- snip -- 
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   1564   532 ?        S    09:00   0:00 init [2]         
root         2  0.0  0.0      0     0 ?        SN   09:00   0:00 [ksoftirqd/0]
root         3  0.0  0.0      0     0 ?        S    09:00   0:00 [watchdog/0]
root         4  0.0  0.0      0     0 ?        S<   09:00   0:00 [events/0]
root         5  0.0  0.0      0     0 ?        S<   09:00   0:00 [khelper]
root         6  0.0  0.0      0     0 ?        S<   09:00   0:00 [kthread]
root         8  0.0  0.0      0     0 ?        S<   09:00   0:01 [kblockd/0]
root         9  0.0  0.0      0     0 ?        S<   09:00   0:00 [kacpid]
root       123  0.0  0.0      0     0 ?        S    09:00   0:00 [pdflush]
root       124  0.0  0.0      0     0 ?        S    09:00   0:00 [pdflush]
root       126  0.0  0.0      0     0 ?        S<   09:00   0:00 [aio/0]
root       125  0.0  0.0      0     0 ?        S    09:00   0:00 [kswapd0]
root       713  0.0  0.0      0     0 ?        S<   09:00   0:00 [kseriod]
root      1729  0.0  0.0      0     0 ?        S<   09:00   0:00 [ata/0]
root      1730  0.0  0.0      0     0 ?        S<   09:00   0:00 [ata_hotplug/0]
root      1733  0.0  0.0      0     0 ?        S<   09:00   0:00 [scsi_eh_0]
root      1734  0.0  0.0      0     0 ?        S<   09:00   0:00 [scsi_eh_1]
root      1735  0.0  0.0      0     0 ?        S<   09:00   0:00 [scsi_eh_2]
root      1816  0.0  0.0      0     0 ?        S<   09:00   0:00 [scsi_eh_3]
root      1817  0.0  0.0      0     0 ?        S<   09:00   0:00 [scsi_eh_4]
root      1907  0.0  0.0      0     0 ?        S<   09:00   0:00 [khubd]
root      1926  0.0  0.0      0     0 ?        S    09:00   0:00 [khpsbpkt]
root      1956  0.0  0.0      0     0 ?        S    09:00   0:00 [knodemgrd_0]
root      2201  0.0  0.0      0     0 ?        S<   09:00   0:01 [md0_raid1]
root      2280  0.0  0.0      0     0 ?        S    09:00   0:00 [kjournald]
root      2494  0.0  0.0   2432   920 ?        S<s  09:00   0:00 /sbin/udevd --daemon
root      3314  0.0  0.0      0     0 ?        S    09:00   0:00 [shpchpd_event]
root      4120  0.0  0.0   2156  1192 ?        Ss   09:00   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4239  0.0  0.0   1680   496 ?        Ss   09:00   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4241  0.0  0.0   2428  1352 ?        Ss   09:00   0:00 /sbin/klogd -P /var/run/klogd/kmsg
hplip     4266  0.0  0.0  12872   916 ?        Ssl  09:00   0:00 /usr/sbin/hpiod
hplip     4269  0.0  0.2   9408  4668 ?        S    09:00   0:00 python /usr/sbin/hpssd
104       4350  0.0  0.0   2196   832 ?        Ss   09:00   0:00 /usr/bin/dbus-daemon --system
108       4365  0.0  0.2   6980  5584 ?        Ss   09:00   0:01 /usr/sbin/hald
root      4366  0.0  0.0   2720   972 ?        S    09:00   0:00 hald-runner
108       4371  0.0  0.0   2004   792 ?        S    09:00   0:00 /usr/lib/hal/hald-addon-acpi
108       4426  0.0  0.0   2008   796 ?        S    09:00   0:00 /usr/lib/hal/hald-addon-keyboard
108       4443  0.0  0.0   2008   864 ?        S    09:00   0:03 /usr/lib/hal/hald-addon-storage
108       4444  0.0  0.0   2012   864 ?        S    09:00   0:03 /usr/lib/hal/hald-addon-storage
root      4474  0.0  0.1   5992  4000 ?        S    09:00   0:00 /usr/bin/perl -w /usr/sbin/ddclient -daemon 300 -syslog
112       4493  0.0  0.0   5256   976 ?        Ss   09:00   0:00 /usr/sbin/exim4 -bd -q30m
root      4519  0.0  0.0   2628  1300 ?        S    09:00   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     4559  0.1  1.3 121560 28320 ?        Sl   09:00   0:37 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      4560  0.0  0.0   1548   500 ?        S    09:00   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root      4633  0.0  0.0   5768  1416 ?        Ss   09:00   0:00 /usr/sbin/nmbd -D
root      4635  0.0  0.1   8528  2116 ?        Ss   09:00   0:00 /usr/sbin/smbd -D
root      4653  0.0  0.0   4768  1056 ?        Ss   09:00   0:00 /usr/sbin/sshd
root      4678  0.0  0.0   8528   956 ?        S    09:00   0:00 /usr/sbin/smbd -D
root      4685  0.0  0.0   1416   160 ?        S    09:00   0:00 /usr/bin/vmnet-bridge -d /var/run/vmnet-bridge-0.pid /dev/vmnet0 eth0
root      4699  0.0  0.0   1660   440 ?        Ss   09:00   0:00 /usr/bin/vmnet-natd -d /var/run/vmnet-natd-8.pid -m /var/run/vmnet-natd-8.mac -c /etc/vmware/vmnet8/nat/nat.conf
root      4767  0.0  0.0   1968   708 ?        Ss   09:00   0:00 hcid: processing events
root      4771  0.0  0.0   1620   460 ?        Ss   09:00   0:00 /usr/sbin/sdpd
root      4785  0.0  0.0      0     0 ?        S<   09:00   0:00 [krfcommd]
root      4799  0.0  0.0   1888   656 ?        Ss   09:00   0:00 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -s
daemon    4833  0.0  0.0   1804   400 ?        Ss   09:00   0:00 /usr/sbin/atd
root      4846  0.0  0.0   2116   840 ?        Ss   09:00   0:00 /usr/sbin/cron
root      5192  0.0  0.0   2744   636 ?        Ss   09:00   0:00 /usr/bin/kdm
root      5216  7.3  7.3 167072 152968 tty7    Ss+  09:00  38:22 /usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-hPRERV
root      5254  0.0  0.0   1560   492 tty1     Ss+  09:00   0:00 /sbin/getty 38400 tty1
root      5255  0.0  0.0   1564   492 tty2     Ss+  09:00   0:00 /sbin/getty 38400 tty2
root      5256  0.0  0.0   1560   492 tty3     Ss+  09:00   0:00 /sbin/getty 38400 tty3
root      5257  0.0  0.0   1564   492 tty4     Ss+  09:00   0:00 /sbin/getty 38400 tty4
root      5258  0.0  0.0   1560   492 tty5     Ss+  09:00   0:00 /sbin/getty 38400 tty5
root      5259  0.0  0.0   1564   496 tty6     Ss+  09:00   0:00 /sbin/getty 38400 tty6
root      5272  0.0  0.0   3676  1364 ?        S    09:00   0:00 -:0         
root      5292  0.0  0.0   1412   164 ?        S    09:00   0:00 /usr/bin/vmnet-netifup -d /var/run/vmnet-netifup-vmnet1.pid /dev/vmnet1 vmnet1
root      5298  0.0  0.0   1408   160 ?        S    09:00   0:00 /usr/bin/vmnet-netifup -d /var/run/vmnet-netifup-vmnet8.pid /dev/vmnet8 vmnet8
root      5317  0.0  0.0   1724   296 ?        Ss   09:00   0:00 /usr/bin/vmnet-dhcpd -cf /etc/vmware/vmnet1/dhcpd/dhcpd.conf -lf /etc/vmware/vmnet1/dhcpd/dhcpd.leases -pf /var/run/vmnet-dhcpd-vmnet1.pid vmnet1
root      5318  0.0  0.0   1724   304 ?        Ss   09:00   0:00 /usr/bin/vmnet-dhcpd -cf /etc/vmware/vmnet8/dhcpd/dhcpd.conf -lf /etc/vmware/vmnet8/dhcpd/dhcpd.leases -pf /var/run/vmnet-dhcpd-vmnet8.pid vmnet8
jgordon   5323  0.0  0.0   4180  1684 ?        Ss   09:01   0:00 /bin/sh /usr/bin/x-session-manager
jgordon   5373  0.0  0.0   4332   736 ?        Ss   09:01   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
jgordon   5376  0.0  0.0   2712   648 ?        S    09:01   0:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
jgordon   5377  0.0  0.0   2080   424 ?        Ss   09:01   0:00 dbus-daemon --fork --print-pid 8 --print-address 6 --session
jgordon   5406  0.0  0.2  25132  4172 ?        Ss   09:01   0:00 kdeinit Running...
jgordon   5409  0.0  0.1  24584  3080 ?        S    09:01   0:00 dcopserver [kdeinit] --nosid
jgordon   5411  0.0  0.4  25784  8760 ?        S    09:01   0:00 klauncher [kdeinit]
jgordon   5413  0.0  0.6  30436 14456 ?        S    09:01   0:02 kded [kdeinit]  
jgordon   5415  0.0  0.0   2868  1528 ?        S    09:01   0:04 /usr/lib/gamin/gam_server
jgordon   5423  0.0  0.5  50272 12044 ?        S    09:01   0:01 /usr/bin/artsd -F 10 -S 4096 -s 5 -m artsmessage -c drkonqi -l 3 -f
jgordon   5425  0.0  0.4  25804  9772 ?        S    09:01   0:00 kaccess [kdeinit]
jgordon   5426  0.0  0.0   1548   340 ?        S    09:01   0:00 kwrapper ksmserver
jgordon   5428  0.0  0.4  25912 10192 ?        S    09:01   0:00 ksmserver [kdeinit]
jgordon   5431  0.1  0.6  29384 13912 ?        S    09:01   0:47 kwin [kdeinit] -session 10d9e9d775000115798878500000053180000_1160626899_840862
jgordon   5444  0.0  0.8  32772 18436 ?        S    09:01   0:03 kdesktop [kdeinit]
jgordon   5446  0.5  0.9  35608 20456 ?        S    09:01   2:49 kicker [kdeinit]
jgordon   5449  0.0  0.6  29584 13836 ?        S    09:01   0:02 adept_notifier
jgordon   5450  0.0  0.6  27888 12780 ?        S    09:01   0:02 klipper [kdeinit]
jgordon   5452  0.0  0.5  27152 12008 ?        S    09:01   0:00 kbluetoothd --dontforceshow
jgordon   5453  0.0  0.0   2392  1036 ?        S    09:01   0:03 ksysguardd
jgordon   5458  0.0  0.7  30512 14640 ?        S    09:01   0:00 kio_uiserver [kdeinit]
jgordon   5469  0.0  0.7  29940 14868 ?        S    09:01   0:00 kmix [kdeinit] -session 10d8cecf96000111065458100000063760027_1160626899_574930
jgordon   5470  0.0  0.7  29360 15816 ?        S    09:01   0:02 katapult -session 10d9d39668000112680660600000081280032_1160626899_575123
jgordon   5471  0.0  0.8  33012 17160 ?        S    09:01   0:06 konsole [kdeinit] -session 10d9e9d775000115824921500000053570024_1160626899_575308
jgordon   5472  0.0  1.0  35756 21304 ?        S    09:01   0:01 gwenview [kdeinit] -session 10d9e9d775000115851446500000054120018_1160626899_575470
jgordon   5473  0.0  0.1   5732  3416 pts/1    Ss+  09:01   0:00 /bin/bash
jgordon   5476  0.0  1.0  35420 21016 ?        S    09:01   0:04 karm -session 10d9e9d775000115825299800000053840018_1160626899_575582
jgordon   5477  0.0  0.1   5732  3412 pts/2    Ss+  09:01   0:00 /bin/bash
jgordon   5480  0.0  0.1   5724  3408 pts/3    Ss+  09:01   0:00 /bin/bash
jgordon   5484  0.0  0.1   5732  3468 pts/4    Ss+  09:01   0:00 /bin/bash
jgordon   5485  0.0  0.1   5732  3428 pts/5    Ss   09:01   0:00 /bin/bash
jgordon   5496  0.0  0.1   5728  3412 pts/6    Ss+  09:01   0:00 /bin/bash
jgordon   5507  0.0  2.1  98144 45036 ?        Sl   09:01   0:22 kontact -session 10d9e9d775000116014169900000054240011_1160626899_567152
jgordon   5566  0.3  1.0  41276 22012 ?        S    09:01   1:57 gaim --session 10d9e9d775000115964948100000054100016
jgordon   5568  0.0  0.8  41256 18360 ?        S    09:01   0:00 kalarm -session 10d9e9d775000115868262900000054190021_1160626899_575792
jgordon   5590  0.0  1.2  66764 25332 ?        S    09:01   0:27 konqueror [kdeinit] -session 10d9e9d775000116060415800000054210012_1160626899_577330
jgordon   5593  0.0  0.6  33480 13236 ?        S    09:01   0:04 knotify [kdeinit]
jgordon   5594  0.0  0.6  28744 14480 ?        S    09:01   0:00 kcalc [kdeinit] -session 10d9e9d775000116061318700000054210019_1160626899_577518
jgordon   5599  0.0  0.4  26592  9280 ?        S    09:01   0:00 kalarmd --autostart
jgordon   5614  0.0  0.9  34920 19128 ?        S    09:01   0:01 korgac --miniicon korganizer
jgordon   5615  0.0  0.0   4188  1696 ?        S    09:01   0:00 /bin/sh /usr/bin/mozilla-thunderbird
jgordon   5619  0.0  0.0   4232  1728 ?        S    09:01   0:00 /bin/sh /usr/lib/mozilla-thunderbird/run-mozilla.sh /usr/lib/mozilla-thunderbird/mozilla-thunderbird-bin
jgordon   5624  1.6  5.5 196088 116128 ?       Sl   09:01   8:28 /usr/lib/mozilla-thunderbird/mozilla-thunderbird-bin
jgordon   5630  0.0  0.1   4636  2220 ?        S    09:01   0:00 /usr/lib/libgconf2-4/gconfd-2 10
jgordon   5646  5.0  8.4 245844 174464 ?       Sl   09:02  26:17 /usr/lib/firefox/firefox-bin -a firefox
jgordon   5673  0.0  0.0   3644  1348 ?        S    09:03   0:00 /bin/sh -c cd  /usr/local/thinking-rock-1.2.2/; ./thinking-rock.sh  
jgordon   5674  0.0  0.0   3652  1340 ?        S    09:03   0:00 /bin/sh ./thinking-rock.sh
jgordon   5675  0.2  4.0 307004 84972 ?        Sl   09:03   1:11 java -jar thinking-rock-linux-1.2.2.jar
cupsys    5800  0.0  0.0   4196  1864 ?        SNs  09:05   0:00 /usr/sbin/cupsd
syslog    5910  0.0  0.0   1764   708 ?        SNs  09:08   0:00 /sbin/syslogd -u syslog
jgordon   5936  0.0  0.0   3704  1444 ?        S    09:12   0:00 /bin/sh /usr/lib/vmware-player/lib/wrapper-gtk24.sh /usr/lib/vmware-player/lib /usr/lib/vmware-player/bin/vmplayer /usr/lib/vmware-player/libconf
jgordon   5950  0.3  1.5  51800 31896 ?        S    09:12   2:00 /usr/lib/vmware-player/bin/vmplayer
jgordon   5951  0.0  0.0   3704   984 ?        S    09:12   0:00 /bin/sh /usr/lib/vmware-player/lib/wrapper-gtk24.sh /usr/lib/vmware-player/lib /usr/lib/vmware-player/bin/vmplayer /usr/lib/vmware-player/libconf
jgordon   5954  7.6 20.5 517516 426984 ?       S<l  09:12  39:23 /usr/lib/vmware-player/bin/vmware-vmx -@ pipe=/tmp/vmware-jgordon/vmx38fd575ff514fcc0;vm=38fd575ff514fcc0 /opt/win-2003-ent/Windows Server 2003 Enterprise Edition.vmx
jgordon   6004  0.0  0.0   4184  1680 ?        S    09:24   0:00 /bin/sh /usr/lib/openoffice/program/soffice -writer
jgordon   6015  0.1  4.3 208564 91272 ?        Sl   09:24   0:54 /usr/lib/openoffice/program/soffice.bin -writer
root      6102  0.0  0.1   8812  3088 ?        S    09:59   0:00 /usr/sbin/smbd -D
jgordon   6755  0.0  1.2  47644 25076 ?        S    14:00   0:10 kate [kdeinit] --use
jgordon   6759  0.0  0.3  25484  7936 ?        S    14:00   0:00 kio_file [kdeinit] file /tmp/ksocket-jgordon/klauncherkOMbfa.slave-socket /tmp/ksocket-jgordon/kateW6nIDb.slave-socket
jgordon   7117  0.0  0.6  23208 14488 ?        S    15:43   0:02 /usr/local/MyPasswordSafe/MyPasswordSafe /home/jgordon/[password.dat]
jgordon   7657  0.0  0.0   2400  1024 pts/5    R+   17:45   0:00 ps auxw

-- snip --

Thanks for your help!

Jonathan.

---

