---
title: "Zoombie Process upon startup"
date: 2008-05-10
forum: General Help
---

### Post by enoughsaid05 on 2008-05-10
I am listing the output of ps -e

 PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   39 ?        00:00:00 kblockd/0
   42 ?        00:00:00 kacpid
   43 ?        00:00:00 kacpi_notify
  134 ?        00:00:00 kseriod
  179 ?        00:00:00 pdflush
  180 ?        00:00:00 pdflush
  181 ?        00:00:00 kswapd0
  224 ?        00:00:00 aio/0
 1500 ?        00:00:00 ata/0
 1503 ?        00:00:00 ata_aux
 1510 ?        00:00:00 ksuspend_usbd
 1518 ?        00:00:00 khubd
 1525 ?        00:00:00 scsi_eh_0
 1531 ?        00:00:00 scsi_eh_1
 3531 ?        00:00:00 kjournald
 3811 ?        00:00:00 udevd
 4146 ?        00:00:00 kmmcd
 4158 ?        00:00:00 pccardd
 4176 ?        00:00:00 kpsmoused
 5575 tty4     00:00:00 getty
 5576 tty5     00:00:00 getty
 5580 tty2     00:00:00 getty
 5581 tty3     00:00:00 getty
 5583 tty6     00:00:00 getty
 5767 ?        00:00:00 acpid
 5812 ?        00:00:00 kondemand/0
 5872 ?        00:00:00 syslogd
 5925 ?        00:00:00 dd
 5927 ?        00:00:00 klogd
 5949 ?        00:00:00 dbus-daemon
 5965 ?        00:00:01 NetworkManager
 5979 ?        00:00:00 NetworkManagerD
 5992 ?        00:00:00 system-tools-ba
 6012 ?        00:00:00 avahi-daemon
 6013 ?        00:00:00 avahi-daemon
 6042 ?        00:00:00 cupsd
 6061 ?        00:00:00 atieventsd
 6163 ?        00:00:00 freshclam
 6271 ?        00:00:00 dhcdbd
 6290 ?        00:00:00 hald
 6293 ?        00:00:00 console-kit-dae
 6355 ?        00:00:00 hald-runner
 6379 ?        00:00:00 hald-addon-cpuf
 6380 ?        00:00:00 hald-addon-acpi
 6381 ?        00:00:00 hald-addon-inpu
 6397 ?        00:00:00 hald-addon-stor
 6420 ?        00:00:00 hcid
 6428 ?        00:00:00 btaddconn
 6429 ?        00:00:00 btdelconn
 6441 ?        00:00:00 bluetoothd-serv
 6448 ?        00:00:00 bluetoothd-serv
 6459 ?        00:00:00 krfcommd
 6517 ?        00:00:00 gdm
 6520 ?        00:00:00 gdm
 6524 tty7     00:08:22 Xorg
 6577 ?        00:00:00 atd
 6591 ?        00:00:00 cron
 6692 tty1     00:00:00 getty
 6698 tty7     00:00:00 Xorg
 6716 ?        00:00:02 gconfd-2
 6718 ?        00:00:00 gnome-keyring-d
 6719 ?        00:00:00 x-session-manag
 6827 ?        00:00:00 seahorse-agent
 6833 ?        00:00:00 dbus-daemon
 6834 ?        00:00:02 gnome-settings-
 6846 ?        00:00:07 pulseaudio
 6849 ?        00:00:00 gconf-helper
 6863 ?        00:00:07 gnome-screensav
 6864 ?        00:00:05 metacity
 6866 ?        00:00:06 gnome-panel
 6867 ?        00:00:03 nautilus
 6874 ?        00:00:00 bonobo-activati
 6877 ?        00:00:00 gvfsd
 6881 ?        00:00:00 bluetooth-apple
 6885 ?        00:00:00 update-notifier
 6888 ?        00:00:00 tracker-applet
 6890 ?        00:00:00 evolution-alarm
 6897 ?        00:00:00 trackerd
 6899 ?        00:00:00 python
 6900 ?        00:00:00 gnome-volume-ma
 6901 ?        00:00:04 nm-applet
 6903 ?        00:00:00 gnome-power-man
 6910 ?        00:00:00 evolution-data-
 6971 ?        00:00:00 wpa_supplicant
 6979 ?        00:00:00 trashapplet
 6985 ?        00:00:00 gvfsd-burn
 6990 ?        00:00:00 gvfsd-trash
 7018 ?        00:00:00 stickynotes_app
 7021 ?        00:00:00 gnome-dictionar
 7024 ?        00:00:00 mixer_applet2
 7027 ?        00:00:01 deskbar-applet
 7030 ?        00:00:00 fast-user-switc
 7038 ?        00:00:00 dhclient
 7313 ?        00:00:00 sh <defunct>
 7319 ?        00:00:00 sh <defunct>
 7321 ?        00:00:00 sh <defunct>
 7334 ?        00:00:00 gnome-vfs-daemo
 7350 ?        00:03:37 firefox
 7372 ?        00:00:16 python
 7395 ?        00:00:00 gnome-open <defunct>
10795 ?        00:00:16 gnome-system-mo
10843 ?        00:00:00 gnome-terminal
10846 ?        00:00:00 gnome-pty-helpe
10847 pts/0    00:00:00 bash

Why is it that at least 2 sh zoombie processes are running upon startup? How do I make sure that they do not run?

---

