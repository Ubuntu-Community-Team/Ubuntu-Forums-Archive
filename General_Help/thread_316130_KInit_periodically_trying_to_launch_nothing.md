---
title: "KInit periodically trying to launch nothing"
date: 2006-12-10
forum: General Help
---

### Post by carlosm on 2006-12-10
Hello there,

I'm getting periodical hard drive activity by KInit, at the konsole I get the following printed when the HD activity hits (periodically each 2-3 seconds, never ends)

(HD activity)
KInit could not launch ''.
Could not find '' executable.
(2 secs)
(HD activity)
KInit could not launch ''.
Could not find '' executable.
(2 secs)

etc ...

I read it had something to do with Kerberos, but i haven't got any kerberos stuff installed and i haven't got any service working on my machine like sshd or apache or alike.

Anyone could give me a hint please? Thanks in advance :)

Btw: i started killing processes like mad, but couldn't find the one causing the activity.

// Kubuntu 6.10 fully updated

carlosm@metheny:~$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
  104 ?        00:00:00 kseriod
  137 ?        00:00:00 pdflush
  138 ?        00:00:00 pdflush
  139 ?        00:00:00 kswapd0
  140 ?        00:00:00 aio/0
 1703 ?        00:00:00 khubd
 1726 ?        00:00:00 khpsbpkt
 1751 ?        00:00:00 knodemgrd_0
 1799 ?        00:00:00 kjournald
 1874 ?        00:00:00 logd
 2020 ?        00:00:00 udevd
 2801 ?        00:00:00 kpsmoused
 2823 ?        00:00:00 shpchpd
 2963 ?        00:00:00 ipw2200/0
 3080 ?        00:00:00 pccardd
 3322 ?        00:00:00 reiserfs/0
 3639 tty1     00:00:00 getty
 3640 tty2     00:00:00 login
 3641 tty3     00:00:00 getty
 3642 tty4     00:00:00 getty
 3643 tty5     00:00:00 getty
 3644 tty6     00:00:00 getty
 3870 ?        00:00:00 acpid
 3985 ?        00:00:00 dd
 3987 ?        00:00:00 klogd
 4098 ?        00:00:00 dbus-daemon
 4113 ?        00:00:02 hald
 4114 ?        00:00:00 hald-runner
 4122 ?        00:00:00 hald-addon-acpi
 4124 ?        00:00:00 hald-addon-keyb
 4140 ?        00:00:00 hald-addon-stor
 4234 ?        00:00:00 ondemand
 4318 ?        00:00:00 cron
 6553 tty2     00:00:00 bash
 6703 tty2     00:00:00 startx
 6719 tty2     00:00:00 xinit
 6720 tty7     00:01:29 Xorg
 6725 tty2     00:00:00 x-session-manag
 6752 ?        00:00:00 ssh-agent
 6755 tty2     00:00:00 dbus-launch
 6756 ?        00:00:00 dbus-daemon
 6789 tty2     00:00:00 start_kdeinit
 6790 ?        00:00:00 kdeinit
 6793 ?        00:00:00 dcopserver
 6796 ?        00:00:00 klauncher
 6798 ?        00:00:01 kded
 6804 tty2     00:00:00 kwrapper
 6806 ?        00:00:00 ksmserver
 6807 ?        00:00:02 kwin
 6809 ?        00:00:02 kdesktop
 6811 ?        00:00:02 kicker
 6815 ?        00:00:00 kio_file
 6817 ?        00:00:00 kio_uiserver
 6833 ?        00:00:00 kaccess
 6836 ?        00:00:00 kmix
 6837 ?        00:00:00 katapult
 6839 ?        00:00:01 knotes
 6842 ?        00:00:00 aspell
 6853 ?        00:00:00 guidance-power-
 6854 ?        00:00:06 guidance-power-
 6860 ?        00:00:00 knotify
 6861 ?        00:00:00 klipper
 6863 ?        00:00:08 adept_notifier
 6865 ?        00:00:00 kbluetoothd
 6869 ?        00:00:03 konsole
 6870 pts/1    00:00:00 bash
 7182 ?        00:00:00 kdeinit
 7187 ?        00:00:00 dcopserver
 7190 ?        00:00:00 klauncher
 7192 ?        00:00:00 kded
 7197 ?        00:00:00 knotify
 7199 ?        00:00:00 knotify
 7416 pts/3    00:00:00 bash
 9661 pts/3    00:00:09 firestarter
 9663 pts/3    00:00:00 gconfd-2
10013 pts/1    00:00:18 firefox-bin
10022 pts/1    00:00:00 gconfd-2
10919 pts/1    00:00:00 ps

---

### Post by carlosm on 2006-12-10
I think this may be serious, I just reinstalled, updated and it keeps happening.

---

