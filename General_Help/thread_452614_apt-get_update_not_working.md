---
title: "apt-get update not working"
date: 2007-05-23
forum: General Help
---

### Post by stickperson on 2007-05-23
Hey, I'm trying to install awn and when I do the sudo apt-get update, it spits out this..

joe@joe-laptop:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

anyone know what to do?  Thanks a lot.

---

### Post by taurus on 2007-05-23
Do you by an chance have synaptic open as well?

---

### Post by stickperson on 2007-05-23
Nope.

---

### Post by taurus on 2007-05-23
Run this command again.

```
sudo aptitude update
```
And if you still get the same error message, then post the output of this command here.

```
ps -A
```

---

### Post by stickperson on 2007-05-23
joe@joe-laptop:~$ sudo aptitude update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?
joe@joe-laptop:~$ ps -A
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
  155 ?        00:00:00 kseriod
  184 ?        00:00:00 pdflush
  185 ?        00:00:00 pdflush
  186 ?        00:00:00 kswapd0
  187 ?        00:00:00 aio/0
  188 ?        00:00:00 aio/1
  821 ?        00:00:00 kirqd
 2024 ?        00:00:00 ksuspend_usbd
 2025 ?        00:00:00 khubd
 2068 ?        00:00:01 ata/0
 2069 ?        00:00:00 ata/1
 2070 ?        00:00:00 ata_aux
 2238 ?        00:00:00 scsi_eh_0
 2239 ?        00:00:00 scsi_eh_1
 2240 ?        00:00:00 scsi_eh_2
 2241 ?        00:00:00 scsi_eh_3
 2300 ?        00:00:02 scsi_eh_4
 2301 ?        00:00:00 scsi_eh_5
 2460 ?        00:00:00 kjournald
 2659 ?        00:00:00 udevd
 3594 ?        00:00:00 kpsmoused
 3768 ?        00:00:00 pccardd
 3769 ?        00:00:00 ipw3945/0
 3770 ?        00:00:00 ipw3945/1
 3771 ?        00:00:00 ipw3945/0
 3772 ?        00:00:00 ipw3945/1
 3821 ?        00:00:00 irda_sir_wq
 3861 ?        00:00:00 ipw3945d-2.6.20
 4233 ?        00:00:00 avahi-autoipd
 4234 ?        00:00:00 avahi-autoipd
 4238 ?        00:00:00 dhclient3
 4462 tty4     00:00:00 getty
 4463 tty5     00:00:00 getty
 4465 tty2     00:00:00 getty
 4467 tty3     00:00:00 getty
 4469 tty1     00:00:00 getty
 4470 tty6     00:00:00 getty
 4756 ?        00:00:00 acpid
 4866 ?        00:00:00 syslogd
 4920 ?        00:00:00 dd
 4922 ?        00:00:00 klogd
 4943 ?        00:00:00 dbus-daemon
 4959 ?        00:00:02 hald
 4960 ?        00:00:00 hald-runner
 4966 ?        00:00:00 hald-addon-acpi
 4967 ?        00:00:00 hald-addon-cpuf
 4974 ?        00:00:00 hald-addon-keyb
 4987 ?        00:00:00 hald-addon-keyb
 4992 ?        00:00:00 hald-addon-keyb
 5005 ?        00:00:02 hald-addon-stor
 5018 ?        00:00:00 dhcdbd
 5033 ?        00:00:00 NetworkManager
 5051 ?        00:00:00 avahi-daemon
 5052 ?        00:00:00 avahi-daemon
 5068 ?        00:00:00 NetworkManagerD
 5081 ?        00:00:00 system-tools-ba
 5082 ?        00:00:00 dbus-daemon
 5140 ?        00:00:00 gdm
 5141 ?        00:00:00 gdm
 5144 tty7     00:00:13 Xorg
 5149 ?        00:00:00 dhclient
 5198 ?        00:00:00 cupsd
 5222 ?        00:00:00 hpiod
 5225 ?        00:00:00 python
 5333 ?        00:00:00 kondemand/0
 5334 ?        00:00:00 kondemand/1
 5372 ?        00:00:00 hcid
 5392 ?        00:00:00 krfcommd
 5414 ?        00:00:00 anacron
 5428 ?        00:00:00 atd
 5442 ?        00:00:00 cron
 5600 ?        00:00:00 gnome-session
 5639 ?        00:00:00 ssh-agent
 5642 ?        00:00:00 dbus-launch
 5643 ?        00:00:00 dbus-daemon
 5644 ?        00:02:35 Xgl
 5649 ?        00:00:00 gconfd-2
 5652 ?        00:00:00 gnome-keyring-d
 5654 ?        00:00:00 gnome-settings-
 5661 ?        00:00:00 sh
 5662 ?        00:00:00 esd
 5666 ?        00:00:05 metacity
 5671 ?        00:00:11 gnome-panel
 5675 ?        00:00:15 nautilus
 5678 ?        00:00:00 bonobo-activati
 5679 ?        00:00:00 gnome-volume-ma
 5685 ?        00:00:00 gnome-vfs-daemo
 5688 ?        00:00:00 update-notifier
 5693 ?        00:00:00 evolution-alarm
 5695 ?        00:00:00 nm-applet
 5696 ?        00:00:00 gnome-cups-icon
 5697 ?        00:00:00 gnome-power-man
 5742 ?        00:00:00 mapping-daemon
 5764 ?        00:00:00 mixer_applet2
 5775 ?        00:00:04 gnome-screensav
 5881 ?        00:00:00 sh
 5882 ?        00:00:00 run-parts
 5893 ?        00:00:00 apt
 5905 ?        00:00:00 apt-get
 5907 ?        00:00:00 http
 5908 ?        00:00:00 http
 5909 ?        00:00:00 http
 5910 ?        00:00:00 http
 5912 ?        00:00:00 gpgv
 5919 ?        00:00:00 bzip2
 5982 ?        00:00:00 notification-da
 6045 ?        00:01:19 firefox-bin
 6583 ?        00:00:00 evolution-excha
 9692 ?        00:00:00 gnome-terminal
 9695 ?        00:00:00 gnome-pty-helpe
 9696 pts/0    00:00:00 bash
 9716 pts/0    00:00:00 ps

