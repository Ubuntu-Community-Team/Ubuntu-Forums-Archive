---
title: "Software Management tools . . ."
date: 2007-05-20
forum: General Help
---

### Post by orgrimdoom on 2007-05-20
I have Ubuntu fiesty 

and i was able to install programs fine in the beginning.

but now whenever i try to run one of the different installers, it tells me that a installer is already in use and that i cannot use it.

i have restarted the machine several times now before trying again

here is the error the package installer for .deb's gives me

ERROR
_________________________________________________________

Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'Update Manager', 'aptitude' or 'Synaptic' first.

---

### Post by taurus on 2007-05-20
What's the output of this command from a terminal?

```
ps -A
```

---

### Post by orgrimdoom on 2007-05-20
PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 migration/1
    6 ?        00:00:00 ksoftirqd/1
    7 ?        00:00:00 watchdog/1
    8 ?        00:00:00 events/0
    9 ?        00:00:00 events/1
   10 ?        00:00:00 khelper
   11 ?        00:00:00 kthread
   35 ?        00:00:00 kblockd/0
   36 ?        00:00:00 kblockd/1
   37 ?        00:00:00 kacpid
   38 ?        00:00:00 kacpi_notify
  190 ?        00:00:00 kseriod
  219 ?        00:00:00 pdflush
  220 ?        00:00:00 pdflush
  221 ?        00:00:00 kswapd0
  222 ?        00:00:00 aio/0
  223 ?        00:00:00 aio/1
  849 ?        00:00:00 kirqd
 2099 ?        00:00:00 ksuspend_usbd
 2100 ?        00:00:00 khubd
 2174 ?        00:00:00 khpsbpkt
 2250 ?        00:00:00 ata/0
 2251 ?        00:00:00 ata/1
 2252 ?        00:00:00 ata_aux
 2270 ?        00:00:00 knodemgrd_0
 2295 ?        00:00:00 scsi_eh_0
 2296 ?        00:00:00 scsi_eh_1
 2314 ?        00:00:00 scsi_eh_2
 2315 ?        00:00:00 usb-storage
 2353 ?        00:00:00 scsi_eh_3
 2354 ?        00:00:00 scsi_eh_4
 2557 ?        00:00:00 kjournald
 2757 ?        00:00:00 udevd
 3766 ?        00:00:00 kpsmoused
 3913 ?        00:00:00 hda_codec
 4566 tty4     00:00:00 getty
 4567 tty5     00:00:00 getty
 4569 tty2     00:00:00 getty
 4572 tty3     00:00:00 getty
 4573 tty1     00:00:00 getty
 4574 tty6     00:00:00 getty
 4841 ?        00:00:00 acpid
 4942 ?        00:00:00 syslogd
 4995 ?        00:00:00 dd
 4997 ?        00:00:00 klogd
 5018 ?        00:00:00 dbus-daemon
 5034 ?        00:00:02 hald
 5035 ?        00:00:00 hald-runner
 5041 ?        00:00:00 hald-addon-acpi
 5042 ?        00:00:00 hald-addon-cpuf
 5049 ?        00:00:00 hald-addon-keyb
 5058 ?        00:00:00 hald-addon-keyb
 5061 ?        00:00:00 hald-addon-keyb
 5072 ?        00:00:00 hald-addon-stor
 5077 ?        00:00:00 hald-addon-stor
 5079 ?        00:00:00 hald-addon-stor
 5081 ?        00:00:00 hald-addon-stor
 5083 ?        00:00:00 hald-addon-stor
 5096 ?        00:00:00 dhcdbd
 5111 ?        00:00:00 NetworkManager
 5129 ?        00:00:00 avahi-daemon
 5130 ?        00:00:00 avahi-daemon
 5143 ?        00:00:00 NetworkManagerD
 5156 ?        00:00:00 system-tools-ba
 5157 ?        00:00:00 dbus-daemon
 5191 ?        00:00:00 gdm
 5192 ?        00:00:00 gdm
 5195 tty7     00:00:05 Xorg
 5241 ?        00:00:00 cupsd
 5265 ?        00:00:00 hpiod
 5270 ?        00:00:00 python
 5332 ?        00:00:00 kondemand/0
 5333 ?        00:00:00 kondemand/1
 5370 ?        00:00:00 hcid
 5390 ?        00:00:00 krfcommd
 5425 ?        00:00:00 atd
 5439 ?        00:00:00 cron
 5540 ?        00:00:00 x-session-manag
 5578 ?        00:00:00 ssh-agent
 5581 ?        00:00:00 dbus-launch
 5582 ?        00:00:00 dbus-daemon
 5584 ?        00:00:00 gconfd-2
 5587 ?        00:00:00 gnome-keyring-d
 5589 ?        00:00:00 gnome-settings-
 5596 ?        00:00:00 sh
 5597 ?        00:00:00 esd
 5604 ?        00:00:01 gnome-panel
 5610 ?        00:00:00 nautilus
 5613 ?        00:00:00 bonobo-activati
 5616 ?        00:00:00 gnome-vfs-daemo
 5617 ?        00:00:00 gnome-volume-ma
 5630 ?        00:00:00 update-notifier
 5633 ?        00:00:00 beryl-manager
 5641 ?        00:00:00 evolution-alarm
 5647 ?        00:00:00 nm-applet
 5648 ?        00:00:00 gnome-power-man
 5649 ?        00:00:00 gnome-cups-icon
 5691 ?        00:00:00 mapping-daemon
 5733 ?        00:00:00 emerald
 5736 ?        00:00:02 beryl
 5739 ?        00:00:00 trashapplet
 5796 ?        00:00:00 mixer_applet2
 5807 ?        00:00:02 firefox-bin
 5824 ?        00:00:00 gnome-screensav
 5878 ?        00:00:00 gnome-terminal
 5880 ?        00:00:00 gnome-pty-helpe
 5881 pts/0    00:00:00 bash
 5898 pts/0    00:00:00 ps


this is what is shown

---

### Post by orgrimdoom on 2007-05-22
any ideas of what happened?

---

