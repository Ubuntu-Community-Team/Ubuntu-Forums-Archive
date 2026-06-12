---
title: "There is a strange file that just appeared in my home folder called azScript"
date: 2007-09-30
forum: General Help
---

### Post by feisty_hot_lover on 2007-09-30
I noticed this strange file just now in my home folder.  It's called azScript and right clicking in Nautilus I see that it's listed as plain text document and the rights are mine and allow executing as program is set.  The content of the file is:

> echo "Passing startup args to already-running Azureus java process listening on [127.0.0.1: 6880]"
exit

I am a bit concerned about the part where it says passing args.  Is this safe or malicious.  I am running Gutsy.  I also have this in my logs debug and kern and syslog:

> Sep 30 14:52:33 ubuntu kernel: [ 4483.430829] UDP: short packet: From 209.222.2.2:33623 35269/50 to 192.168.1.100:37868

Output of ps fax
```
ps fax
  PID TTY      STAT   TIME COMMAND
    2 ?        S<     0:00 [kthreadd]
    3 ?        S<     0:00  \_ [migration/0]
    4 ?        SN     0:00  \_ [ksoftirqd/0]
    5 ?        S<     0:00  \_ [watchdog/0]
    6 ?        S<     0:00  \_ [migration/1]
    7 ?        SN     0:00  \_ [ksoftirqd/1]
    8 ?        S<     0:00  \_ [watchdog/1]
    9 ?        S<     0:00  \_ [events/0]
   10 ?        S<     0:00  \_ [events/1]
   11 ?        S<     0:00  \_ [khelper]
   31 ?        S<     0:00  \_ [kblockd/0]
   32 ?        S<     0:00  \_ [kblockd/1]
   33 ?        S<     0:00  \_ [kacpid]
   34 ?        S<     0:00  \_ [kacpi_notify]
  128 ?        S<     0:00  \_ [kseriod]
  153 ?        S      0:00  \_ [pdflush]
  154 ?        S      0:00  \_ [pdflush]
  155 ?        S<     0:00  \_ [kswapd0]
  206 ?        S<     0:00  \_ [aio/0]
  207 ?        S<     0:00  \_ [aio/1]
 1995 ?        S<     0:00  \_ [ksuspend_usbd]
 1996 ?        S<     0:00  \_ [khubd]
 2041 ?        S<     0:00  \_ [ata/0]
 2042 ?        S<     0:00  \_ [ata/1]
 2051 ?        S<     0:00  \_ [ata_aux]
 2144 ?        S<     0:00  \_ [khpsbpkt]
 2157 ?        S<     0:00  \_ [scsi_eh_0]
 2158 ?        S<     0:00  \_ [scsi_eh_1]
 2250 ?        S<     0:00  \_ [scsi_eh_2]
 2251 ?        S<     0:00  \_ [scsi_eh_3]
 2266 ?        S<     0:00  \_ [knodemgrd_0]
 2580 ?        S<     0:00  \_ [kjournald]
 3810 ?        S<     0:00  \_ [kpsmoused]
 3885 ?        S<     0:00  \_ [kgameportd]
 3947 ?        S<     0:00  \_ [cx88 tvaudio]
 4846 ?        S<     0:00  \_ [kondemand/0]
 4847 ?        S<     0:00  \_ [kondemand/1]
 7369 ?        S<     0:00  \_ [krfcommd]
    1 ?        Ss     0:01 /sbin/init
 2777 ?        S<s    0:00 /sbin/udevd --daemon
 4357 ?        Ss     0:00 /sbin/mount.ntfs /dev/sda1 /media/sda1 -o rw,nls=utf8
 4360 ?        Ss     0:00 /sbin/mount.ntfs /dev/sdb1 /media/sdb1 -o rw,nls=utf8
 4597 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 4598 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 4600 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 4602 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 4604 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 4605 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 4788 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid
 4916 ?        Ss     0:00 /sbin/syslogd -u syslog
 4970 ?        S      0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 4972 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 4993 ?        Ss     0:01 /usr/bin/dbus-daemon --system
 5009 ?        Ssl    0:01 /usr/sbin/NetworkManager --pid-file /var/run/NetworkM
 5023 ?        Ss     0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/ru
 5036 ?        Ss     0:00 /usr/bin/system-tools-backends
 5037 ?        S      0:00  \_ dbus-daemon --session --print-address --nofork
 5053 ?        Ss     0:01 /usr/sbin/hald
 5054 ?        S      0:00  \_ hald-runner
 5115 ?        S      0:00      \_ hald-addon-keyboard: listening on /dev/input/
 5116 ?        S      0:00      \_ hald-addon-keyboard: listening on /dev/input/
 5117 ?        S      0:00      \_ hald-addon-keyboard: listening on /dev/input/
 5120 ?        S      0:00      \_ hald-addon-acpi: listening on acpid socket /v
 5125 ?        S      0:00      \_ hald-addon-hid-ups: listening on /dev/usb/hid
 5162 ?        S      0:00      \_ hald-addon-storage: polling /dev/scd0 (every 
 5191 ?        S      0:00      \_ hald-addon-storage: polling /dev/scd1 (every 
 5703 ?        Ss     0:00 /usr/sbin/gdm
 5715 ?        S      0:00  \_ /usr/sbin/gdm
 5734 tty7     SLs+   4:42      \_ /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm
12092 ?        Ssl    0:00      \_ x-session-manager
12131 ?        Ss     0:00          \_ /usr/bin/ssh-agent x-session-manager
12147 ?        S      0:09          \_ /usr/bin/metacity --sm-client-id=default0
12149 ?        S      0:07          \_ gnome-panel --sm-client-id default1
12151 ?        S      0:09          \_ nautilus --no-default-window --sm-client-
12162 ?        S      0:00          \_ vino-session --sm-client-id default5
12165 ?        S      0:00          \_ bluetooth-applet
12168 ?        S      0:00          \_ update-notifier
12182 ?        Sl     0:00          \_ /usr/lib/evolution/2.12/evolution-alarm-n
12184 ?        SNl    0:06          \_ trackerd
12190 ?        S      0:00          \_ nm-applet --sm-disable
12192 ?        S      0:00          \_ python /usr/share/system-config-printer/a
 6497 ?        Ss     0:00 /usr/sbin/cupsd
 7094 ?        Ssl    0:00 /usr/sbin/console-kit-daemon
 7256 ?        Ss     0:00 avahi-daemon: running [ubuntu.local]
 7258 ?        Ss     0:00  \_ avahi-daemon: chroot helper
 7325 ?        Ss     0:00 /usr/sbin/dhcdbd --system
 7934 ?        S      0:00  \_ /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth
 7351 ?        Ss     0:00 /usr/sbin/hcid -x -s
 7363 ?        S      0:00  \_ /usr/lib/bluetooth/bluetoothd-service-input
 7373 ?        S      0:00  \_ /usr/lib/bluetooth/bluetoothd-service-audio
 7404 ?        Ss     0:00 /usr/sbin/atd
 7418 ?        Ss     0:00 /usr/sbin/cron
12089 ?        SL     0:00 /usr/bin/gnome-keyring-daemon -d
12133 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2 6
12137 ?        Ss     0:00 dbus-daemon --fork --print-address 17 --print-pid 19
12139 ?        Sl     0:01 /usr/lib/gnome-control-center/gnome-settings-daemon
12158 ?        Ss     0:00 gnome-volume-manager --sm-client-id default4
12160 ?        Ssl    0:00 /usr/lib/bonobo-activation/bonobo-activation-server -
12164 ?        S      0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
12194 ?        Ss     0:00 gnome-power-manager
12200 ?        Ss     0:10 gnome-screensaver
12223 ?        Sl     0:00 /usr/lib/evolution/evolution-data-server-1.12 --oaf-a
12231 ?        Sl     0:00 /usr/lib/evolution/2.12/evolution-exchange-storage --
12233 ?        S      0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
12236 ?        S      0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid
12279 ?        Sl     0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-i
13273 ?        S      0:00 /bin/bash /opt/azureus/azureus
13323 ?        Sl     2:01  \_ java -Xmx128m -cp ./Azureus2.jar:./swt.jar -Djava
15102 ?        S      0:00 /bin/sh /usr/bin/firefox
15114 ?        S      0:00  \_ /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/
15118 ?        Sl     0:43      \_ /usr/lib/firefox/firefox-bin
15460 ?        Sl     0:00 gnome-terminal
15466 ?        S      0:00  \_ gnome-pty-helper
15467 pts/0    Ss     0:00  \_ bash
15485 pts/0    R+     0:00      \_ ps fax
```

---

### Post by chuckyp on 2007-09-30
It appears to be an azureus file to configuring something during the startup of azureus.

---

### Post by feisty_hot_lover on 2007-10-01
> **chuckyp said:**
> It appears to be an azureus file to configuring something during the startup of azureus.Thanks for the reply.  Further research has  led me to see that this is a startup file for azureus and in itself it is normal.  But it don't explain why it got on my desktop.  I'll ask on the irc for azureus if this is suppose to show up on the desktop.  Quite the panic for me there.

---