---

### Post by taurus on 2007-05-23
> 5893 ? 00:00:00 apt
5905 ? 00:00:00 apt-get

Run

```
sudo kill -9 5893 5905
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by subru77 on 2007-07-11
Thanks 

This worked for me.
Can you explain the problem why this happened in the first place ?
:popcorn:

---

### Post by rillip on 2007-07-11
You can't run apt and apt-get at the same time, or at the same time as dpkg, Synaptic, Adept, or any other number of package managers.  To prevent themselves from getting messed up, they each create a lock file.  While the lock file for the package system (dpkg is the root) is in place, nobody can access it until the lock is released.

---

### Post by levele304 on 2007-08-25
hey I am getting the same error message.. 

my output is as follows:

ps -A
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
  173 ?        00:00:00 kseriod
  202 ?        00:00:00 pdflush
  203 ?        00:00:00 pdflush
  204 ?        00:00:00 kswapd0
  205 ?        00:00:00 aio/0
  206 ?        00:00:00 aio/1
  838 ?        00:00:00 kirqd
 2037 ?        00:00:00 ksuspend_usbd
 2038 ?        00:00:00 khubd
 2073 ?        00:00:00 khpsbpkt
 2111 ?        00:00:00 ata/0
 2112 ?        00:00:00 ata/1
 2113 ?        00:00:00 ata_aux
 2229 ?        00:00:00 knodemgrd_0
 2230 ?        00:00:00 scsi_eh_0
 2231 ?        00:00:00 scsi_eh_1
 2449 ?        00:00:00 kjournald
 2648 ?        00:00:00 udevd
 3565 ?        00:00:00 kpsmoused
 3575 ?        00:00:00 kmmcd
 3718 ?        00:00:00 hda_codec
 4241 ?        00:00:00 wrap_wq
 4242 ?        00:00:00 ntos_wq
 4243 ?        00:00:00 ndis_wq
 4436 tty4     00:00:00 getty
 4437 tty5     00:00:00 getty
 4439 tty2     00:00:00 getty
 4441 tty3     00:00:00 getty
 4443 tty1     00:00:00 getty
 4444 tty6     00:00:00 getty
 4728 ?        00:00:00 acpid
 4837 ?        00:00:00 syslogd
 4891 ?        00:00:00 dd
 4893 ?        00:00:00 klogd
 4914 ?        00:00:00 dbus-daemon
 4930 ?        00:00:01 hald
 4931 ?        00:00:00 hald-runner
 4937 ?        00:00:00 hald-addon-keyb
 4939 ?        00:00:00 hald-addon-cpuf
 4940 ?        00:00:00 hald-addon-acpi
 4941 ?        00:00:00 hald-addon-keyb
 4942 ?        00:00:00 hald-addon-keyb
 4943 ?        00:00:00 hald-addon-keyb
 4963 ?        00:00:00 hald-addon-stor
 4976 ?        00:00:00 dhcdbd
 4991 ?        00:00:00 NetworkManager
 5009 ?        00:00:00 avahi-daemon
 5010 ?        00:00:00 avahi-daemon
 5025 ?        00:00:00 NetworkManagerD
 5039 ?        00:00:00 system-tools-ba
 5040 ?        00:00:00 dbus-daemon
 5091 ?        00:00:00 gdm
 5092 ?        00:00:00 gdm
 5095 tty7     00:00:50 Xorg
 5138 ?        00:00:00 cupsd
 5164 ?        00:00:00 hpiod
 5185 ?        00:00:00 python
 5269 ?        00:00:00 kondemand/0
 5270 ?        00:00:00 kondemand/1
 5307 ?        00:00:00 hcid
 5327 ?        00:00:00 krfcommd
 5363 ?        00:00:00 atd
 5377 ?        00:00:00 cron
 5636 ?        00:00:00 bonobo-activati
 5945 ?        00:00:00 evolution-data-
 6136 ?        00:00:00 avahi-autoipd
 6137 ?        00:00:00 avahi-autoipd
 6143 ?        00:00:00 wpa_supplicant
 6156 ?        00:00:00 dhclient
 6219 ?        00:00:00 dhclient3
 6691 ?        00:00:00 apt-get
 6696 ?        00:00:00 http
 6697 ?        00:00:00 http
 6698 ?        00:00:00 http
 6699 ?        00:00:00 http
 6700 ?        00:00:00 http
 6701 ?        00:00:00 http
 6702 ?        00:00:00 http
 6703 ?        00:00:00 http
 6705 ?        00:00:00 gpgv
 6717 ?        00:00:00 bzip2
 7860 ?        00:00:00 gnome-session
 7905 ?        00:00:00 ssh-agent
 7908 ?        00:00:00 dbus-daemon
 7909 ?        00:00:00 dbus-launch
 7910 ?        00:00:55 Xgl
 7912 ?        00:00:00 scim-launcher
 7916 ?        00:00:00 scim-helper-man
 7917 ?        00:00:00 scim-panel-gtk
 7919 ?        00:00:00 scim-launcher
 7923 ?        00:00:00 gconfd-2
 7926 ?        00:00:00 gnome-keyring-d
 7928 ?        00:00:00 gnome-settings-
 7935 ?        00:00:00 sh
 7936 ?        00:00:00 esd
 7943 ?        00:00:05 gnome-panel
 7950 ?        00:00:01 nautilus
 7954 ?        00:00:00 gnome-volume-ma
 7957 ?        00:00:05 beagled
 7960 ?        00:00:00 beagle-search
 7963 ?        00:00:00 update-notifier
 7965 ?        00:00:00 gnome-vfs-daemo
 7969 ?        00:00:00 evolution-alarm
 7976 ?        00:00:00 nm-applet
 7977 ?        00:00:00 gnome-cups-icon
 7982 ?        00:00:00 trashapplet
 7985 ?        00:00:00 evolution-excha
 8023 ?        00:00:00 gnome-power-man
 8045 ?        00:00:00 mixer_applet2
 8055 ?        00:00:00 mapping-daemon
 8220 ?        00:00:00 scim-panel-gtk
 8273 ?        00:00:02 gnome-screensav
 8317 ?        00:00:32 beagled-helper
 8366 ?        00:00:04 metacity
 8375 ?        00:00:25 firefox-bin
 8389 ?        00:00:04 gaim
 8462 ?        00:00:00 gnome-terminal
 8465 ?        00:00:00 gnome-pty-helpe
 8466 pts/1    00:00:00 bash
 9035 ?        00:00:00 notification-da
 9079 pts/1    00:00:00 ps

Help!

---

### Post by rillip on 2007-08-28
I don't see any two of the usual culprits.  Are you 110% sure you're not running two?

If you're getting the same exact error, you can always just blow away the lock file if you're REALLY sure you don't have two running

```
 sudo rm  /var/lib/apt/lists/lock 
```

Then try again.

---

