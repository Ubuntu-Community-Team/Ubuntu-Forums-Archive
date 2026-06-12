---
title: "Services not starting at boot in Ubuntu 12.04 server AMD64"
date: 2013-10-24
forum: General Help
---

### Post by Shadow aok on 2013-10-24
I'm running Ubuntu 12.04 server AMD64 (system is up to date).

My services doesn't start at boot (even with a service start in rc.local), no even cron.

Here what's up after boot :
```
~# ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1  24008  1920 ?        Ss   10:01   0:00 init
root         2  0.0  0.0      0     0 ?        S    10:01   0:00 [kthreadd/106]
root         3  0.0  0.0      0     0 ?        S    10:01   0:00 [khelper/106]
root        47  0.0  0.0  26360   956 ?        S    10:01   0:00 /sbin/plymouthd --mode=boot --attach-to-session
syslog      78  0.0  0.1 177708  1628 ?        Sl   10:01   0:00 rsyslogd -c5
root        96  0.0  0.0  17192   532 ?        S    10:01   0:00 upstart-udev-bridge --daemon
root       101  0.0  0.1  21428  1060 ?        Ss   10:01   0:00 /sbin/udevd --daemon
108        117  0.0  0.0  23776   752 ?        Ss   10:01   0:00 dbus-daemon --system --fork --activation=upstart
root       196  0.0  0.2  49992  2920 ?        Ss   10:01   0:00 /usr/sbin/sshd -D
root       238  0.5  0.3  73396  4048 ?        Ss   10:03   0:00 sshd: root@pts/0
root       254  2.4  0.3  20064  4064 pts/0    Ss   10:03   0:00 -bash
root       311  0.0  0.1  15236  1136 pts/0    R+   10:03   0:00 ps aux
```

