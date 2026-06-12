---
title: "Problem when Gnome is starting"
date: 2005-10-20
forum: General Help
---

### Post by gyhelle on 2005-10-20
Hello,

My problem is the following :

One day, after settle a network problem, Gnome was suddently low to start.

Now, the ubuntu starting is normal until gdm. But when I log-in, a brown screen appear, and if I can still move the mouse  but I must wait a long time (at least 5 mn) to see the  gnome splash bar. At this moment the loading of my desktop is very quick. 

I don't have any problem with xfce.
Moreover if I login into xfce, logout, and login into gnome I don't have this problem to.

I've this problem since Hoary but the upgrade to Breezy didn't resolve this problem.

any suuggestion ?
best regards,

gyhelle


PS if it can help :
this is the .xsession-error during the gnome log-in :

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "menut"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/villon:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/villon:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/villon:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/villon:/tmp/.ICE-unix/8650

and the ps aux :
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.9  0.1   1560   528 ?        S    16:23   0:01 init [2]
root         2  0.0  0.0      0     0 ?        SN   16:23   0:00 [ksoftirqd/0]
root         3  0.0  0.0      0     0 ?        S<   16:23   0:00 [events/0]
root         4  0.0  0.0      0     0 ?        S<   16:23   0:00 [khelper]
root         5  0.0  0.0      0     0 ?        S<   16:23   0:00 [kthread]
root         7  0.0  0.0      0     0 ?        S<   16:23   0:00 [kacpid]
root       133  0.0  0.0      0     0 ?        S<   16:23   0:00 [kblockd/0]
root       161  0.0  0.0      0     0 ?        S    16:23   0:00 [pdflush]
root       162  0.0  0.0      0     0 ?        S    16:23   0:00 [pdflush]
root       164  0.0  0.0      0     0 ?        S<   16:23   0:00 [aio/0]
root       163  0.0  0.0      0     0 ?        S    16:23   0:00 [kswapd0]
root       754  0.0  0.0      0     0 ?        S    16:23   0:00 [kseriod]
root       985  0.0  0.0      0     0 ?        S<   16:23   0:00 [ata/0]
root       990  0.0  0.0      0     0 ?        S    16:23   0:00 [scsi_eh_0]
root       994  0.0  0.0      0     0 ?        S    16:23   0:00 [scsi_eh_1]
root      1733  0.0  0.0      0     0 ?        S    16:23   0:00 [khubd]
root      3152  0.0  0.0      0     0 ?        S    16:23   0:00 [kjournald]
root      3294  0.0  0.1   1664   576 ?        S<s  16:23   0:00 udevd --daemon
root      6341  0.0  0.0      0     0 ?        S    16:23   0:00 [pccardd]
root      6426  0.0  0.0      0     0 ?        S<   16:23   0:00 [ipw2200/0]
root      7632  0.0  0.2   1956  1040 ?        Ss   16:23   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
syslog    7647  0.0  0.1   1760   756 ?        Ss   16:23   0:00 /sbin/syslogd -u syslog
root      7664  0.0  0.0   1564   400 ?        Ss   16:23   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      7666  0.0  0.3   2580  1560 ?        Ss   16:23   0:00 /sbin/klogd -P /var/run/klogd/kmsg
101       7679  0.0  0.2   2148  1036 ?        Ss   16:23   0:00 /usr/bin/dbus-daemon --system
hal       7692  0.4  0.7   5144  3816 ?        Ss   16:23   0:00 /usr/sbin/hald
hal       7697  0.0  0.1   1864   696 ?        S    16:23   0:00 hald-addon-acpi
hal       7711  0.0  0.1   1872   636 ?        S    16:23   0:00 hald-addon-storage
root      8085  0.0  0.4  10864  2580 ?        Ss   16:23   0:00 /usr/sbin/gdm
root      8090  0.0  0.6  11420  3180 ?        S    16:23   0:00 /usr/sbin/gdm
root      8148  3.0  2.2  14452 11664 ?        SL   16:23   0:02 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      8177  0.0  0.2   4616  1440 ?        Ss   16:23   0:00 /usr/sbin/cupsd -F
root      8197  0.0  0.1   3260   920 ?        S    16:23   0:00 /usr/lib/cups/backend/hp
root      8282  0.0  0.0   1556   444 ?        Ss   16:23   0:00 /usr/sbin/inetd
root      8324  0.0  0.1   1708   736 ?        Ss   16:23   0:00 /sbin/cardmgr
root      8497  0.0  0.1   1552   532 ?        SNs  16:23   0:00 /usr/sbin/powernowd -q
root      8512  0.0  0.1   1924   816 ?        Ss   16:23   0:00 hcid: processing events
root      8518  0.0  0.1   1612   556 ?        Ss   16:23   0:00 /usr/sbin/sdpd
root      8528  0.0  0.0      0     0 ?        S<   16:23   0:00 [krfcommd]
daemon    8560  0.0  0.1   1748   652 ?        Ss   16:23   0:00 /usr/sbin/atd
root      8573  0.0  0.1   1816   856 ?        Ss   16:23   0:00 /usr/sbin/cron
root      8614  0.0  0.2   2260  1056 tty1     Ss   16:23   0:00 /bin/login --
root      8615  0.0  0.0   1560   496 tty2     Ss+  16:23   0:00 /sbin/getty 38400 tty2
root      8616  0.0  0.0   1560   496 tty3     Ss+  16:23   0:00 /sbin/getty 38400 tty3
root      8617  0.0  0.0   1560   496 tty4     Ss+  16:23   0:00 /sbin/getty 38400 tty4
root      8618  0.0  0.0   1560   496 tty5     Ss+  16:23   0:00 /sbin/getty 38400 tty5
root      8619  0.0  0.0   1560   492 tty6     Ss+  16:23   0:00 /sbin/getty 38400 tty6
menut     8650  0.2  1.2  17172  6656 ?        Ss   16:24   0:00 /usr/bin/gnome-session
menut     8701  0.0  0.1   3124  1004 ?        Ss   16:24   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session
menut     8704  0.0  0.1   2572   740 ?        S    16:24   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session
menut     8705  0.0  0.1   2032   740 ?        Ss   16:24   0:00 dbus-daemon --fork --print-pid 8 --print-address 6 --session
menut     8707  0.1  0.4   5484  2476 ?        S    16:24   0:00 /usr/lib/gconf2/gconfd-2 5
menut     8736  0.0  0.2   2328  1060 ?        S    16:24   0:00 /usr/bin/gnome-keyring-daemon
menut     8737  0.0  0.4   4968  2088 tty1     S    16:24   0:00 -bash
menut     8749  0.0  0.1   2548   872 tty1     R+   16:25   0:00 ps aux

---

