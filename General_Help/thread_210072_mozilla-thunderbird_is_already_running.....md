---
title: "mozilla-thunderbird is already running...."
date: 2006-07-06
forum: General Help
---

### Post by mttolmie on 2006-07-06
m-t displays an error message the start of which i show in the title on launching. In fact no such process is running. The behaviour came right out of the box, i.e. on a fresh install of Dapper 6.06. Uninstall and re-install did not help.
JNik mentioned this problem 4 weeks ago; perhaps he can describe his solution in more detail. For example, I do not have a profile because I never got beyind the error message.
This problem is keeping me from switching my main activities from Breezy on an old machine to Dapper on a shiny faster box:(

---

### Post by beniwtv on 2006-07-06
Could you post the output of "ps ax" on the terminal?

---

### Post by mk1970 on 2006-07-06
[QUOTE=mttolmie]m-t displays an error message the start of which i show in the title on launching. In fact no such process is running.[/QUOTE]

I have to run this before staring Firefox or Thunderbird (my home directory is NFS mounted):

```
rm -f .mozilla/firefox/*/.parentlock .mozilla-thunderbird/*/.parentlock
```

---

### Post by mttolmie on 2006-07-06
To the second responder, I foud one lock deep in firebird, i removed it, not effect (I will try a reboot later). 
To the first responder:
  PID TTY      STAT   TIME COMMAND
    1 ?        S      0:01 init [2]
    2 ?        SN     0:00 [ksoftirqd/0]
    3 ?        S      0:00 [watchdog/0]
    4 ?        S<     0:00 [events/0]
    5 ?        S<     0:00 [khelper]
    6 ?        S<     0:00 [kthread]
    8 ?        S<     0:00 [kblockd/0]
    9 ?        S<     0:00 [kacpid]
  121 ?        S      0:00 [pdflush]
  122 ?        S      0:00 [pdflush]
  124 ?        S<     0:00 [aio/0]
  123 ?        S      0:00 [kswapd0]
  711 ?        S<     0:00 [kseriod]
 1490 ?        S<     0:00 [ata/0]
 1491 ?        S<     0:00 [scsi_eh_0]
 1492 ?        S<     0:00 [scsi_eh_1]
 1636 ?        S<     0:00 [khubd]
 1873 ?        S      0:00 [kjournald]
 2100 ?        S<s    0:00 /sbin/udevd --daemon
 2862 ?        S      0:00 [shpchpd_event]
 2931 ?        S      0:00 [khpsbpkt]
 2938 ?        S      0:00 [knodemgrd_0]
 2941 ?        S<     0:00 [kgameportd]
 3408 ?        S<     0:00 [ktxnmgrd:sda5:w]
 3409 ?        S<     0:00 [ent:sda5.]
 3410 ?        S      0:00 [kjournald]
 3535 ?        S<s    0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
 3959 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
 4075 ?        Ss     0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 4077 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 4096 ?        Ss     0:02 /usr/bin/dbus-daemon --system
 4111 ?        Ss     0:01 /usr/sbin/hald
 4112 ?        S      0:00 hald-runner
 4117 ?        S      0:00 /usr/lib/hal/hald-addon-acpi
 4127 ?        S      0:00 /usr/lib/hal/hald-addon-keyboard
 4133 ?        S      0:05 /usr/lib/hal/hald-addon-storage
 4134 ?        S      0:05 /usr/lib/hal/hald-addon-storage
 4167 ?        Ss     0:00 /usr/sbin/gdm
 4168 ?        S      0:00 /usr/sbin/gdm
 4171 tty7     Ss+   13:15 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 4242 ?        Ssl    0:00 /usr/sbin/hpiod
 4246 ?        S      0:00 python /usr/sbin/hpssd
 4329 ?        Ss     0:00 /usr/sbin/sshd
 4369 ?        Ss     0:00 hcid: processing events
 4375 ?        Ss     0:00 /usr/sbin/sdpd
 4384 ?        S<     0:00 [krfcommd]
 4397 ?        Ss     0:00 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -s
 4431 ?        Ss     0:00 /usr/sbin/atd
 4444 ?        Ss     0:00 /usr/sbin/cron
 4510 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 4511 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 4512 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 4513 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 4514 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 4515 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 4534 ?        Ss     0:00 x-session-manager
 4576 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
 4579 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
 4580 ?        Ss     0:00 dbus-daemon --fork --print-pid 8 --print-address 6 --session
 4582 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2 5
 4585 ?        S      0:00 /usr/bin/gnome-keyring-daemon
 4587 ?        Ss     0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=17
 4589 ?        Sl     0:01 /usr/lib/control-center/gnome-settings-daemon --oaf-activate-iid=OAFIID:GNOME_SettingsDaemon --oaf-ior-fd=25
 4591 ?        Ss     0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 18
 4597 ?        Ss     0:04 /usr/bin/metacity --sm-client-id=default0
 4602 ?        Ssl    0:04 gnome-panel --sm-client-id default1
 4604 ?        Ssl    0:02 nautilus --no-default-window --sm-client-id default2
 4609 ?        Ss     0:02 gnome-volume-manager --sm-client-id default4
 4615 ?        Ss     0:01 update-notifier
 4619 ?        Ss     1:46 gnome-cups-icon --sm-client-id default3
 4624 ?        Sl     0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon --oaf-activate-iid=OAFIID:GNOME_VFS_Daemon_Factory --oaf-ior-fd=31
 4626 ?        Sl     0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=32
 4632 ?        Ss     0:00 gnome-power-manager
 4650 ?        S      0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
 4653 ?        S      0:01 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=31
 4655 ?        S      0:01 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=38
 4663 ?        S      0:00 /usr/lib/notification-daemon/notification-daemon
 4673 ?        Ss     0:01 gnome-screensaver
 4687 ?        Sl     0:09 gnome-terminal
 4688 ?        S      0:00 gnome-pty-helper
 4689 pts/0    Ss     0:00 bash
 4712 pts/0    S+     0:00 mc
 4714 pts/1    Ss+    0:00 bash -rcfile .bashrc
 4786 pts/2    Ss     0:00 bash
 4805 pts/2    S+     0:00 mc
 4807 pts/3    Ss     0:00 bash -rcfile .bashrc
 4846 pts/3    S     18:27 squeak Next-Gen-Medical-Project.3.image
 4882 ?        Ss     0:00 /usr/local/bin/tnos
14460 ?        Sl     6:19 /usr/lib/firefox/firefox-bin -a firefox
32679 ?        SNs    0:06 /usr/sbin/cupsd
32761 ?        RNs    0:00 /sbin/syslogd -u syslog
 5616 pts/3    R+     0:00 ps ax

---