```
~# chkconfig -l
anacron                   0:off  1:off  2:off  3:off  4:off  5:off  6:off
apache2                   0:off  1:off  2:on   3:on   4:on   5:on   6:off
bind9                     0:off  1:off  2:on   3:on   4:on   5:on   6:off
bootlogd                  0:off  1:off  2:off  3:off  4:off  5:off  6:off
console-screen.sh         0:off  1:off  2:off  3:off  4:off  5:off  6:off  S:on
cron                      0:off  1:off  2:on   3:on   4:on   5:on   6:off
dbus                      0:off  1:off  2:off  3:off  4:off  5:off  6:off
dmesg                     0:off  1:off  2:off  3:off  4:off  5:off  6:off
fetchmail                 0:off  1:off  2:on   3:on   4:on   5:on   6:off
grub-common               0:off  1:off  2:on   3:on   4:on   5:on   6:off
hostname                  0:off  1:off  2:off  3:off  4:off  5:off  6:off
hwclock                   0:off  1:off  2:off  3:off  4:off  5:off  6:off
hwclock-save              0:off  1:off  2:off  3:off  4:off  5:off  6:off
keymap.sh                 0:off  1:off  2:off  3:off  4:off  5:off  6:off  S:on
killprocs                 0:off  1:on   2:off  3:off  4:off  5:off  6:off
klogd                     0:off  1:off  2:off  3:off  4:off  5:off  6:off
module-init-tools         0:off  1:off  2:off  3:off  4:off  5:off  6:off
modules_dep.sh            0:off  1:off  2:on   3:on   4:on   5:on   6:off
mysql                     0:off  1:off  2:on   3:on   4:on   5:on   6:off
network-interface         0:off  1:off  2:off  3:off  4:off  5:off  6:off
network-interface-container  0:off  1:off  2:off  3:off  4:off  5:off  6:off
network-interface-security  0:off  1:off  2:off  3:off  4:off  5:off  6:off
networking                0:on   1:off  2:off  3:off  4:off  5:off  6:off
ntp                       0:off  1:off  2:on   3:on   4:on   5:on   6:off
ondemand                  0:off  1:off  2:on   3:on   4:on   5:on   6:off
passwd                    0:off  1:off  2:off  3:off  4:off  5:off  6:off
plymouth                  0:off  1:off  2:off  3:off  4:off  5:off  6:off
plymouth-log              0:off  1:off  2:off  3:off  4:off  5:off  6:off
plymouth-ready            0:off  1:off  2:off  3:off  4:off  5:off  6:off
plymouth-splash           0:off  1:off  2:off  3:off  4:off  5:off  6:off
plymouth-stop             0:off  1:off  2:off  3:off  4:off  5:off  6:off
plymouth-upstart-bridge   0:off  1:off  2:off  3:off  4:off  5:off  6:off
postfix                   0:off  1:off  2:on   3:on   4:on   5:on   6:off
procps                    0:off  1:off  2:off  3:off  4:off  5:off  6:off
pygrenouille.sh           0:off  1:off  2:off  3:off  4:off  5:off  6:off
quota                     0:off  1:off  2:off  3:off  4:off  5:off  6:off  S:on
quotarpc                  0:off  1:off  2:on   3:on   4:on   5:on   6:off
rc.local                  0:off  1:off  2:on   3:on   4:on   5:on   6:off
rcS                       0:off  1:off  2:off  3:off  4:off  5:off  6:off
rsync                     0:off  1:off  2:on   3:on   4:on   5:on   6:off
rsyslog                   0:off  1:off  2:off  3:off  4:off  5:off  6:off
saslauthd                 0:off  1:off  2:off  3:off  4:off  5:off  6:off
screen-cleanup            0:off  1:off  2:off  3:off  4:off  5:off  6:off
sendmail                  0:off  1:off  2:on   3:on   4:on   5:on   6:off
sendsigs                  0:on   1:off  2:off  3:off  4:off  5:off  6:off
ssh                       0:off  1:off  2:on   3:on   4:on   5:on   6:off
stop-bootlogd             0:off  1:off  2:off  3:off  4:off  5:off  6:off
stop-bootlogd-single      0:off  1:off  2:off  3:off  4:off  5:off  6:off
sudo                      0:off  1:off  2:on   3:on   4:on   5:on   6:off
sysklogd                  0:off  1:off  2:on   3:on   4:on   5:on   6:off
udev                      0:off  1:off  2:off  3:off  4:off  5:off  6:off
udev-fallback-graphics    0:off  1:off  2:off  3:off  4:off  5:off  6:off
udev-finish               0:off  1:off  2:off  3:off  4:off  5:off  6:off
udevmonitor               0:off  1:off  2:off  3:off  4:off  5:off  6:off
udevtrigger               0:off  1:off  2:off  3:off  4:off  5:off  6:off
umountfs                  0:on   1:off  2:off  3:off  4:off  5:off  6:off
umountnfs.sh              0:on   1:off  2:off  3:off  4:off  5:off  6:off
umountroot                0:on   1:off  2:off  3:off  4:off  5:off  6:off
urandom                   0:on   1:off  2:off  3:off  4:off  5:off  6:off  S:on
vzreboot                  0:off  1:off  2:off  3:off  4:off  5:off  6:off
wide-dhcpv6-client        0:off  1:off  2:on   3:on   4:on   5:on   6:off
x11-common                0:off  1:off  2:off  3:off  4:off  5:off  6:off  S:on
xinetd                    0:off  1:off  2:off  3:off  4:off  5:off  6:off
xinetd based services:
        chargen:            off
        daytime:            off
        discard:            off
        echo:               off
        time:               off
```
        
