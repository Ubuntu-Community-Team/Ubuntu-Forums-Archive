---
title: "strangly many processes of same kind running"
date: 2008-04-05
forum: General Help
---

### Post by jakupl on 2008-04-05
Why are there so many multiple instances of the same process?
Does ubuntu maybe have a problem killing them?

jakup@bobby:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:02 events/0
    7 ?        00:00:00 khelper
   26 ?        00:00:00 kblockd/0
   27 ?        00:00:00 kacpid
   28 ?        00:00:00 kacpi_notify
  131 ?        00:00:00 kseriod
 [B] 154 ?        00:00:00 pdflush
  155 ?        00:00:00 pdflush[/B]
  156 ?        00:00:00 kswapd0
  207 ?        00:00:00 aio/0
 1975 ?        00:00:00 ksuspend_usbd
 1976 ?        00:00:00 khubd
 2010 ?        00:00:00 ata/0
 2011 ?        00:00:00 ata_aux
 2419 ?        00:00:00 kjournald
 2696 ?        00:00:00 udevd
 3567 ?        00:00:00 kpsmoused
 3622 ?        00:00:00 pccardd
 3668 ?        00:00:00 kmmcd
 3700 ?        00:00:00 irda_sir_wq
 4201 ?        00:00:00 portmap
 4220 ?        00:00:00 rpc.statd
[B] 4398 tty4     00:00:00 getty
 4399 tty5     00:00:00 getty
 4402 tty2     00:00:00 getty
 4403 tty3     00:00:00 getty
 4404 tty1     00:00:00 getty
 4405 tty6     00:00:00 getty[/B]
 4606 ?        00:00:00 acpid
 4651 ?        00:00:00 kondemand/0
 4713 ?        00:00:00 syslogd
 4770 ?        00:00:00 dd
 4772 ?        00:00:00 klogd
 4793 ?        00:00:00 dbus-daemon
 4809 ?        00:00:00 NetworkManager
 4823 ?        00:00:00 NetworkManagerD
 4836 ?        00:00:00 system-tools-ba
 4837 ?        00:00:00 dbus-daemon
 4856 ?        00:00:00 hald
 4857 ?        00:00:00 hald-runner
[B] 4931 ?        00:00:00 hald-addon-keyb
 4935 ?        00:00:00 hald-addon-keyb[/B]
 4938 ?        00:00:00 hald-addon-acpi
[B] 4941 ?        00:00:00 hald-addon-keyb
 4942 ?        00:00:00 hald-addon-keyb
 4946 ?        00:00:00 hald-addon-keyb[/B]
 4968 ?        00:00:00 hald-addon-stor
 4969 ?        00:00:00 cupsd
 5299 ?        00:00:00 exim4
 5402 ?        00:00:00 lockd
 5403 ?        00:00:00 rpciod/0
 5407 ?        00:00:00 nfsd4
[B] 5408 ?        00:00:00 nfsd
 5409 ?        00:00:00 nfsd
 5410 ?        00:00:00 nfsd
 5411 ?        00:00:00 nfsd
 5412 ?        00:00:00 nfsd
 5413 ?        00:00:00 nfsd
 5414 ?        00:00:00 nfsd
 5415 ?        00:00:00 nfsd[/B]
 5419 ?        00:00:00 rpc.mountd
 5489 ?        00:00:00 nmbd
 5507 ?        00:00:00 smbd
 5558 ?        00:00:00 console-kit-dae
 5643 ?        00:00:00 avahi-daemon
 5644 ?        00:00:00 avahi-daemon
 5674 ?        00:00:00 smbd
 5675 ?        00:00:00 dhcdbd
 5714 ?        00:00:00 krfcommd
 5744 ?        00:00:00 gdm
 5747 ?        00:00:00 gdm
 5752 tty7     00:00:14 Xorg
 5808 ?        00:00:00 dhclient
 5809 ?        00:00:00 ntpd
 5858 tty7     00:00:00 Xorg
 5859 ?        00:00:00 atd
 5873 ?        00:00:00 cron
 5994 ?        00:00:00 timidity
 6811 ?        00:00:00 gnome-keyring-d
 6814 ?        00:00:00 x-session-manag
 6868 ?        00:00:00 Xgl-lockfile-wr
 6873 ?        00:06:01 Xgl
 6878 ?        00:00:00 ssh-agent
 6880 ?        00:00:00 gconfd-2
 6884 ?        00:00:00 dbus-daemon
 6886 ?        00:00:00 gnome-settings-
 6892 ?        00:00:07 metacity
 6894 ?        00:00:07 gnome-panel
 6896 ?        00:00:01 nautilus
 6904 ?        00:00:00 bonobo-activati
 6908 ?        00:00:00 gnome-vfs-daemo
 6909 ?        00:00:00 gnome-volume-ma
 6912 ?        00:00:00 vino-session
 6913 ?        00:00:00 bluetooth-apple
 6916 ?        00:00:00 update-notifier
 6925 ?        00:00:06 skype
 6927 ?        00:00:00 trackerd
 6930 ?        00:00:03 python
 6933 ?        00:00:00 nm-applet
 6939 ?        00:00:00 gnome-power-man
 6943 ?        00:00:08 gnome-screensav
 6971 ?        00:00:00 evolution-data-
 6977 ?        00:00:00 evolution-excha
 7000 ?        00:00:00 trashapplet
 7015 ?        00:00:00 mapping-daemon
 7032 ?        00:00:01 gweather-applet
 7034 ?        00:00:01 fast-user-switc
 7036 ?        00:00:00 mixer_applet2
 7038 ?        00:00:01 deskbar-applet
 7065 ?        00:00:00 charpick_applet
 7153 ?        00:00:06 evolution
 7182 ?        00:00:00 evolution-alarm
 7212 ?        00:00:00 firefox
 7225 ?        00:00:00 run-mozilla.sh
 7229 ?        00:04:48 firefox-bin
 7650 ?        00:01:30 rhythmbox
 7843 ?        00:00:01 gnome-terminal
 7845 ?        00:00:00 gnome-pty-helpe
 7846 pts/0    00:00:00 bash
 8507 pts/0    00:00:00 ps

---

### Post by kaivalagi on 2008-04-05
multiple getty's for each terminal you have available (tty1 accessible via Ctrl-Alt-F1 for example, Ctrl-Alt-F7 to get you back!)

I am guessing that the multiple nfsd processes are for the network file system service. Apache can do the same thing (default I think), to allow for simultaneous execution (processes rather than threads).

I see the same duplicates when I list my processes...

---

### Post by jakupl on 2008-04-05
okay, nice to know :) thanks

---

