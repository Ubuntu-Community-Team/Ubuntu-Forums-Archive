---
title: "Trimming process schedule"
date: 2007-01-29
forum: General Help
---

### Post by carverj on 2007-01-29
Hi all,
         I have a pretty large process tree:-

```
jeremy@jeremy-desktop:~$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:03 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
   66 ?        00:00:00 kseriod
   97 ?        00:00:00 pdflush
   98 ?        00:00:00 pdflush
   99 ?        00:00:02 kswapd0
  100 ?        00:00:00 aio/0
 1729 ?        00:00:00 khubd
 1790 ?        00:00:00 kjournald
 1863 ?        00:00:00 logd
 1995 ?        00:00:01 udevd
 2734 ?        00:00:00 shpchpd
 2744 ?        00:00:00 kpsmoused
 3203 ?        00:00:00 kjournald
 3582 tty1     00:00:00 getty
 3583 tty2     00:00:00 getty
 3584 tty3     00:00:00 getty
 3585 tty4     00:00:00 getty
 3586 tty5     00:00:00 getty
 3587 tty6     00:00:00 getty
 3799 ?        00:00:00 acpid
 3919 ?        00:00:00 dd
 3921 ?        00:00:00 klogd
 3943 ?        00:00:00 gdm
 3951 ?        00:00:00 gdm
 3956 tty7     00:06:08 Xorg
 3986 ?        00:00:01 dbus-daemon
 4003 ?        00:00:09 hald
 4004 ?        00:00:00 hald-runner
 4034 ?        00:00:00 hald-addon-acpi
 4035 ?        00:00:00 hald-addon-keyb
 4048 ?        00:00:01 hald-addon-stor
 4050 ?        00:00:01 hald-addon-stor
 4077 ?        00:00:00 dhcdbd
 4094 ?        00:00:00 NetworkManager
 4109 ?        00:00:00 NetworkManagerD
 4131 ?        00:00:00 dhclient
 4142 ?        00:00:00 perl
 4260 ?        00:00:00 atd
 4273 ?        00:00:00 cron
 5026 ?        00:00:00 syslogd
 5029 ?        00:00:02 x-session-manag
 5064 ?        00:00:00 ssh-agent
 5067 ?        00:00:00 dbus-launch
 5068 ?        00:00:00 dbus-daemon
 5070 ?        00:00:03 gconfd-2
 5073 ?        00:00:00 gnome-keyring-d
 5076 ?        00:00:03 gnome-settings-
 5085 ?        00:00:00 sh
 5086 ?        00:00:00 esd
 5091 ?        00:00:38 metacity
 5096 ?        00:00:21 gnome-panel
 5098 ?        00:00:10 nautilus
 5102 ?        00:00:01 bonobo-activati
 5106 ?        00:00:00 gnome-vfs-daemo
 5109 ?        00:00:02 gnome-volume-ma
 5111 ?        00:00:02 update-notifier
 5117 ?        00:00:01 evolution-alarm
 5130 ?        00:06:02 beagled
 5133 ?        00:00:03 nm-applet
 5142 ?        00:00:00 gnome-power-man
 5170 ?        00:00:00 evolution-data-
 5185 ?        00:00:01 trashapplet
 5200 ?        00:00:00 mapping-daemon
 5211 ?        00:00:01 evolution-excha
 5217 ?        00:00:02 gnome-screensav
 5248 ?        00:00:01 multiload-apple
 5261 ?        00:00:03 mixer_applet2
 5267 ?        00:00:03 notification-da
 5336 ?        00:00:07 gksudo
 5337 ?        00:00:44 nautilus
 5339 ?        00:00:02 gconfd-2
 5341 ?        00:00:00 bonobo-activati
 5349 ?        00:00:00 mapping-daemon
 5354 ?        00:00:00 sh
 5355 ?        00:00:00 esd
 5477 ?        00:05:40 firefox-bin
 5557 ?        00:00:00 soffice
 5571 ?        00:00:43 soffice.bin
 5581 ?        00:00:07 gnome-terminal
 5585 ?        00:00:00 gnome-pty-helpe
 5586 pts/0    00:00:01 bash
 5655 ?        00:00:13 beagled-helper
 5689 pts/0    00:00:00 ps

```

Will this schedule slow my computer down and if so, what is the best method for altering or removing the redundant processes?
Thanks guys

---