```
/etc/rc2.d# ll
total 12
drwxr-xr-x   2 root root 4096 Oct 24 09:58 ./
drwxr-xr-x 106 root root 4096 Oct 24 10:01 ../
-rw-r--r--   1 root root  677 Jul 26  2012 README
lrwxrwxrwx   1 root root   24 Oct 24 09:50 S01modules_dep.sh -> ../init.d/modules_dep.sh*
lrwxrwxrwx   1 root root   14 Oct 24 09:50 S01sudo -> ../init.d/sudo*
lrwxrwxrwx   1 root root   18 Oct 24 09:50 S01sysklogd -> ../init.d/sysklogd*
lrwxrwxrwx   1 root root   15 Oct 24 09:50 S02bind9 -> ../init.d/bind9*
lrwxrwxrwx   1 root root   13 Oct 24 09:50 S02ntp -> ../init.d/ntp*
lrwxrwxrwx   1 root root   18 Oct 24 09:50 S02quotarpc -> ../init.d/quotarpc*
lrwxrwxrwx   1 root root   18 Oct 24 09:50 S02sendmail -> ../init.d/sendmail*
lrwxrwxrwx   1 root root   13 Oct 24 09:57 S02ssh -> ../init.d/ssh*
lrwxrwxrwx   1 root root   28 Oct 24 09:50 S02wide-dhcpv6-client -> ../init.d/wide-dhcpv6-client*
lrwxrwxrwx   1 root root   17 Oct 24 09:50 S03apache2 -> ../init.d/apache2*
lrwxrwxrwx   1 root root   17 Oct 24 09:50 S04postfix -> ../init.d/postfix*
lrwxrwxrwx   1 root root   15 Oct 24 09:50 S04rsync -> ../init.d/rsync*
lrwxrwxrwx   1 root root   19 Oct 24 09:50 S05fetchmail -> ../init.d/fetchmail*
lrwxrwxrwx   1 root root   21 Oct 24 09:50 S06grub-common -> ../init.d/grub-common*
lrwxrwxrwx   1 root root   18 Oct 24 09:50 S06ondemand -> ../init.d/ondemand*
lrwxrwxrwx   1 root root   18 Oct 24 09:50 S06rc.local -> ../init.d/rc.local*
lrwxrwxrwx   1 root root   14 Oct 24 09:58 S20cron -> ../init.d/cron*
lrwxrwxrwx   1 root root   15 Oct 24 09:58 S20mysql -> ../init.d/mysql*

```

```
~# initctl list
nmbd stop/waiting
passwd stop/waiting
rc stop/waiting
rsyslog start/running, process 78
screen-cleanup stop/waiting
tty4 stop/waiting
udev start/running, process 101
upstart-udev-bridge start/running, process 96
tty5 stop/waiting
failsafe stop/waiting
dbus start/running, process 117
mounted-var stop/waiting
plymouth start/running, process 47
ssh start/running, process 196
udev-fallback-graphics stop/waiting
portmap-boot stop/waiting
module-init-tools stop/waiting
shutdown stop/waiting
cron stop/waiting
mountall start/running
mounted-debugfs stop/waiting
xinetd stop/waiting
console stop/waiting
mounted-run stop/waiting
plymouth-stop stop/waiting
rcS stop/waiting
wait-for-state stop/waiting
flush-early-job-log stop/waiting
rc-sysinit stop/waiting
upstart-socket-bridge stop/waiting
anacron stop/waiting
tty2 stop/waiting
udevtrigger stop/waiting
container-detect stop/waiting
mounted-dev stop/waiting
tty3 stop/waiting
hostname stop/waiting
mysql stop/waiting
mounted-tmp stop/waiting
network-interface stop/waiting
plymouth-ready stop/waiting
portmap-wait stop/waiting
tty1 stop/waiting
dmesg stop/waiting
network-interface-security (networking) start/running
networking stop/waiting
procps stop/waiting
tty6 stop/waiting
network-interface-container stop/waiting
```

I got nothing helpful in syslog.
I have no dmesg or boot.log file.

