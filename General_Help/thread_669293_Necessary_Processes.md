---
title: "Necessary Processes"
date: 2008-01-16
forum: General Help
---

### Post by The Titan on 2008-01-16
I'm using Ubuntu 7.10 and when i play quake i CPU lag really bad and i was wondering if there are any processes that are unnecessary but are enabled by default.  Ill give you a list of my running processes and maybe you can help.  Some are obvious like firefox and amarok but others im not sure of 

```

titan@thedungeon:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:01 events/0
    7 ?        00:00:00 khelper
   26 ?        00:00:00 kblockd/0
   27 ?        00:00:00 kacpid
   28 ?        00:00:00 kacpi_notify
   87 ?        00:00:00 kseriod
  108 ?        00:00:05 kswapd0
  159 ?        00:00:00 aio/0
 1980 ?        00:00:00 ksuspend_usbd
 1981 ?        00:00:00 khubd
 1999 ?        00:00:09 ata/0
 2000 ?        00:00:00 ata_aux
 2029 ?        00:00:00 scsi_eh_0
 2030 ?        00:01:23 scsi_eh_1
 2384 ?        00:00:11 kjournald
 2589 ?        00:00:00 udevd
 4009 ?        00:00:00 portmap
 4027 ?        00:00:00 rpc.statd
 4154 tty4     00:00:00 getty
 4155 tty5     00:00:00 getty
 4157 tty2     00:00:00 getty
 4161 tty3     00:00:00 getty
 4162 tty1     00:00:00 getty
 4163 tty6     00:00:00 getty
 4335 ?        00:00:00 acpid
 4372 ?        00:00:00 kondemand/0
 4448 ?        00:00:00 syslogd
 4501 ?        00:00:00 dd
 4503 ?        00:00:00 klogd
 4524 ?        00:00:04 dbus-daemon
 4540 ?        00:00:00 NetworkManager
 4554 ?        00:00:00 NetworkManagerD
 4567 ?        00:00:00 system-tools-ba
 4568 ?        00:00:00 dbus-daemon
 4587 ?        00:00:02 hald
 4588 ?        00:00:00 hald-runner
 4657 ?        00:00:01 hald-addon-keyb
 4663 ?        00:00:00 hald-addon-keyb
 4664 ?        00:00:00 hald-addon-keyb
 4670 ?        00:00:00 hald-addon-acpi
 4706 ?        00:00:34 hald-addon-stor
 4793 ?        00:00:00 console-kit-dae
 4893 ?        00:00:01 dhcdbd
 4913 ?        00:00:00 hcid
 4928 ?        00:00:00 bluetoothd-serv
 4929 ?        00:00:00 bluetoothd-serv
 4932 ?        00:00:00 krfcommd
 4962 ?        00:00:00 gdm
 4965 ?        00:00:01 gdm
 4970 tty7     01:43:02 Xorg
 5007 ?        00:00:00 atd
 5021 ?        00:00:00 cron
 5137 ?        00:00:00 gnome-keyring-d
 5140 ?        00:00:00 x-session-manag
 5177 ?        00:00:00 ssh-agent
 5179 ?        00:00:05 gconfd-2
 5183 ?        00:00:07 dbus-daemon
 5185 ?        00:00:21 gnome-settings-
 5191 ?        00:03:52 metacity
 5194 ?        00:03:30 gnome-panel
 5195 ?        00:02:44 nautilus
 5199 ?        00:00:03 gnome-volume-ma
 5219 ?        00:00:00 bonobo-activati
 5222 ?        00:00:00 gnome-vfs-daemo
 5223 ?        00:00:00 vino-session
 5225 ?        00:00:00 bluetooth-apple
 5226 ?        00:01:38 beagled
 5240 ?        00:00:06 update-notifier
 5243 ?        00:00:00 evolution-alarm
 5250 ?        00:00:14 nm-applet
 5255 ?        00:00:07 python
 5259 ?        00:00:00 gnome-power-man
 5261 ?        00:09:14 gnome-screensav
 5278 ?        00:00:00 mapping-daemon
 5295 ?        00:00:08 multiload-apple
 5304 ?        00:00:04 trashapplet
 5316 ?        00:00:05 mixer_applet2
 5318 ?        00:00:30 gnome-netstatus
 5327 ?        00:00:09 notification-da
 7393 ?        00:00:00 rpciod/0
 7394 ?        00:00:00 lockd
 7400 ?        00:00:00 gam_server
 9510 pts/0    00:00:00 gnome-mount
 9512 ?        00:00:00 gnome-mount
 9521 ?        00:04:28 gksu
 9522 ?        00:00:00 sudo
 9550 ?        00:01:54 mount.ntfs-3g
16613 ?        00:00:00 mysqld_safe
16747 ?        00:06:13 mysqld
16748 ?        00:00:00 logger
16928 ?        00:00:00 pdflush
21394 ?        00:00:00 firefox
21406 ?        00:00:00 run-mozilla.sh
21410 ?        01:01:53 firefox-bin
22261 ?        00:07:23 amarokapp
22264 ?        00:00:00 kdeinit
22267 ?        00:00:00 dcopserver
22270 ?        00:00:00 klauncher
22272 ?        00:00:00 kded
22284 ?        00:00:00 kio_file
22285 ?        00:00:00 ruby
22286 ?        00:00:00 ruby
23108 ?        00:00:00 pdflush
23352 ?        00:00:00 avahi-daemon
23354 ?        00:00:00 avahi-daemon
23557 ?        00:00:00 cupsd
23878 ?        00:00:08 beagled-helper
23920 ?        00:00:03 gnome-terminal
23931 ?        00:00:00 gnome-pty-helpe
23932 pts/1    00:00:00 bash
23965 pts/1    00:00:00 ps

```
thank you for your replies!

