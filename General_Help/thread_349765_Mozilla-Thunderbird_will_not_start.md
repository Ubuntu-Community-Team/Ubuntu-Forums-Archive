---
title: "Mozilla-Thunderbird will not start"
date: 2007-01-30
forum: General Help
---

### Post by maguro on 2007-01-30
I have a multi OS PC (dual AMD 64 cpus), running Win XP, Gentoo, and Ununtu 6.06. I have a single shared Thunderbird mail profile used by all three systems. It is in a fat32 partition. Well it is "Used" by Windows and Gentoo. I can't get Thunderbird to work with it on Ubuntu to save my life, and I can't find any trace of an error in any logs. 

If I start the application from a terminal window, I get no messages at all just a new line. I am attaching the resulat of starting Thunderbird from a terminal window followed by ps ax. Does anyone have a clue what the problem might be, or where Thunderbird might be hiding a log entry.

roroger@Blackie:/etc/init.d$ ps ax
  PID TTY      STAT   TIME COMMAND
    1 ?        S      0:00 init [2]
    2 ?        S      0:00 [migration/0]
    3 ?        SN     0:18 [ksoftirqd/0]
    4 ?        S      0:00 [watchdog/0]
    5 ?        S      0:00 [migration/1]
    6 ?        SN     0:00 [ksoftirqd/1]
    7 ?        S      0:00 [watchdog/1]
    8 ?        S<     0:00 [events/0]
    9 ?        S<     0:00 [events/1]
   10 ?        S<     0:00 [khelper]
   11 ?        S<     0:00 [kthread]
   15 ?        S<     0:00 [kblockd/0]
   16 ?        S<     0:00 [kblockd/1]
   17 ?        S<     0:00 [kacpid]
  182 ?        S      0:22 [pdflush]
  183 ?        S      0:12 [pdflush]
  185 ?        S<     0:00 [aio/0]
  186 ?        S<     0:00 [aio/1]
  184 ?        S      0:17 [kswapd0]
  780 ?        S<     0:00 [kseriod]
 1832 ?        S<     0:00 [ata/0]
 1833 ?        S<     0:00 [ata/1]
 1834 ?        S<     0:00 [ata_hotplug/0]
 1835 ?        S<     0:00 [ata_hotplug/1]
 1840 ?        S<     0:00 [scsi_eh_0]
 1841 ?        S<     0:00 [scsi_eh_1]
 1844 ?        S<     0:00 [scsi_eh_2]
 1845 ?        S<     0:00 [scsi_eh_3]
 2048 ?        S<     0:00 [khubd]
 2215 ?        S      0:00 [kjournald]
 2451 ?        S<s    0:00 /sbin/udevd --daemon
 3295 ?        S<s    0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
 3391 ?        S      0:00 [shpchpd_event]
 3526 ?        S<     0:00 [scsi_eh_4]
 3527 ?        S<     0:06 [usb-storage]
 3542 ?        S<     0:00 [kgameportd]
 4077 ?        S      0:00 [kjournald]
 4078 ?        S      0:00 [kjournald]
 4079 ?        S      0:00 [kjournald]
 4080 ?        S      0:00 [kjournald]
 4081 ?        S      0:00 [kjournald]
 4504 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
 4631 ?        Ss     0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 4633 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 4653 ?        Ss     0:03 /usr/bin/dbus-daemon --system
 4668 ?        Ss     0:02 /usr/sbin/hald
 4669 ?        S      0:00 hald-runner
 4674 ?        S      0:00 /usr/lib/hal/hald-addon-acpi
 4725 ?        S      0:00 /usr/lib/hal/hald-addon-keyboard
 4735 ?        S      0:00 /usr/lib/hal/hald-addon-storage
 4736 ?        S      0:00 /usr/lib/hal/hald-addon-storage
 4740 ?        S      0:02 /usr/lib/hal/hald-addon-storage
 4741 ?        S      0:02 /usr/lib/hal/hald-addon-storage
 4743 ?        S      0:00 /usr/lib/hal/hald-addon-storage
 4744 ?        S      0:00 /usr/lib/hal/hald-addon-storage
 5082 ?        Ss     0:00 /usr/sbin/gdm
 5101 ?        S      0:00 /usr/sbin/gdm
 5108 tty7     Ss+   16:46 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 5125 ?        Ssl    0:00 /usr/sbin/hpiod
 5129 ?        S      0:00 python /usr/sbin/hpssd
 5192 ?        Ss    27:34 /usr/bin/gkrellmd
 5225 ?        SNs    0:00 /usr/sbin/powernowd -q
 5277 ?        Ss     0:00 hcid: processing events
 5281 ?        Ss     0:00 /usr/sbin/sdpd
 5302 ?        S<     0:00 [krfcommd]
 5315 ?        Ss     0:00 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -s
 5349 ?        Ss     0:00 /usr/sbin/atd
 5362 ?        Ss     0:00 /usr/sbin/cron
 5434 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 5435 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 5436 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 5437 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 5438 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 5439 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 5469 ?        Ss     0:00 x-session-manager
 5511 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
 5514 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
 5515 ?        Ss     0:00 dbus-daemon --fork --print-pid 8 --print-address 6 --session
 5517 ?        S      0:01 /usr/lib/libgconf2-4/gconfd-2 5
 5520 ?        S      0:00 /usr/bin/gnome-keyring-daemon
 5522 ?        Ss     0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=17
 5524 ?        Sl     0:03 /usr/lib/control-center/gnome-settings-daemon --oaf-activate-iid=OAFIID:GNOME_SettingsDaem 5526 ?        Ss     0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 18
 5534 ?        Ss     0:38 /usr/bin/metacity --sm-client-id=default0
 5540 ?        Ssl    0:23 gnome-panel --sm-client-id default1
 5542 ?        Ssl    0:54 nautilus --no-default-window --sm-client-id default2
 5545 ?        Ss     0:01 gnome-volume-manager --sm-client-id default4
 5562 ?        Sl     0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon --oaf-activate-iid=OAFIID:GNOME_VFS_Daemon_Factory 5564 ?        Ss     0:01 update-notifier
 5572 ?        Ss     0:00 gnome-cups-icon --sm-client-id default3
 5577 ?        Ss     0:00 gnome-power-manager
 5582 ?        Sl     0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Facto 5610 ?        S      0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
 5614 ?        S      0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oa 5623 ?        S      0:01 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory - 5637 ?        Ss     0:05 gnome-screensaver
 5706 ?        Rl     0:09 gnome-terminal
 5709 ?        S      0:00 gnome-pty-helper
 5710 pts/0    Ss     0:00 bash
 5932 ?        SNs    0:00 /usr/sbin/cupsd
 6110 ?        SNs    0:00 /sbin/syslogd -u syslog
