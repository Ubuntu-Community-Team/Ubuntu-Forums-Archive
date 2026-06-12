---
title: "[SOLVED] cannot change packages in adept"
date: 2007-08-11
forum: General Help
---

### Post by rbprogrammer on 2007-08-11
i had this problem before. when i open up adept, i get the error message:
[INDENT]check screen shot[/INDENT]

here is my output of [FONT="Courier New"]ps -A[/FONT] if it helps:
```

$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
   30 ?        00:00:00 kblockd/0
   31 ?        00:00:00 kacpid
   32 ?        00:00:00 kacpi_notify
  161 ?        00:00:00 kseriod
  186 ?        00:00:00 pdflush
  187 ?        00:00:00 pdflush
  188 ?        00:00:00 kswapd0
  189 ?        00:00:00 aio/0
 2000 ?        00:00:00 ksuspend_usbd
 2001 ?        00:00:00 khubd
 2032 ?        00:00:00 khpsbpkt
 2050 ?        00:00:00 ata/0
 2051 ?        00:00:00 ata_aux
 2167 ?        00:00:00 knodemgrd_0
 2174 ?        00:00:00 scsi_eh_0
 2175 ?        00:00:00 scsi_eh_1
 2345 ?        00:00:00 kjournald
 2544 ?        00:00:00 udevd
 3411 ?        00:00:00 kmmcd
 3471 ?        00:00:00 kpsmoused
 3523 ?        00:00:00 ipw3945/0
 3524 ?        00:00:00 ipw3945/0
 3587 ?        00:00:00 scsi_eh_2
 3588 ?        00:00:00 usb-storage
 3681 ?        00:00:00 hda_codec
 3753 ?        00:00:00 ipw3945d-2.6.20
 4021 ?        00:00:00 kjournald
 4023 ?        00:00:00 kjournald
 4903 tty4     00:00:00 getty
 4904 tty5     00:00:00 getty
 4908 tty2     00:00:00 getty
 4909 tty3     00:00:00 getty
 4910 tty1     00:00:00 getty
 4911 tty6     00:00:00 getty
 5177 ?        00:00:00 acpid
 5283 ?        00:00:00 syslogd
 5336 ?        00:00:00 dd
 5338 ?        00:00:00 klogd
 5384 ?        00:00:01 dbus-daemon
 5400 ?        00:00:03 hald
 5401 ?        00:00:00 hald-runner
 5407 ?        00:00:00 hald-addon-acpi
 5408 ?        00:00:00 hald-addon-cpuf
 5415 ?        00:00:00 hald-addon-keyb
 5418 ?        00:00:00 hald-addon-keyb
 5421 ?        00:00:00 hald-addon-keyb
 5434 ?        00:00:00 hald-addon-keyb
 5437 ?        00:00:00 hald-addon-keyb
 5453 ?        00:00:00 hald-addon-stor
 5467 ?        00:00:00 dhcdbd
 5482 ?        00:00:00 NetworkManager
 5500 ?        00:00:00 avahi-daemon
 5501 ?        00:00:00 avahi-daemon
 5516 ?        00:00:00 NetworkManagerD
 5562 ?        00:00:00 cupsd
 5598 ?        00:00:00 hpiod
 5601 ?        00:00:00 python
 5686 ?        00:00:00 kondemand/0
 5726 ?        00:00:00 hcid
 5743 ?        00:00:00 krfcommd
 5779 ?        00:00:00 atd
 5793 ?        00:00:00 cron
 5854 ?        00:00:00 kdm
 5873 tty7     00:00:23 Xorg
 5888 ?        00:00:00 kdm
 5922 ?        00:00:00 x-session-manag
 5961 ?        00:00:00 ssh-agent
 5964 ?        00:00:00 dbus-launch
 5965 ?        00:00:00 dbus-daemon
 6000 ?        00:00:00 start_kdeinit
 6001 ?        00:00:00 kdeinit
 6004 ?        00:00:00 dcopserver
 6007 ?        00:00:00 klauncher
 6009 ?        00:00:00 kded
 6014 ?        00:00:00 kwrapper
 6016 ?        00:00:00 ksmserver
 6017 ?        00:00:04 kwin
 6024 ?        00:00:00 avahi-autoipd
 6025 ?        00:00:00 avahi-autoipd
 6027 ?        00:00:09 kdesktop
 6029 ?        00:00:02 kicker
 6045 ?        00:00:00 kio_uiserver
 6060 ?        00:00:01 artsd
 6063 ?        00:00:00 kaccess
 6070 ?        00:00:00 kmix
 6071 ?        00:00:00 katapult
 6073 ?        00:00:30 ktorrent
 6078 ?        00:00:00 aspell
 6082 ?        00:00:02 gaim
 6083 ?        00:00:00 dhclient3
 6103 ?        00:00:01 konqueror
 6105 ?        00:00:03 amarokapp
 6127 ?        00:00:01 yakuake
 6128 ?        00:00:01 konqueror
 6129 ?        00:00:00 firefox
 6135 ?        00:00:01 guidance-power-
 6137 ?        00:00:00 knotify
 6138 ?        00:00:00 kio_file
 6147 ?        00:00:00 run-mozilla.sh
 6164 ?        00:00:28 firefox-bin
 6174 ?        00:00:00 kjournald
 6176 ?        00:00:00 kbluetoothd
 6187 ?        00:00:01 knetworkmanager
 6189 ?        00:00:00 passkey-agent
 6192 ?        00:00:00 klipper
 6213 ?        00:00:00 wpa_supplicant
 6223 ?        00:00:00 dhclient
 6273 pts/1    00:00:00 bash
 6310 ?        00:00:00 gconfd-2
 6320 ?        00:00:00 kio_http
 6324 ?        00:00:00 netstat <defunct>
 6343 ?        00:00:00 kio_file
 6344 ?        00:00:00 ruby
 6425 ?        00:00:00 kdesud
 6466 ?        00:00:00 artsd
 6527 ?        00:00:00 sudo
 6540 ?        00:00:00 kdeinit
 6543 ?        00:00:00 dcopserver
 6546 ?        00:00:00 klauncher
 6548 ?        00:00:00 kded
 6558 ?        00:00:00 knotify
 6571 pts/1    00:00:00 ps

```
last time i had to execute:
```
sudp kill -9 #ofprogram
```
but i dont knwo what to kill this time..

---

### Post by rbprogrammer on 2007-08-12
somehow i figured it out, not sure if this is exactly what i did, so i'll try and post what i went through in case other people get this problem.

i ran:
```
sudo aptitude update
```
it told me to run:
```
sudo dpkg --configure -a
```
that somehow lead me to:
```
sudo aptitude remove linux-image-2.6.20-16-generic
```
so i got an error message saying i shouldn't uninstall it b/c that was the only linux image i was running, so i chose "dont uninstall" but somehow it must of reinstalled itself because when i ran:
```
sudo aptitude update
```
and all was fine.

---