---

### Post by ahaslam on 2008-01-16
You're the only one than can decide what you need. To give you an Idea tho, here's what I have from an Arch install with Xfce:

```
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   46 ?        00:00:00 kblockd/0
   47 ?        00:00:00 kblockd/1
   50 ?        00:00:00 kacpid
   51 ?        00:00:00 kacpi_notify
  188 ?        00:00:00 kseriod
  234 ?        00:00:00 pdflush
  235 ?        00:00:00 pdflush
  236 ?        00:00:00 kswapd0
  289 ?        00:00:00 aio/0
  290 ?        00:00:00 aio/1
  440 ?        00:00:00 rpciod/0
  441 ?        00:00:00 rpciod/1
  454 ?        00:00:00 ata/0
  455 ?        00:00:00 ata/1
  456 ?        00:00:00 ata_aux
  462 ?        00:00:02 scsi_eh_0
  464 ?        00:00:00 scsi_eh_1
  479 ?        00:00:00 scsi_eh_2
  481 ?        00:00:00 scsi_eh_3
  491 ?        00:00:00 scsi_eh_4
  493 ?        00:00:00 scsi_eh_5
  498 ?        00:00:00 scsi_eh_6
  500 ?        00:00:00 scsi_eh_7
 1522 ?        00:00:00 xfslogd/0
 1523 ?        00:00:00 xfslogd/1
 1524 ?        00:00:00 xfsdatad/0
 1525 ?        00:00:00 xfsdatad/1
 1528 ?        00:00:00 xfs_mru_cache
 1548 ?        00:00:00 xfsbufd
 1549 ?        00:00:00 xfssyncd
 1585 ?        00:00:00 ksuspend_usbd
 1591 ?        00:00:00 khubd
 1607 ?        00:00:00 udevd
 4666 ?        00:00:00 kpsmoused
 6452 ?        00:00:00 xfsbufd
 6453 ?        00:00:00 xfssyncd
 6747 ?        00:00:00 syslog-ng
 6775 tty1     00:00:00 login
 6776 tty2     00:00:00 agetty
 6777 tty3     00:00:00 agetty
 6778 tty4     00:00:00 agetty
 6779 tty5     00:00:00 agetty
 6780 tty6     00:00:00 agetty
 6853 ?        00:00:00 crond
 6856 ?        00:00:00 dbus-daemon
 6867 ?        00:00:00 portmap
 6901 ?        00:00:00 famd
 6904 ?        00:00:00 hald
 6905 ?        00:00:00 hald-runner
 6907 ?        00:00:00 cupsd
 6920 ?        00:00:00 hald-addon-inpu
 6923 ?        00:00:00 hald-addon-acpi
 6933 ?        00:00:02 hald-addon-stor
 6935 ?        00:00:00 dhcpcd
 6937 tty1     00:00:00 bash
 6943 tty1     00:00:00 startx
 6959 tty1     00:00:00 xinit
 6960 tty7     00:01:10 X
 6974 tty1     00:00:00 sh
 6986 tty1     00:00:05 dbus-launch
 6987 ?        00:00:00 dbus-daemon
 6989 tty1     00:00:00 xfce4-session
 6992 ?        00:00:00 xfce-mcs-manage
 6994 tty1     00:00:00 xfwm4
 6996 tty1     00:00:00 xfce4-panel
 6998 tty1     00:00:01 Thunar
 7000 tty1     00:00:02 xfdesktop
 7005 tty1     00:00:23 xfce4-mixer-plu
 7006 tty1     00:00:02 xfce4-clipman-p
 7007 tty1     00:00:01 xfce4-menu-plug
 7008 tty1     00:00:00 orageclock
 7010 ?        00:00:01 conky
 7416 ?        00:00:00 kjournald
 7486 ?        00:00:00 gconfd-2
 7537 ?        00:00:00 Terminal
 7538 ?        00:00:00 gnome-pty-helpe
 7539 pts/0    00:00:00 bash
 7540 pts/0    00:00:00 ps
```
Check the 'make ubuntu run like arch' link in my sig for a few tips. ;)

PS. If you're using a Nvidia card the command below will give you a noticeable performance boost in games:
```
nvidia-settings -a OpenGLImageSettings=3
```

;)

---

### Post by The Titan on 2008-01-17
i understand, that command helped a lot, what did it actually do?.

---

### Post by ahaslam on 2008-01-17
It reduced your OpenGL quality settings for maximum performance. While that's also the lowest quality, you'll have to take screenshots to notice the difference in an action game. See the nvidia-settings man page for many more tweaks. ;)

---