10647 ?        Ss     0:00 avahi-daemon: running [Blackie.local]
10648 ?        Ss     0:00 avahi-daemon: chroot helper process
19510 ?        S      0:01 gkrellm
19934 ?        Sl     0:33 /usr/lib/firefox/firefox-bin -a firefox
24296 pts/0    R+     0:00 ps axger@Blackie:/etc/init.d$ mozilla-thunderbird

---

### Post by llamakc on 2007-01-30
For starters is the FAT partition mounted and can you as a user r,w to it? What's your fstab look like?

---

### Post by maguro on 2007-01-31
Yes the partition is mounted and I have R/W permission. I just copied and deleted a file to the   mail directory just to prove it to myself.  Just in case you still want the info here is my profiles.ini and fstab:

roger@Blackie:~$ cat .mozilla-thunderbird/profiles.ini
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/media/sda13/MyMailProfile/83vrbrsx.default
Default=1

roger@Blackie:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda10      /media/sda10    ext3    defaults        0       2
/dev/sda11      /media/sda11    ext3    defaults        0       2
/dev/sda12      /media/sda12    ext3    defaults        0       2
/dev/sda13      /media/sda13    vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda6       /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda7       /media/sda7     ext3    defaults        0       2
/dev/sda9       /media/sda9     ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/sda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by maguro on 2007-01-31
I just noticed that Ubuntu is loading that vfat partition as UTF8. Is this a possible reason for the problem?

---

### Post by maguro on 2007-01-31
That was it I got rid of the utf8 from fstab, and the umask=007 while I was at it. Remounted the filesystem, and Thunderbird started right up.

---