```
/etc/init.d# ll
total 264
drwxr-xr-x   2 root root  4096 Oct 24 09:51 ./
drwxr-xr-x 106 root root  4096 Oct 24 10:01 ../
-rw-r--r--   1 root root   123 Oct 24 09:57 .depend.boot
-rw-r--r--   1 root root   866 Oct 24 09:57 .depend.start
-rw-r--r--   1 root root   709 Oct 24 09:57 .depend.stop
-rw-r--r--   1 root root     0 May 18  2011 .legacy-bootordering
-rw-r--r--   1 root root  2427 Jul 26  2012 README
lrwxrwxrwx   1 root root    21 Apr  5  2013 anacron -> /lib/init/upstart-job*
-rwxr-xr-x   1 root root  7621 Feb 14  2012 apache2*
-rwxr-xr-x   1 root root  3449 Oct  9  2012 bind9*
-rwxr-xr-x   1 root root  2444 Dec 15  2011 bootlogd*
-rwxr-xr-x   1 root root  6277 Jun 23  2008 console-screen.sh*
lrwxrwxrwx   1 root root    21 Jun 19  2012 cron -> /lib/init/upstart-job*
lrwxrwxrwx   1 root root    21 Jun 13 16:55 dbus -> /lib/init/upstart-job*
lrwxrwxrwx   1 root root    21 Sep 19 22:17 dmesg -> /lib/init/upstart-job*
-rwxr-xr-x   1 root root  7706 Sep  4  2011 fetchmail*
-rwxr-xr-x   1 root root  1105 Oct  1  2011 grub-common*
-rwxr-xr-x   1 root root  1329 Sep  7  2009 halt*
lrwxrwxrwx   1 root root    21 Apr  5  2013 hostname -> /lib/init/upstart-job*
lrwxrwxrwx   1 root root    21 Apr  5  2013 hwclock -> /lib/init/upstart-job*
lrwxrwxrwx   1 root root    21 Apr  5  2013 hwclock-save -> /lib/init/upstart-job*
-rwxr-xr-x   1 root root  3463 Dec  5  2011 keymap.sh*
-rwxr-xr-x   1 root root  1293 Sep  7  2009 killprocs*
-rwxr-xr-x   1 root root  1816 Oct 25  2010 klogd*
lrwxrwxrwx   1 root root    21 Apr  5  2013 module-init-tools -> /lib/init/upstart-job*
-rwxr-xr-x   1 root root   671 May 18  2011 modules_dep.sh*
lrwxrwxrwx   1 root root    21 Jul 24 05:43 mysql -> /lib/init/upstart-job*
lrwxrwxrwx   1 root root    21 Sep 19 21:59 network-interface -> /lib/init/upstart-job*
lrwxrwxrwx   1 root root    21 Sep 19 21:59 network-interface-container -> /lib/init/upstart-job*
lrwxrwxrwx   1 root root    21 Sep 19 21:59 network-interface-security -> /lib/init/upstart-job*
-rwxr-xr-x   1 root root  2797 May 23  2011 networking*
-rwxr-xr-x   1 root root  1818 Nov 30  2010 ntp*
-rwxr-xr-x   1 root root   882 Sep  7  2009 ondemand*
lrwxrwxrwx   1 root root    21 Apr  5  2013 passwd -> /lib/init/upstart-job*
lrwxrwxrwx   1 root root    21 May 17 00:12 plymouth -> /lib/init/upstart-job*
lrwxrwxrwx   1 root root    21 May 17 00:12 plymouth-log -> /lib/init/upstart-job*
lrwxrwxrwx   1 root root    21 May 17 00:12 plymouth-ready -> /lib/init/upstart-job*
lrwxrwxrwx   1 root root    21 May 17 00:12 plymouth-splash -> /lib/init/upstart-job*
lrwxrwxrwx   1 root root    21 May 17 00:12 plymouth-stop -> /lib/init/upstart-job*
lrwxrwxrwx   1 root root    21 May 17 00:12 plymouth-upstart-bridge -> /lib/init/upstart-job*
-rwxr-xr-x   1 root root  7355 Oct 23  2012 postfix*
lrwxrwxrwx   1 root root    21 Oct 17 16:50 procps -> /lib/init/upstart-job*
-rwxr-xr-x   1 root root  1038 Oct 11  2011 pygrenouille.sh*
-rwxr-xr-x   1 root root  3092 Oct 18  2012 quota*
-rwxr-xr-x   1 root root  1959 Oct 18  2012 quotarpc*
-rwxr-xr-x   1 root root  8635 Jul 26  2012 rc*
-rwxr-xr-x   1 root root   801 Sep  7  2009 rc.local*
-rwxr-xr-x   1 root root   117 Jul 26  2012 rcS*
-rwxr-xr-x   1 root root   639 Sep  7  2009 reboot*
-rwxr-xr-x   1 root root  4395 Nov  8  2011 rsync*
lrwxrwxrwx   1 root root    21 Sep 19 22:17 rsyslog -> /lib/init/upstart-job*
-rwxr-xr-x   1 root root 10486 Aug 15  2011 saslauthd*
lrwxrwxrwx   1 root root    21 Apr  5  2013 screen-cleanup -> /lib/init/upstart-job*
-rwxr-xr-x   1 root root 33742 Aug 14  2011 sendmail*
-rwxr-xr-x   1 root root  4321 Dec 15  2011 sendsigs*
-rwxr-xr-x   1 root root   590 Sep  7  2009 single*
-rw-r--r--   1 root root  4304 Jul 26  2012 skeleton
-rwxr-xr-x   1 root root  4371 Apr  2  2012 ssh*
-rwxr-xr-x   1 root root   567 Dec 15  2011 stop-bootlogd*
-rwxr-xr-x   1 root root  1143 Dec 15  2011 stop-bootlogd-single*
-rwxr-xr-x   1 root root   700 Apr 13  2011 sudo*
-rwxr-xr-x   1 root root  3582 Oct 25  2010 sysklogd*
lrwxrwxrwx   1 root root    21 Jul 20 02:21 udev -> /lib/init/upstart-job*
lrwxrwxrwx   1 root root    21 Jul 20 02:21 udev-fallback-graphics -> /lib/init/upstart-job*
lrwxrwxrwx   1 root root    21 Jul 20 02:21 udev-finish -> /lib/init/upstart-job*
lrwxrwxrwx   1 root root    21 Jul 20 02:21 udevmonitor -> /lib/init/upstart-job*
lrwxrwxrwx   1 root root    21 Jul 20 02:21 udevtrigger -> /lib/init/upstart-job*
-rwxr-xr-x   1 root root  2800 Dec 15  2011 umountfs*
-rwxr-xr-x   1 root root  2211 Dec 15  2011 umountnfs.sh*
-rwxr-xr-x   1 root root  2926 Dec 15  2011 umountroot*
-rwxr-xr-x   1 root root  1985 Dec 15  2011 urandom*
-rwxr-xr-x   1 root root   194 May 18  2011 vzreboot*
-rwxr-xr-x   1 root root  1830 Jul 16  2010 wide-dhcpv6-client*
-rwxr-xr-x   1 root root  2666 Mar 22  2012 x11-common*
lrwxrwxrwx   1 root root    21 Apr  5  2013 xinetd -> /lib/init/upstart-job*
```

I don't know what to check next.

Any idea ?

Thanks.

---

### Post by Shadow aok on 2013-10-24
It's an openvz container with proxmox 3.1-20.
Problem is I have other container with the same template and it's working well.

I tried a telinit 2 but i didn't fixed the issue.

And after a reboot, my init level isn't good : 
```
~# runlevel
unknown
```

---

### Post by Shadow aok on 2013-10-24
[HR][/HR]I'm wondering if i'm not missing some init files.

```
~# ll /etc/init
total 216
drwxr-xr-x   2 root root 4096 Oct 24 10:38 ./
drwxr-xr-x 106 root root 4096 Oct 24 10:33 ../
-rw-r--r--   1 root root  281 Oct 24 10:00 anacron.conf
-rw-r--r--   1 root root  266 Apr 26  2012 console.conf
-rw-r--r--   1 root root 1122 Apr 26  2012 container-detect.conf
-rw-r--r--   1 root root  297 Jan  5  2011 cron.conf
-rw-r--r--   1 root root  510 Jan 10  2012 dbus.conf
-rw-r--r--   1 root root  273 Jan 12  2011 dmesg.conf
-rw-r--r--   1 root root 1377 Apr 26  2012 failsafe.conf
-rw-r--r--   1 root root  267 Apr 26  2012 flush-early-job-log.conf
-rw-r--r--   1 root root  317 Nov 17  2010 hostname.conf
-rw-r--r--   1 root root  367 Apr  1  2011 module-init-tools.conf
-rw-r--r--   1 root root  789 May 18  2011 mountall.conf
-rw-r--r--   1 root root  405 Apr 12  2012 mounted-debugfs.conf
-rw-r--r--   1 root root  550 Jul 15  2011 mounted-dev.conf
-rw-r--r--   1 root root  610 Jul 15  2011 mounted-run.conf
-rw-r--r--   1 root root 1890 Apr 12  2012 mounted-tmp.conf
-rw-r--r--   1 root root  903 Jul 15  2011 mounted-var.conf
-rw-r--r--   1 root root 1108 Feb 20  2012 mysql.conf
-rw-r--r--   1 root root  523 Apr  5  2012 network-interface-container.conf
-rw-r--r--   1 root root 1603 Apr  5  2012 network-interface-security.conf
-rw-r--r--   1 root root  803 Apr  5  2012 network-interface.conf
-rw-r--r--   1 root root  344 Nov  7  2012 networking.conf
-rw-r--r--   1 root root  348 Oct 17  2012 networking.conf.dpkg-old
-rw-r--r--   1 root root  483 Jun  8  2012 nmbd.conf
-rw-r--r--   1 root root  534 Sep 13  2012 passwd.conf
-rw-r--r--   1 root root  647 May  3 09:49 plymouth-ready.conf
-rw-r--r--   1 root root  800 Sep 28  2011 plymouth-stop.conf
-rw-r--r--   1 root root  971 Sep 28  2011 plymouth.conf
-rw-r--r--   1 root root  230 Mar 14  2011 portmap-boot.conf
-rw-r--r--   1 root root  684 Mar 14  2011 portmap-wait.conf
-rw-r--r--   1 root root  363 Dec  5  2011 procps.conf
-rw-r--r--   1 root root 1543 Apr 25  2012 rc-sysinit.conf
-rw-r--r--   1 root root 1504 May 18  2011 rc-sysinit.conf.dpkg-old
-rw-r--r--   1 root root  454 Apr 25  2012 rc.conf
-rw-r--r--   1 root root  389 May 18  2011 rc.conf.dpkg-old
-rw-r--r--   1 root root  705 Apr 25  2012 rcS.conf
-rw-r--r--   1 root root  426 Mar 30  2012 rsyslog.conf
-rw-r--r--   1 root root  683 Apr 14  2011 screen-cleanup.conf
-rw-r--r--   1 root root  277 Apr 26  2012 shutdown.conf
-rw-r--r--   1 root root  667 Feb  6  2012 ssh.conf
-rw-r--r--   1 root root  348 Apr 26  2012 tty1.conf
-rw-r--r--   1 root root  333 Apr 26  2012 tty2.conf
-rw-r--r--   1 root root  333 Apr 26  2012 tty3.conf
-rw-r--r--   1 root root  333 Apr 26  2012 tty4.conf
-rw-r--r--   1 root root  232 Apr 26  2012 tty5.conf
-rw-r--r--   1 root root  232 Apr 26  2012 tty6.conf
-rw-r--r--   1 root root  637 Jul 16  2012 udev-fallback-graphics.conf
-rw-r--r--   1 root root  322 Nov 15  2011 udev.conf
-rw-r--r--   1 root root  352 Jul 16  2012 udevtrigger.conf
-rw-r--r--   1 root root  329 Apr 21  2011 upstart-socket-bridge.conf
-rw-r--r--   1 root root  553 Apr 25  2012 upstart-udev-bridge.conf
-rw-r--r--   1 root root 1481 Apr 25  2012 wait-for-state.conf
-rw-r--r--   1 root root 1481 Dec  6  2010 xinetd.conf
```

---

### Post by Shadow aok on 2013-10-24
Ok, fixed it.
I moved elsewhere all the /etc/init conf files from the vm and replaced them by those from another vm (same template).
Now everything seems to work.

---

