---
title: "puter keeps freezing"
date: 2008-02-11
forum: General Help
---

### Post by wtfdoyouwantdude on 2008-02-11
im trying to find an answer as to why my puter keeps locking up. it usually happens when im online downloading. but has happend before when doing something simple as a spreadsheet. what is causing this and is there any thing i can do to fix it?

---

### Post by chadeldridge on 2008-02-11
Can you post some information for us?  

Make / Model / Speed / Memory 

The tail from /var/log/messages  and /var/log/syslog


Thanks,

---

### Post by harold4 on 2008-02-11
Assuming it's the system in the sig, I'd take a look at the parking bug.

[My laptop was locking up just before /dev/sda died after 6 weeks!]("http://ubuntuforums.org/showthread.php?t=591503")

Sticking with Debian until this gets fixed.

---

### Post by wtfdoyouwantdude on 2008-02-11
Feb 11 12:25:19 red-queen syslogd 1.4.1#21ubuntu3: restart.
Feb 11 12:25:19 red-queen anacron[6648]: Job `cron.daily' terminated
Feb 11 12:25:19 red-queen anacron[6648]: Normal exit (1 job run)
Feb 11 12:25:19 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:25:19 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:25:19 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:25:42 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:25:42 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:25:42 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:25:42 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:26:12 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:26:12 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:26:12 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:26:42 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:26:42 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:26:42 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:27:12 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:27:12 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:27:12 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:27:42 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:27:42 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:27:42 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:28:12 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:28:12 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:28:12 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:28:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:28:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:28:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:29:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:29:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:29:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:29:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:29:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:29:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:30:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:30:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:30:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:30:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:30:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:30:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:31:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:31:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:31:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:31:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:31:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:31:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:32:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:32:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:32:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:32:32 red-queen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Feb 11 12:32:38 red-queen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Feb 11 12:32:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:32:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:32:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:32:49 red-queen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Feb 11 12:32:57 red-queen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Feb 11 12:33:03 red-queen dhclient: No DHCPOFFERS received.
Feb 11 12:33:03 red-queen dhclient: No working leases in persistent database - sleeping.
Feb 11 12:33:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:33:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:33:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:33:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:33:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:33:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:34:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:34:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:34:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:34:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:34:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:34:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:35:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:35:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:35:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:35:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:35:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:35:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:36:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:36:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:36:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:36:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:36:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:36:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:37:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:37:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:37:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:37:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:37:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:37:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:38:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:38:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:38:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:38:26 red-queen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Feb 11 12:38:30 red-queen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Feb 11 12:38:41 red-queen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Feb 11 12:38:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:38:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:38:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:38:53 red-queen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Feb 11 12:38:57 red-queen dhclient: No DHCPOFFERS received.
Feb 11 12:38:57 red-queen dhclient: No working leases in persistent database - sleeping.
Feb 11 12:39:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:39:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:39:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:39:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:39:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:39:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:40:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:40:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:40:13 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:40:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 12:40:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 12:40:43 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 12:40:58 red-queen hald: unmounted /dev/sdb1 from '/media/FOX COMPANY' on behalf of uid 1000
Feb 11 12:40:59 red-queen init: tty4 main process (4727) killed by TERM signal
Feb 11 12:40:59 red-queen init: tty5 main process (4728) killed by TERM signal
Feb 11 12:40:59 red-queen init: tty2 main process (4730) killed by TERM signal
Feb 11 12:40:59 red-queen init: tty3 main process (4732) killed by TERM signal
Feb 11 12:40:59 red-queen init: tty1 main process (4734) killed by TERM signal
Feb 11 12:40:59 red-queen init: tty6 main process (4735) killed by TERM signal
Feb 11 12:40:59 red-queen avahi-daemon[5588]: Got SIGTERM, quitting.
Feb 11 12:40:59 red-queen avahi-daemon[5588]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.7.85.
Feb 11 12:41:01 red-queen exiting on signal 15
Feb 11 18:11:56 red-queen syslogd 1.4.1#21ubuntu3: restart.
Feb 11 18:11:57 red-queen kernel: Inspecting /boot/System.map-2.6.22-14-generic
Feb 11 18:11:57 red-queen kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Feb 11 18:11:57 red-queen kernel: Symbols match kernel version 2.6.22.
Feb 11 18:11:57 red-queen kernel: No module symbols loaded - kernel modules not enabled. 
Feb 11 18:11:57 red-queen kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Fri Feb 1 04:59:50 UTC 2008 (Ubuntu 2.6.22-14.51-generic)
Feb 11 18:11:57 red-queen kernel: [    0.000000] BIOS-provided physical RAM map:
Feb 11 18:11:57 red-queen kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Feb 11 18:11:57 red-queen kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Feb 11 18:11:57 red-queen kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cf693400 (usable)
Feb 11 18:11:57 red-queen kernel: [    0.000000]  BIOS-e820: 00000000cf693400 - 00000000d0000000 (reserved)
Feb 11 18:11:57 red-queen kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
Feb 11 18:11:57 red-queen kernel: [    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
Feb 11 18:11:57 red-queen kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Feb 11 18:11:57 red-queen kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
Feb 11 18:11:57 red-queen kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Feb 11 18:11:57 red-queen kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Feb 11 18:11:57 red-queen kernel: [    0.000000] 2422MB HIGHMEM available.
Feb 11 18:11:57 red-queen kernel: [    0.000000] 896MB LOWMEM available.
Feb 11 18:11:57 red-queen kernel: [    0.000000] Entering add_active_range(0, 0, 849555) 0 entries of 256 used
Feb 11 18:11:57 red-queen kernel: [    0.000000] Zone PFN ranges:
Feb 11 18:11:57 red-queen kernel: [    0.000000]   DMA             0 ->     4096
Feb 11 18:11:57 red-queen kernel: [    0.000000]   Normal       4096 ->   229376
Feb 11 18:11:57 red-queen kernel: [    0.000000]   HighMem    229376 ->   849555
Feb 11 18:11:57 red-queen kernel: [    0.000000] early_node_map[1] active PFN ranges
Feb 11 18:11:57 red-queen kernel: [    0.000000]     0:        0 ->   849555
Feb 11 18:11:57 red-queen kernel: [    0.000000] On node 0 totalpages: 849555
Feb 11 18:11:57 red-queen kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Feb 11 18:11:57 red-queen kernel: [    0.000000]   DMA zone: 0 pages reserved
Feb 11 18:11:57 red-queen kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Feb 11 18:11:57 red-queen kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Feb 11 18:11:57 red-queen kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Feb 11 18:11:57 red-queen kernel: [    0.000000]   HighMem zone: 4845 pages used for memmap
Feb 11 18:11:57 red-queen kernel: [    0.000000]   HighMem zone: 615334 pages, LIFO batch:31
Feb 11 18:11:57 red-queen kernel: [    0.000000] DMI 2.4 present.
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FC1D0 checksum 0
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: RSDP 000FC1D0, 0014 (r0 DELL  )
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: RSDT CF6939CD, 0040 (r1 DELL    M07     27D7070A ASL        61)
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: FACP CF694800, 0074 (r1 DELL    M07     27D7070A ASL        61)
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: DSDT CF695400, 4766 (r1 INT430 SYSFexxx     1001 INTL 20050624)
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: FACS CF6A3C00, 0040
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: HPET CF694F00, 0038 (r1 DELL    M07            1 ASL        61)
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: APIC CF695000, 0068 (r1 DELL    M07     27D7070A ASL        47)
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: MCFG CF694FC0, 003E (r16 DELL    M07     27D7070A ASL        61)
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: SLIC CF69509C, 0176 (r1 DELL    M07     27D7070A ASL        61)
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: BOOT CF694BC0, 0028 (r1 DELL    M07     27D7070A ASL        61)
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: SSDT CF693A0D, 04DC (r1  PmRef    CpuPm     3000 INTL 20050624)
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb 11 18:11:57 red-queen kernel: [    0.000000] Processor #0 6:15 APIC version 20
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Feb 11 18:11:57 red-queen kernel: [    0.000000] Processor #1 6:15 APIC version 20
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Feb 11 18:11:57 red-queen kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: IRQ0 used by override.
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: IRQ2 used by override.
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: IRQ9 used by override.
Feb 11 18:11:57 red-queen kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb 11 18:11:57 red-queen kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Feb 11 18:11:57 red-queen kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb 11 18:11:57 red-queen kernel: [    0.000000] Allocating PCI resources starting at d2000000 (gap: d0000000:20000000)
Feb 11 18:11:57 red-queen kernel: [    0.000000] Built 1 zonelists.  Total pages: 842918
Feb 11 18:11:57 red-queen kernel: [    0.000000] Kernel command line: root=UUID=1bd6342d-430a-40f6-8687-a523abbc165c ro quiet splash
Feb 11 18:11:57 red-queen kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Feb 11 18:11:57 red-queen kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Feb 11 18:11:57 red-queen kernel: [    0.000000] Enabling fast FPU save and restore... done.
Feb 11 18:11:57 red-queen kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Feb 11 18:11:57 red-queen kernel: [    0.000000] Initializing CPU#0
Feb 11 18:11:57 red-queen kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Feb 11 18:11:57 red-queen kernel: [    0.000000] Detected 1997.445 MHz processor.
Feb 11 18:11:57 red-queen kernel: [   45.439755] Console: colour VGA+ 80x25
Feb 11 18:11:57 red-queen kernel: [   45.440034] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb 11 18:11:57 red-queen kernel: [   45.440309] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb 11 18:11:57 red-queen kernel: [   45.574284] Memory: 3358220k/3398220k available (2015k kernel code, 38764k reserved, 916k data, 364k init, 2480716k highmem)
Feb 11 18:11:57 red-queen kernel: [   45.574292] virtual kernel memory layout:
Feb 11 18:11:57 red-queen kernel: [   45.574293]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Feb 11 18:11:57 red-queen kernel: [   45.574294]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Feb 11 18:11:57 red-queen kernel: [   45.574295]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Feb 11 18:11:57 red-queen kernel: [   45.574296]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Feb 11 18:11:57 red-queen kernel: [   45.574297]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Feb 11 18:11:57 red-queen kernel: [   45.574298]       .data : 0xc02f7e66 - 0xc03dce84   ( 916 kB)
Feb 11 18:11:57 red-queen kernel: [   45.574299]       .text : 0xc0100000 - 0xc02f7e66   (2015 kB)
Feb 11 18:11:57 red-queen kernel: [   45.574302] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb 11 18:11:57 red-queen kernel: [   45.574339] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Feb 11 18:11:57 red-queen kernel: [   45.574468] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Feb 11 18:11:57 red-queen kernel: [   45.574472] hpet0: 3 64-bit timers, 14318180 Hz
Feb 11 18:11:57 red-queen kernel: [   45.655383] Calibrating delay using timer specific routine.. 3998.92 BogoMIPS (lpj=7997841)
Feb 11 18:11:57 red-queen kernel: [   45.655405] Security Framework v1.0.0 initialized
Feb 11 18:11:57 red-queen kernel: [   45.655412] SELinux:  Disabled at boot.
Feb 11 18:11:57 red-queen kernel: [   45.655423] Mount-cache hash table entries: 512
Feb 11 18:11:57 red-queen kernel: [   45.655550] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
Feb 11 18:11:57 red-queen kernel: [   45.655557] monitor/mwait feature present.
Feb 11 18:11:57 red-queen kernel: [   45.655559] using mwait in idle threads.
Feb 11 18:11:57 red-queen kernel: [   45.655563] CPU: L1 I cache: 32K, L1 D cache: 32K
Feb 11 18:11:57 red-queen kernel: [   45.655565] CPU: L2 cache: 4096K
Feb 11 18:11:57 red-queen kernel: [   45.655567] CPU: Physical Processor ID: 0
Feb 11 18:11:57 red-queen kernel: [   45.655569] CPU: Processor Core ID: 0
Feb 11 18:11:57 red-queen kernel: [   45.655570] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
Feb 11 18:11:57 red-queen kernel: [   45.655579] Compat vDSO mapped to ffffe000.
Feb 11 18:11:57 red-queen kernel: [   45.655591] Checking 'hlt' instruction... OK.
Feb 11 18:11:57 red-queen kernel: [   45.671471] SMP alternatives: switching to UP code
Feb 11 18:11:57 red-queen kernel: [   45.671883] Early unpacking initramfs... done
Feb 11 18:11:57 red-queen kernel: [   45.952444] ACPI: Core revision 20070126
Feb 11 18:11:57 red-queen kernel: [   45.952483] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Feb 11 18:11:57 red-queen kernel: [   45.954682] CPU0: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
Feb 11 18:11:57 red-queen kernel: [   45.954696] SMP alternatives: switching to SMP code
Feb 11 18:11:57 red-queen kernel: [   45.954768] Booting processor 1/1 eip 3000
Feb 11 18:11:57 red-queen kernel: [   47.999052] Initializing CPU#1
Feb 11 18:11:57 red-queen kernel: [   48.078154] Calibrating delay using timer specific routine.. 3994.67 BogoMIPS (lpj=7989352)
Feb 11 18:11:57 red-queen kernel: [   48.078160] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
Feb 11 18:11:57 red-queen kernel: [   48.078164] monitor/mwait feature present.
Feb 11 18:11:57 red-queen kernel: [   48.078166] CPU: L1 I cache: 32K, L1 D cache: 32K
Feb 11 18:11:57 red-queen kernel: [   48.078168] CPU: L2 cache: 4096K
Feb 11 18:11:57 red-queen kernel: [   48.078170] CPU: Physical Processor ID: 0
Feb 11 18:11:57 red-queen kernel: [   48.078171] CPU: Processor Core ID: 1
Feb 11 18:11:57 red-queen kernel: [   48.078172] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
Feb 11 18:11:57 red-queen kernel: [   46.047534] CPU1: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
Feb 11 18:11:57 red-queen kernel: [   46.047555] Total of 2 processors activated (7993.59 BogoMIPS).
Feb 11 18:11:57 red-queen kernel: [   46.047748] ENABLING IO-APIC IRQs
Feb 11 18:11:57 red-queen kernel: [   46.047939] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Feb 11 18:11:57 red-queen kernel: [   46.194735] checking TSC synchronization [CPU#0 -> CPU#1]:
Feb 11 18:11:57 red-queen kernel: [   46.214717] Measured 4062605580 cycles TSC warp between CPUs, turning off TSC clock.
Feb 11 18:11:57 red-queen kernel: [    0.512000] Marking TSC unstable due to: check_tsc_sync_source failed.
Feb 11 18:11:57 red-queen kernel: [    0.516000] Brought up 2 CPUs
Feb 11 18:11:57 red-queen kernel: [    0.696000] migration_cost=8000
Feb 11 18:11:57 red-queen kernel: [    0.696000] Booting paravirtualized kernel on bare hardware
Feb 11 18:11:57 red-queen kernel: [    0.696000] Time:  0:11:40  Date: 01/12/108
Feb 11 18:11:57 red-queen kernel: [    0.696000] NET: Registered protocol family 16
Feb 11 18:11:57 red-queen kernel: [    0.696000] EISA bus registered
Feb 11 18:11:57 red-queen kernel: [    0.696000] ACPI: bus type pci registered
Feb 11 18:11:57 red-queen kernel: [    0.724000] PCI: PCI BIOS revision 2.10 entry at 0xfb336, last bus=14
Feb 11 18:11:57 red-queen kernel: [    0.724000] PCI: Using configuration type 1
Feb 11 18:11:57 red-queen kernel: [    0.724000] Setting up standard PCI resources
Feb 11 18:11:57 red-queen kernel: [    0.728000] ACPI: EC: Look up EC in DSDT
Feb 11 18:11:57 red-queen kernel: [    0.732000] ACPI: Interpreter enabled
Feb 11 18:11:57 red-queen kernel: [    0.732000] ACPI: (supports S0 S3 S4 S5)
Feb 11 18:11:57 red-queen kernel: [    0.732000] ACPI: Using IOAPIC for interrupt routing
Feb 11 18:11:57 red-queen kernel: [    0.748000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Feb 11 18:11:57 red-queen kernel: [    0.748000] PCI: Probing PCI hardware (bus 00)
Feb 11 18:11:57 red-queen kernel: [    0.748000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Feb 11 18:11:57 red-queen kernel: [    0.748000] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Feb 11 18:11:57 red-queen kernel: [    0.748000] PCI: Transparent bridge - 0000:00:1e.0
Feb 11 18:11:57 red-queen kernel: [    0.748000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Feb 11 18:11:57 red-queen kernel: [    0.748000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Feb 11 18:11:57 red-queen kernel: [    0.748000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Feb 11 18:11:57 red-queen kernel: [    0.748000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Feb 11 18:11:57 red-queen kernel: [    0.748000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Feb 11 18:11:57 red-queen kernel: [    0.756000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
Feb 11 18:11:57 red-queen kernel: [    0.756000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
Feb 11 18:11:57 red-queen kernel: [    0.756000] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
Feb 11 18:11:57 red-queen kernel: [    0.756000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
Feb 11 18:11:57 red-queen kernel: [    0.756000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Feb 11 18:11:57 red-queen kernel: [    0.756000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Feb 11 18:11:57 red-queen kernel: [    0.756000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Feb 11 18:11:57 red-queen kernel: [    0.756000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Feb 11 18:11:57 red-queen kernel: [    0.756000] Linux Plug and Play Support v0.97 (c) Adam Belay
Feb 11 18:11:57 red-queen kernel: [    0.756000] pnp: PnP ACPI init
Feb 11 18:11:57 red-queen kernel: [    0.756000] ACPI: bus type pnp registered
Feb 11 18:11:57 red-queen kernel: [    0.784000] pnp: PnP ACPI: found 12 devices
Feb 11 18:11:57 red-queen kernel: [    0.784000] ACPI: ACPI bus type pnp unregistered
Feb 11 18:11:57 red-queen kernel: [    0.784000] PnPBIOS: Disabled by ACPI PNP
Feb 11 18:11:57 red-queen kernel: [    0.784000] PCI: Using ACPI for IRQ routing
Feb 11 18:11:57 red-queen kernel: [    0.784000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Feb 11 18:11:57 red-queen kernel: [    0.832000] NET: Registered protocol family 8
Feb 11 18:11:57 red-queen kernel: [    0.832000] NET: Registered protocol family 20
Feb 11 18:11:57 red-queen kernel: [    0.832000] pnp: 00:00: iomem range 0x0-0x9fbff could not be reserved
Feb 11 18:11:57 red-queen kernel: [    0.832000] pnp: 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
Feb 11 18:11:57 red-queen kernel: [    0.832000] pnp: 00:00: iomem range 0xc0000-0xcffff could not be reserved
Feb 11 18:11:57 red-queen kernel: [    0.832000] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved
Feb 11 18:11:57 red-queen kernel: [    0.832000] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
Feb 11 18:11:57 red-queen kernel: [    0.832000] pnp: 00:02: ioport range 0x1000-0x1005 has been reserved
Feb 11 18:11:57 red-queen kernel: [    0.832000] pnp: 00:02: ioport range 0x1008-0x100f has been reserved
Feb 11 18:11:57 red-queen kernel: [    0.832000] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
Feb 11 18:11:57 red-queen kernel: [    0.832000] pnp: 00:03: ioport range 0x1006-0x1007 has been reserved
Feb 11 18:11:57 red-queen kernel: [    0.832000] pnp: 00:03: ioport range 0x100a-0x1059 could not be reserved
Feb 11 18:11:57 red-queen kernel: [    0.832000] pnp: 00:03: ioport range 0x1060-0x107f has been reserved
Feb 11 18:11:57 red-queen kernel: [    0.832000] pnp: 00:03: ioport range 0x1080-0x10bf has been reserved
Feb 11 18:11:57 red-queen kernel: [    0.832000] pnp: 00:03: ioport range 0x10c0-0x10df has been reserved
Feb 11 18:11:57 red-queen kernel: [    0.832000] pnp: 00:08: ioport range 0xc80-0xcff could not be reserved
Feb 11 18:11:57 red-queen kernel: [    0.832000] pnp: 00:08: ioport range 0x910-0x91f has been reserved
Feb 11 18:11:57 red-queen kernel: [    0.832000] pnp: 00:08: ioport range 0x920-0x92f has been reserved
Feb 11 18:11:57 red-queen kernel: [    0.832000] pnp: 00:08: ioport range 0xcb0-0xcbf has been reserved
Feb 11 18:11:57 red-queen kernel: [    0.832000] pnp: 00:08: ioport range 0x930-0x97f has been reserved
Feb 11 18:11:57 red-queen kernel: [    0.832000] pnp: 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
Feb 11 18:11:57 red-queen kernel: [    0.836000] Time: hpet clocksource has been installed.
Feb 11 18:11:57 red-queen kernel: [    0.836000] Switched to high resolution mode on CPU 0
Feb 11 18:11:57 red-queen kernel: [    0.836000] Switched to high resolution mode on CPU 1
Feb 11 18:11:57 red-queen kernel: [    0.860000] PCI: Bridge: 0000:00:1c.0
Feb 11 18:11:57 red-queen kernel: [    0.860000]   IO window: disabled.
Feb 11 18:11:57 red-queen kernel: [    0.860000]   MEM window: disabled.
Feb 11 18:11:57 red-queen kernel: [    0.860000]   PREFETCH window: disabled.
Feb 11 18:11:57 red-queen kernel: [    0.860000] PCI: Bridge: 0000:00:1c.1
Feb 11 18:11:57 red-queen kernel: [    0.860000]   IO window: disabled.
Feb 11 18:11:57 red-queen kernel: [    0.860000]   MEM window: efd00000-efdfffff
Feb 11 18:11:57 red-queen kernel: [    0.860000]   PREFETCH window: e0000000-e00fffff
Feb 11 18:11:57 red-queen kernel: [    0.860000] PCI: Bridge: 0000:00:1c.3
Feb 11 18:11:57 red-queen kernel: [    0.860000]   IO window: d000-dfff
Feb 11 18:11:57 red-queen kernel: [    0.860000]   MEM window: efa00000-efcfffff
Feb 11 18:11:57 red-queen kernel: [    0.860000]   PREFETCH window: e0100000-e03fffff
Feb 11 18:11:57 red-queen kernel: [    0.860000] PCI: Bridge: 0000:00:1e.0
Feb 11 18:11:57 red-queen kernel: [    0.860000]   IO window: disabled.
Feb 11 18:11:57 red-queen kernel: [    0.860000]   MEM window: ef900000-ef9fffff
Feb 11 18:11:57 red-queen kernel: [    0.860000]   PREFETCH window: disabled.
Feb 11 18:11:57 red-queen kernel: [    0.860000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Feb 11 18:11:57 red-queen kernel: [    0.860000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Feb 11 18:11:57 red-queen kernel: [    0.860000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
Feb 11 18:11:57 red-queen kernel: [    0.860000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Feb 11 18:11:57 red-queen kernel: [    0.860000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
Feb 11 18:11:57 red-queen kernel: [    0.860000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Feb 11 18:11:57 red-queen kernel: [    0.860000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Feb 11 18:11:57 red-queen kernel: [    0.860000] NET: Registered protocol family 2
Feb 11 18:11:57 red-queen kernel: [    0.904000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Feb 11 18:11:57 red-queen kernel: [    0.904000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Feb 11 18:11:57 red-queen kernel: [    0.904000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Feb 11 18:11:57 red-queen kernel: [    0.904000] TCP: Hash tables configured (established 131072 bind 65536)
Feb 11 18:11:57 red-queen kernel: [    0.904000] TCP reno registered
Feb 11 18:11:57 red-queen kernel: [    0.920000] checking if image is initramfs... it is
Feb 11 18:11:57 red-queen kernel: [    1.472000] Freeing initrd memory: 7441k freed
Feb 11 18:11:57 red-queen kernel: [    1.472000] Simple Boot Flag at 0x79 set to 0x1
Feb 11 18:11:57 red-queen kernel: [    1.472000] audit: initializing netlink socket (disabled)
Feb 11 18:11:57 red-queen kernel: [    1.472000] audit(1202775100.336:1): initialized
Feb 11 18:11:57 red-queen kernel: [    1.472000] highmem bounce pool size: 64 pages
Feb 11 18:11:57 red-queen kernel: [    1.476000] VFS: Disk quotas dquot_6.5.1
Feb 11 18:11:57 red-queen kernel: [    1.476000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb 11 18:11:57 red-queen kernel: [    1.476000] io scheduler noop registered
Feb 11 18:11:57 red-queen kernel: [    1.476000] io scheduler anticipatory registered
Feb 11 18:11:57 red-queen kernel: [    1.476000] io scheduler deadline registered
Feb 11 18:11:57 red-queen kernel: [    1.476000] io scheduler cfq registered (default)
Feb 11 18:11:57 red-queen kernel: [    1.476000] Boot video device is 0000:00:02.0
Feb 11 18:11:57 red-queen kernel: [    1.476000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Feb 11 18:11:57 red-queen kernel: [    1.476000] assign_interrupt_mode Found MSI capability
Feb 11 18:11:57 red-queen kernel: [    1.476000] Allocate Port Service[0000:00:1c.0:pcie00]
Feb 11 18:11:57 red-queen kernel: [    1.476000] Allocate Port Service[0000:00:1c.0:pcie02]
Feb 11 18:11:57 red-queen kernel: [    1.476000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Feb 11 18:11:57 red-queen kernel: [    1.476000] assign_interrupt_mode Found MSI capability
Feb 11 18:11:57 red-queen kernel: [    1.476000] Allocate Port Service[0000:00:1c.1:pcie00]
Feb 11 18:11:57 red-queen kernel: [    1.476000] Allocate Port Service[0000:00:1c.1:pcie02]
Feb 11 18:11:57 red-queen kernel: [    1.476000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Feb 11 18:11:57 red-queen kernel: [    1.476000] assign_interrupt_mode Found MSI capability
Feb 11 18:11:57 red-queen kernel: [    1.476000] Allocate Port Service[0000:00:1c.3:pcie00]
Feb 11 18:11:57 red-queen kernel: [    1.476000] Allocate Port Service[0000:00:1c.3:pcie02]
Feb 11 18:11:57 red-queen kernel: [    1.476000] isapnp: Scanning for PnP cards...
Feb 11 18:11:57 red-queen kernel: [    1.832000] isapnp: No Plug & Play device found
Feb 11 18:11:57 red-queen kernel: [    1.848000] Real Time Clock Driver v1.12ac
Feb 11 18:11:57 red-queen kernel: [    1.848000] hpet_resources: 0xfed00000 is busy
Feb 11 18:11:57 red-queen kernel: [    1.848000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Feb 11 18:11:57 red-queen kernel: [    1.848000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Feb 11 18:11:57 red-queen kernel: [    1.848000] input: Macintosh mouse button emulation as /class/input/input0
Feb 11 18:11:57 red-queen kernel: [    1.848000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Feb 11 18:11:57 red-queen kernel: [    1.852000] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 11 18:11:57 red-queen kernel: [    1.852000] serio: i8042 AUX port at 0x60,0x64 irq 12
Feb 11 18:11:57 red-queen kernel: [    1.852000] mice: PS/2 mouse device common for all mice
Feb 11 18:11:57 red-queen kernel: [    1.852000] EISA: Probing bus 0 at eisa.0
Feb 11 18:11:57 red-queen kernel: [    1.852000] Cannot allocate resource for EISA slot 1
Feb 11 18:11:57 red-queen kernel: [    1.852000] EISA: Detected 0 cards.
Feb 11 18:11:57 red-queen kernel: [    1.856000] TCP cubic registered
Feb 11 18:11:57 red-queen kernel: [    1.856000] NET: Registered protocol family 1
Feb 11 18:11:57 red-queen kernel: [    1.856000] Using IPI No-Shortcut mode
Feb 11 18:11:57 red-queen kernel: [    1.856000]   Magic number: 12:487:152
Feb 11 18:11:57 red-queen kernel: [    1.856000]   hash matches device ttyp6
Feb 11 18:11:57 red-queen kernel: [    1.856000] Freeing unused kernel memory: 364k freed
Feb 11 18:11:57 red-queen kernel: [    1.856000] input: AT Translated Set 2 keyboard as /class/input/input1
Feb 11 18:11:57 red-queen kernel: [    3.028000] AppArmor: AppArmor initialized<5>audit(1202775101.836:2):  type=1505 info="AppArmor initialized" pid=1255
Feb 11 18:11:57 red-queen kernel: [    3.032000] fuse init (API version 7.8)
Feb 11 18:11:57 red-queen kernel: [    3.036000] Failure registering capabilities with primary security module.
Feb 11 18:11:57 red-queen kernel: [    3.068000] ACPI: SSDT CF694134, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
Feb 11 18:11:57 red-queen kernel: [    3.068000] ACPI: SSDT CF693EE9, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
Feb 11 18:11:57 red-queen kernel: [    3.072000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Feb 11 18:11:57 red-queen kernel: [    3.072000] ACPI: Processor [CPU0] (supports 8 throttling states)
Feb 11 18:11:57 red-queen kernel: [    3.072000] ACPI: SSDT CF694378, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
Feb 11 18:11:57 red-queen kernel: [    3.072000] ACPI: SSDT CF6940AF, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
Feb 11 18:11:57 red-queen kernel: [    3.072000] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Feb 11 18:11:57 red-queen kernel: [    3.072000] ACPI: Processor [CPU1] (supports 8 throttling states)
Feb 11 18:11:57 red-queen kernel: [    3.076000] ACPI: Thermal Zone [THM] (37 C)
Feb 11 18:11:57 red-queen kernel: [    3.456000] usbcore: registered new interface driver usbfs
Feb 11 18:11:57 red-queen kernel: [    3.456000] usbcore: registered new interface driver hub
Feb 11 18:11:57 red-queen kernel: [    3.456000] usbcore: registered new device driver usb
Feb 11 18:11:57 red-queen kernel: [    3.460000] USB Universal Host Controller Interface driver v3.0
Feb 11 18:11:57 red-queen kernel: [    3.460000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
Feb 11 18:11:57 red-queen kernel: [    3.460000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Feb 11 18:11:57 red-queen kernel: [    3.460000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Feb 11 18:11:57 red-queen kernel: [    3.460000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Feb 11 18:11:57 red-queen kernel: [    3.460000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000bf80
Feb 11 18:11:57 red-queen kernel: [    3.460000] usb usb1: configuration #1 chosen from 1 choice
Feb 11 18:11:57 red-queen kernel: [    3.460000] hub 1-0:1.0: USB hub found
Feb 11 18:11:57 red-queen kernel: [    3.460000] hub 1-0:1.0: 2 ports detected
Feb 11 18:11:57 red-queen kernel: [    3.472000] SCSI subsystem initialized
Feb 11 18:11:57 red-queen kernel: [    3.476000] libata version 2.21 loaded.
Feb 11 18:11:57 red-queen kernel: [    3.564000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
Feb 11 18:11:57 red-queen kernel: [    3.564000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Feb 11 18:11:57 red-queen kernel: [    3.564000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Feb 11 18:11:57 red-queen kernel: [    3.564000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Feb 11 18:11:57 red-queen kernel: [    3.564000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000bf60
Feb 11 18:11:57 red-queen kernel: [    3.564000] usb usb2: configuration #1 chosen from 1 choice
Feb 11 18:11:57 red-queen kernel: [    3.564000] hub 2-0:1.0: USB hub found
Feb 11 18:11:57 red-queen kernel: [    3.564000] hub 2-0:1.0: 2 ports detected
Feb 11 18:11:57 red-queen kernel: [    3.668000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
Feb 11 18:11:57 red-queen kernel: [    3.668000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Feb 11 18:11:57 red-queen kernel: [    3.668000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Feb 11 18:11:57 red-queen kernel: [    3.668000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Feb 11 18:11:57 red-queen kernel: [    3.668000] uhci_hcd 0000:00:1d.2: irq 21, io base 0x0000bf40
Feb 11 18:11:57 red-queen kernel: [    3.668000] usb usb3: configuration #1 chosen from 1 choice
Feb 11 18:11:57 red-queen kernel: [    3.668000] hub 3-0:1.0: USB hub found
Feb 11 18:11:57 red-queen kernel: [    3.668000] hub 3-0:1.0: 2 ports detected
Feb 11 18:11:57 red-queen kernel: [    3.772000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 22
Feb 11 18:11:57 red-queen kernel: [    3.772000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Feb 11 18:11:57 red-queen kernel: [    3.772000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Feb 11 18:11:57 red-queen kernel: [    3.772000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Feb 11 18:11:57 red-queen kernel: [    3.772000] uhci_hcd 0000:00:1d.3: irq 22, io base 0x0000bf20
Feb 11 18:11:57 red-queen kernel: [    3.772000] usb usb4: configuration #1 chosen from 1 choice
Feb 11 18:11:57 red-queen kernel: [    3.772000] hub 4-0:1.0: USB hub found
Feb 11 18:11:57 red-queen kernel: [    3.772000] hub 4-0:1.0: 2 ports detected
Feb 11 18:11:57 red-queen kernel: [    3.816000] usb 1-1: new low speed USB device using uhci_hcd and address 2
Feb 11 18:11:57 red-queen kernel: [    3.876000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
Feb 11 18:11:57 red-queen kernel: [    3.876000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Feb 11 18:11:57 red-queen kernel: [    3.876000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Feb 11 18:11:57 red-queen kernel: [    3.876000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Feb 11 18:11:57 red-queen kernel: [    3.876000] ehci_hcd 0000:00:1d.7: debug port 1
Feb 11 18:11:57 red-queen kernel: [    3.876000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Feb 11 18:11:57 red-queen kernel: [    3.876000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa80000
Feb 11 18:11:57 red-queen kernel: [    3.932000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Feb 11 18:11:57 red-queen kernel: [    3.932000] usb usb5: configuration #1 chosen from 1 choice
Feb 11 18:11:57 red-queen kernel: [    3.932000] hub 5-0:1.0: USB hub found
Feb 11 18:11:57 red-queen kernel: [    3.932000] hub 5-0:1.0: 8 ports detected
Feb 11 18:11:57 red-queen kernel: [    4.000000] Clocksource tsc unstable (delta = -357359932 ns)
Feb 11 18:11:57 red-queen kernel: [    4.036000] b44.c:v1.01 (Jun 16, 2006)
Feb 11 18:11:57 red-queen kernel: [    4.036000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Feb 11 18:11:57 red-queen kernel: [    4.036000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:18:8b:ad:5a:8b
Feb 11 18:11:57 red-queen kernel: [    4.036000] ata_piix 0000:00:1f.2: version 2.11
Feb 11 18:11:57 red-queen kernel: [    4.036000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Feb 11 18:11:57 red-queen kernel: [    4.036000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
Feb 11 18:11:57 red-queen kernel: [    4.036000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Feb 11 18:11:57 red-queen kernel: [    4.040000] scsi0 : ata_piix
Feb 11 18:11:57 red-queen kernel: [    4.040000] scsi1 : ata_piix
Feb 11 18:11:57 red-queen kernel: [    4.040000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
Feb 11 18:11:57 red-queen kernel: [    4.040000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
Feb 11 18:11:57 red-queen kernel: [    4.260000] ata1.00: ATA-8: WDC WD2500BEVS-00UST0, 01.01A01, max UDMA/133
Feb 11 18:11:57 red-queen kernel: [    4.260000] ata1.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 0/32)
Feb 11 18:11:57 red-queen kernel: [    4.276000] ata1.00: configured for UDMA/133
Feb 11 18:11:57 red-queen kernel: [    4.340000] usb 1-1: device not accepting address 2, error -71
Feb 11 18:11:57 red-queen kernel: [    4.612000] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-L632D, DE03, max UDMA/33
Feb 11 18:11:57 red-queen kernel: [    4.800000] ata2.00: configured for UDMA/33
Feb 11 18:11:57 red-queen kernel: [    4.800000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-0 01.0 PQ: 0 ANSI: 5
Feb 11 18:11:57 red-queen kernel: [    4.800000] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632D DE03 PQ: 0 ANSI: 5
Feb 11 18:11:57 red-queen kernel: [    4.800000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 18
Feb 11 18:11:57 red-queen kernel: [    4.852000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Feb 11 18:11:57 red-queen kernel: [    4.868000] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Feb 11 18:11:57 red-queen kernel: [    4.868000] sd 0:0:0:0: [sda] Write Protect is off
Feb 11 18:11:57 red-queen kernel: [    4.868000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 11 18:11:57 red-queen kernel: [    4.868000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 11 18:11:57 red-queen kernel: [    4.868000] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Feb 11 18:11:57 red-queen kernel: [    4.868000] sd 0:0:0:0: [sda] Write Protect is off
Feb 11 18:11:57 red-queen kernel: [    4.868000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 11 18:11:57 red-queen kernel: [    4.868000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 11 18:11:57 red-queen kernel: [    4.868000]  sda: sda1 sda2 < sda5 >
Feb 11 18:11:57 red-queen kernel: [    4.936000] sd 0:0:0:0: [sda] Attached SCSI disk
Feb 11 18:11:57 red-queen kernel: [    4.940000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Feb 11 18:11:57 red-queen kernel: [    4.940000] sr 1:0:0:0: Attached scsi generic sg1 type 5
Feb 11 18:11:57 red-queen kernel: [    4.940000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Feb 11 18:11:57 red-queen kernel: [    4.940000] Uniform CD-ROM driver Revision: 3.20
Feb 11 18:11:57 red-queen kernel: [    4.940000] sr 1:0:0:0: Attached scsi CD-ROM sr0
Feb 11 18:11:57 red-queen kernel: [    5.180000] Attempting manual resume
Feb 11 18:11:57 red-queen kernel: [    5.180000] swsusp: Resume From Partition 8:5
Feb 11 18:11:57 red-queen kernel: [    5.180000] PM: Checking swsusp image.
Feb 11 18:11:57 red-queen kernel: [    5.180000] PM: Resume from disk failed.
Feb 11 18:11:57 red-queen kernel: [    5.228000] kjournald starting.  Commit interval 5 seconds
Feb 11 18:11:57 red-queen kernel: [    5.228000] EXT3-fs: mounted filesystem with ordered data mode.
Feb 11 18:11:57 red-queen kernel: [    5.380000] usb 5-2: new high speed USB device using ehci_hcd and address 3
Feb 11 18:11:57 red-queen kernel: [    5.528000] usb 5-2: configuration #1 chosen from 2 choices
Feb 11 18:11:57 red-queen kernel: [    5.776000] usb 5-5: new high speed USB device using ehci_hcd and address 4
Feb 11 18:11:57 red-queen kernel: [    6.088000] usb 5-5: configuration #1 chosen from 1 choice
Feb 11 18:11:57 red-queen kernel: [    6.128000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[444fc00007dea161]
Feb 11 18:11:57 red-queen kernel: [    6.568000] usb 5-8: new high speed USB device using ehci_hcd and address 6
Feb 11 18:11:57 red-queen kernel: [    6.712000] usb 5-8: configuration #1 chosen from 1 choice
Feb 11 18:11:57 red-queen kernel: [    6.956000] usb 3-2: new full speed USB device using uhci_hcd and address 2
Feb 11 18:11:57 red-queen kernel: [    7.116000] usb 3-2: configuration #1 chosen from 1 choice
Feb 11 18:11:57 red-queen kernel: [    7.360000] usb 1-1: new low speed USB device using uhci_hcd and address 4
Feb 11 18:11:57 red-queen kernel: [    7.536000] usb 1-1: configuration #1 chosen from 1 choice
Feb 11 18:11:57 red-queen kernel: [   11.252000] Linux agpgart interface v0.102 (c) Dave Jones
Feb 11 18:11:57 red-queen kernel: [   11.300000] agpgart: Detected an Intel 945GM Chipset.
Feb 11 18:11:57 red-queen kernel: [   11.304000] agpgart: Detected 7932K stolen memory.
Feb 11 18:11:57 red-queen kernel: [   11.320000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb 11 18:11:57 red-queen kernel: [   11.320000] agpgart: AGP aperture is 256M @ 0xd0000000
Feb 11 18:11:57 red-queen kernel: [   11.332000] iTCO_vendor_support: vendor-support=0
Feb 11 18:11:57 red-queen kernel: [   11.332000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
Feb 11 18:11:57 red-queen kernel: [   11.332000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Feb 11 18:11:57 red-queen kernel: [   11.332000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Feb 11 18:11:57 red-queen kernel: [   11.340000] intel_rng: FWH not detected
Feb 11 18:11:57 red-queen kernel: [   11.464000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Feb 11 18:11:57 red-queen kernel: [   11.480000] input: PC Speaker as /class/input/input2
Feb 11 18:11:57 red-queen kernel: [   11.592000] sdhci: Secure Digital Host Controller Interface driver
Feb 11 18:11:57 red-queen kernel: [   11.592000] sdhci: Copyright(c) Pierre Ossman
Feb 11 18:11:57 red-queen kernel: [   11.592000] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
Feb 11 18:11:57 red-queen kernel: [   11.592000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 23
Feb 11 18:11:57 red-queen kernel: [   11.592000] mmc0: SDHCI at 0xef9fd400 irq 23 DMA
Feb 11 18:11:57 red-queen kernel: [   11.788000] usbcore: registered new interface driver libusual
Feb 11 18:11:57 red-queen kernel: [   11.832000] Linux video capture interface: v2.00
Feb 11 18:11:57 red-queen kernel: [   11.832000] usbcore: registered new interface driver hiddev
Feb 11 18:11:57 red-queen kernel: [   11.848000] input: Microsoft Basic Optical Mouse as /class/input/input3
Feb 11 18:11:57 red-queen kernel: [   11.848000] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.0-1
Feb 11 18:11:57 red-queen kernel: [   11.848000] usbcore: registered new interface driver usbhid
Feb 11 18:11:57 red-queen kernel: [   11.848000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Feb 11 18:11:57 red-queen kernel: [   11.888000] NET: Registered protocol family 17
Feb 11 18:11:57 red-queen kernel: [   11.936000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb 11 18:11:57 red-queen kernel: [   11.936000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb 11 18:11:57 red-queen kernel: [   11.968000] Initializing USB Mass Storage driver...
Feb 11 18:11:57 red-queen kernel: [   11.968000] scsi2 : SCSI emulation for USB Mass Storage devices
Feb 11 18:11:57 red-queen kernel: [   11.968000] usb-storage: device found at 3
Feb 11 18:11:57 red-queen kernel: [   11.968000] usb-storage: waiting for device to settle before scanning
Feb 11 18:11:57 red-queen kernel: [   11.968000] scsi3 : SCSI emulation for USB Mass Storage devices
Feb 11 18:11:57 red-queen kernel: [   11.968000] usb-storage: device found at 6
Feb 11 18:11:57 red-queen kernel: [   11.968000] usb-storage: waiting for device to settle before scanning
Feb 11 18:11:57 red-queen kernel: [   11.968000] usbcore: registered new interface driver usb-storage
Feb 11 18:11:57 red-queen kernel: [   11.968000] USB Mass Storage support registered.
Feb 11 18:11:57 red-queen kernel: [   11.980000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c6)
Feb 11 18:11:57 red-queen kernel: [   11.992000] usbcore: registered new interface driver uvcvideo
Feb 11 18:11:57 red-queen kernel: [   11.992000] USB Video Class driver (v0.1.0)
Feb 11 18:11:57 red-queen kernel: [   12.036000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
Feb 11 18:11:57 red-queen kernel: [   12.036000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Feb 11 18:11:57 red-queen kernel: [   12.052000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04713/0x200000
Feb 11 18:11:57 red-queen kernel: [   12.088000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
Feb 11 18:11:57 red-queen kernel: [   12.108000] usbcore: registered new interface driver snd-usb-audio
Feb 11 18:11:57 red-queen kernel: [   13.420000] hda_intel: azx_get_response timeout, switching to polling mode...
Feb 11 18:11:57 red-queen kernel: [   13.636000] lp: driver loaded but no devices found
Feb 11 18:11:57 red-queen kernel: [   13.700000] usbcore: registered new interface driver usbserial
Feb 11 18:11:57 red-queen kernel: [   13.704000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Feb 11 18:11:57 red-queen kernel: [   13.704000] usbserial_generic 3-2:1.0: generic converter detected
Feb 11 18:11:57 red-queen kernel: [   13.708000] usb 3-2: generic converter now attached to ttyUSB0
Feb 11 18:11:57 red-queen kernel: [   13.708000] usbserial_generic 3-2:1.1: generic converter detected
Feb 11 18:11:57 red-queen kernel: [   13.712000] usb 3-2: generic converter now attached to ttyUSB1
Feb 11 18:11:57 red-queen kernel: [   13.712000] usbcore: registered new interface driver usbserial_generic
Feb 11 18:11:57 red-queen kernel: [   13.712000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
Feb 11 18:11:57 red-queen kernel: [   13.776000] ndiswrapper version 1.45 loaded (smp=yes)
Feb 11 18:11:57 red-queen kernel: [   13.852000] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
Feb 11 18:11:57 red-queen kernel: [   13.852000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Feb 11 18:11:57 red-queen kernel: [   13.852000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
Feb 11 18:11:57 red-queen kernel: [   13.868000] ndiswrapper: using IRQ 17
Feb 11 18:11:57 red-queen kernel: [   14.068000] wlan0: ethernet device 00:19:7d:22:d9:ca using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: '', 14E4:4328.5.conf
Feb 11 18:11:57 red-queen kernel: [   14.068000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Feb 11 18:11:57 red-queen kernel: [   14.072000] usbcore: registered new interface driver ndiswrapper
Feb 11 18:11:57 red-queen kernel: [   14.148000] Adding 9855836k swap on /dev/sda5.  Priority:-1 extents:1 across:9855836k
Feb 11 18:11:57 red-queen kernel: [   14.672000] EXT3 FS on sda1, internal journal
Feb 11 18:11:57 red-queen kernel: [   16.900000] ACPI: AC Adapter [AC] (on-line)
Feb 11 18:11:57 red-queen kernel: [   16.928000] ACPI: Battery Slot [BAT0] (battery present)
Feb 11 18:11:57 red-queen kernel: [   16.936000] No dock devices found.
Feb 11 18:11:57 red-queen kernel: [   16.968000] usb-storage: device scan complete
Feb 11 18:11:57 red-queen kernel: [   16.968000] usb-storage: device scan complete
Feb 11 18:11:57 red-queen kernel: [   16.968000] scsi 3:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100D PQ: 0 ANSI: 4
Feb 11 18:11:57 red-queen kernel: [   16.972000] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Feb 11 18:11:57 red-queen kernel: [   16.976000] sd 2:0:0:0: [sdb] 19488471 4096-byte hardware sectors (79825 MB)
Feb 11 18:11:57 red-queen kernel: [   16.976000] sd 2:0:0:0: [sdb] Write Protect is off
Feb 11 18:11:57 red-queen kernel: [   16.976000] sd 2:0:0:0: [sdb] Mode Sense: 68 00 00 08
Feb 11 18:11:57 red-queen kernel: [   16.976000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Feb 11 18:11:57 red-queen kernel: [   16.976000] sd 2:0:0:0: [sdb] 19488471 4096-byte hardware sectors (79825 MB)
Feb 11 18:11:57 red-queen kernel: [   16.976000] sd 2:0:0:0: [sdb] Write Protect is off
Feb 11 18:11:57 red-queen kernel: [   16.976000] sd 2:0:0:0: [sdb] Mode Sense: 68 00 00 08
Feb 11 18:11:57 red-queen kernel: [   16.976000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Feb 11 18:11:57 red-queen kernel: [   16.976000]  sdb:<6>ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Feb 11 18:11:57 red-queen kernel: [   17.040000] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
Feb 11 18:11:57 red-queen kernel: [   17.040000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Feb 11 18:11:57 red-queen kernel: [   17.048000] input: Lid Switch as /class/input/input5
Feb 11 18:11:57 red-queen kernel: [   17.048000] ACPI: Lid Switch [LID]
Feb 11 18:11:57 red-queen kernel: [   17.048000] input: Power Button (CM) as /class/input/input6
Feb 11 18:11:57 red-queen kernel: [   17.048000] ACPI: Power Button (CM) [PBTN]
Feb 11 18:11:57 red-queen kernel: [   17.048000] input: Sleep Button (CM) as /class/input/input7
Feb 11 18:11:57 red-queen kernel: [   17.048000] ACPI: Sleep Button (CM) [SBTN]
Feb 11 18:11:57 red-queen kernel: [   17.228000]  sdb1
Feb 11 18:11:57 red-queen kernel: [   17.228000] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Feb 11 18:11:57 red-queen kernel: [   17.228000] sd 2:0:0:0: Attached scsi generic sg2 type 0
Feb 11 18:11:57 red-queen kernel: [   17.232000] sd 3:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
Feb 11 18:11:57 red-queen kernel: [   17.232000] sd 3:0:0:0: [sdc] Write Protect is off
Feb 11 18:11:57 red-queen kernel: [   17.232000] sd 3:0:0:0: [sdc] Mode Sense: 1c 00 00 00
Feb 11 18:11:57 red-queen kernel: [   17.232000] sd 3:0:0:0: [sdc] Assuming drive cache: write through
Feb 11 18:11:57 red-queen kernel: [   17.240000] sd 3:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
Feb 11 18:11:57 red-queen kernel: [   17.244000] sd 3:0:0:0: [sdc] Write Protect is off
Feb 11 18:11:57 red-queen kernel: [   17.244000] sd 3:0:0:0: [sdc] Mode Sense: 1c 00 00 00
Feb 11 18:11:57 red-queen kernel: [   17.244000] sd 3:0:0:0: [sdc] Assuming drive cache: write through
Feb 11 18:11:57 red-queen kernel: [   17.244000]  sdc: sdc1
Feb 11 18:11:57 red-queen kernel: [   17.264000] sd 3:0:0:0: [sdc] Attached SCSI disk
Feb 11 18:11:57 red-queen kernel: [   17.264000] sd 3:0:0:0: Attached scsi generic sg3 type 0
Feb 11 18:11:57 red-queen NetworkManager: <info>  starting... 
Feb 11 18:11:57 red-queen NetworkManager: <debug> [1202775117.671368] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_bluetooth_switch'). 
Feb 11 18:11:57 red-queen kernel: [   18.256000] ppdev: user-space parallel port driver
Feb 11 18:11:58 red-queen kernel: [   18.544000] audit(1202775117.851:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5259 profile="/usr/sbin/cupsd"
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.087282] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/dell_wlan_switch'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.087798] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.088195] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a2'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.088553] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27a6'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.088905] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.089286] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.089704] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d2'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.154986] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_4328'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.155506] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d6'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.155906] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c8'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.156271] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.156940] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_if0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.157382] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_84_noserial'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.157752] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_84_noserial_if0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.158111] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c9'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.158480] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.158827] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_if0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.159566] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27ca'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.159888] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.160203] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_if0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.160518] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8114_noserial'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.160832] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8114_noserial_if0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.161145] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8114_noserial_if1'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.161456] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cb'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.161767] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.162077] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_if0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.162388] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27cc'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.162699] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.163023] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_if0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.163335] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5ac_1261_000A2700132DAABF'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.163647] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5ac_1261_000A2700132DAABF_if0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.163958] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5ac_1261_000A2700132DAABF_if0_scsi_host'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.164690] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5ac_1261_000A2700132DAABF_if0_scsi_host_scsi_device_lun0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.165006] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8c6_BC92DD91'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.165321] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8c6_BC92DD91_if0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.165633] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8c6_BC92DD91_if1'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.218827] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8c6_BC92DD91_if2'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.219163] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8c6_BC92DD91_if3'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.219482] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3GJ27'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.219800] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3GJ27_if0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.220115] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3GJ27_if0_scsi_host'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.220431] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3GJ27_if0_scsi_host_scsi_device_lun0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.220747] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2448'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.221099] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_14e4_170c'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.221505] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_832'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.221835] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.222227] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_843'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.222568] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_592'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.224375] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_852'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.224694] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27b9'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.225008] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.225320] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.225664] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.226059] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.226387] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.226754] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27da'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.227068] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.227415] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.227817] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.228151] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.230285] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_iTCO_wdt'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.230604] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.230928] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.231241] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.231552] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.231895] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.232289] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_1'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.232615] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0f13'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.232972] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.233283] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.233591] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.233899] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01_2'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.234207] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.234514] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.234828] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0103'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.235134] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.235440] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_backlight_0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.235746] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.236052] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.236358] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_84_noserial_if0_logicaldev_input'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.236664] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.236970] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.237287] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.237592] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_18_8b_ad_5a_8b'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.246999] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_19_7d_22_d9_ca'). 
Feb 11 18:11:58 red-queen NetworkManager: <info>  wlan0: Device is fully-supported using driver 'ndiswrapper'. 
Feb 11 18:11:58 red-queen NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Feb 11 18:11:58 red-queen NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Feb 11 18:11:58 red-queen NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Feb 11 18:11:58 red-queen NetworkManager: <info>  Deactivating device wlan0. 
Feb 11 18:11:58 red-queen NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.309325] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_scsi_device_lun0_scsi_generic'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.309692] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27c4_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.310010] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5ac_1261_000A2700132DAABF_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.310327] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3GJ27_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.310646] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_1'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.310971] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.311283] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8c6_BC92DD91_if2_oss_pcm_0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.311597] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_control__1'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.311909] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8c6_BC92DD91_if2_alsa_control__1'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.312221] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_pcm_0_0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.312531] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8c6_BC92DD91_if2_oss_pcm_0_0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.312844] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_oss_mixer__1'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.313152] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8c6_BC92DD91_if2_oss_mixer__1'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.313463] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_capture_0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.313773] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.314081] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_27d8_alsa_playback_1'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.314389] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8c6_BC92DD91_if2_alsa_capture_0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.314700] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.315017] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.315326] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.315633] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.315941] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.316253] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.316562] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.316874] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.317184] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8114_noserial_if0_serial_usb_0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.317493] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8114_noserial_if1_serial_usb_1'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.317800] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_0_usbraw'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.318107] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_45e_84_noserial_usbraw'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.318415] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_1_usbraw'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.318722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_2_usbraw'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.319043] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8114_noserial_usbraw'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.319351] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_3_usbraw'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.319658] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_1d_7_usbraw'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.319965] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5ac_1261_000A2700132DAABF_usbraw'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.320273] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8c6_BC92DD91_usbraw'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.320579] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________9QF3GJ27_usbraw'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.320886] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_8c6_BC92DD91_video4linux'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.321192] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_WDC_WD2500BEVS_00UST0_WD_WXE707152580'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.321499] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_1bd6342d_430a_40f6_8687_a523abbc165c'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.397322] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part2_size_1024'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.401214] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_10a71afc_c6e9_4d3d_b242_7432fb4e1490'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.616394] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Apple_iPod_000A2700132DAABF_0_0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.636692] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_3141_5926'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.654732] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Seagate_FreeAgentDesktop_9QF3GJ27_0_0'). 
Feb 11 18:11:58 red-queen kernel: [   19.168000] apm: BIOS not found.
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.756951] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_3664D6F264D6B439'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.803970] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_BAT0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.829043] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU1'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.829385] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.829729] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_AC'). 
Feb 11 18:11:58 red-queen NetworkManager: <debug> [1202775118.830883] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD__RW_TS_L632D'). 
Feb 11 18:11:58 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:11:58 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:11:58 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:11:58 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:11:59 red-queen NetworkManager: <debug> [1202775119.085543] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_554039296'). 
Feb 11 18:11:59 red-queen kernel: [   19.640000] Failure registering capabilities with primary security module.
Feb 11 18:11:59 red-queen avahi-daemon[5516]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Feb 11 18:11:59 red-queen avahi-daemon[5516]: Successfully dropped root privileges.
Feb 11 18:11:59 red-queen avahi-daemon[5516]: avahi-daemon 0.6.20 starting up.
Feb 11 18:11:59 red-queen avahi-daemon[5516]: Successfully called chroot().
Feb 11 18:11:59 red-queen avahi-daemon[5516]: Successfully dropped remaining capabilities.
Feb 11 18:11:59 red-queen avahi-daemon[5516]: No service file found in /etc/avahi/services.
Feb 11 18:11:59 red-queen avahi-daemon[5516]: Network interface enumeration completed.
Feb 11 18:11:59 red-queen avahi-daemon[5516]: Registering HINFO record with values 'I686'/'LINUX'.
Feb 11 18:11:59 red-queen avahi-daemon[5516]: Server startup complete. Host name is red-queen.local. Local service cookie is 2823509104.
Feb 11 18:11:59 red-queen dhcdbd: Started up.
Feb 11 18:11:59 red-queen hcid[5551]: Bluetooth HCI daemon
Feb 11 18:11:59 red-queen kernel: [   20.296000] Bluetooth: Core ver 2.11
Feb 11 18:11:59 red-queen kernel: [   20.296000] NET: Registered protocol family 31
Feb 11 18:11:59 red-queen kernel: [   20.296000] Bluetooth: HCI device and connection manager initialized
Feb 11 18:11:59 red-queen kernel: [   20.296000] Bluetooth: HCI socket layer initialized
Feb 11 18:11:59 red-queen hcid[5551]: Starting SDP server
Feb 11 18:11:59 red-queen kernel: [   20.324000] Bluetooth: L2CAP ver 2.8
Feb 11 18:11:59 red-queen kernel: [   20.324000] Bluetooth: L2CAP socket layer initialized
Feb 11 18:11:59 red-queen hcid[5551]: Created local server at unix:abstract=/var/run/dbus-JQMf1nZI45,guid=5ab016c525b997eb2b12130047b0e44f
Feb 11 18:11:59 red-queen audio[5568]: Bluetooth Audio daemon
Feb 11 18:11:59 red-queen audio[5568]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Feb 11 18:11:59 red-queen audio[5568]: Unix socket created: 5
Feb 11 18:11:59 red-queen kernel: [   20.388000] Bluetooth: RFCOMM socket layer initialized
Feb 11 18:11:59 red-queen kernel: [   20.388000] Bluetooth: RFCOMM TTY layer initialized
Feb 11 18:11:59 red-queen kernel: [   20.388000] Bluetooth: RFCOMM ver 1.8
Feb 11 18:11:59 red-queen input[5569]: Bluetooth Input daemon
Feb 11 18:11:59 red-queen audio[5568]: add_service_record: got record id 0x10000
Feb 11 18:11:59 red-queen input[5569]: Registered input manager path:/org/bluez/input
Feb 11 18:11:59 red-queen audio[5568]: add_service_record: got record id 0x10001
Feb 11 18:11:59 red-queen audio[5568]: Registered manager path:/org/bluez/audio
Feb 11 18:12:00 red-queen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Feb 11 18:12:00 red-queen dhclient: isc-dhclient-V3.0.5
Feb 11 18:12:01 red-queen kernel: [   22.356000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Feb 11 18:12:01 red-queen kernel: [   22.356000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
Feb 11 18:12:01 red-queen kernel: [   22.360000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Feb 11 18:12:01 red-queen kernel: [   22.360000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
Feb 11 18:12:01 red-queen kernel: [   22.364000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Feb 11 18:12:01 red-queen kernel: [   22.364000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
Feb 11 18:12:01 red-queen kernel: [   22.368000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Feb 11 18:12:01 red-queen kernel: [   22.368000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
Feb 11 18:12:01 red-queen kernel: [   22.372000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Feb 11 18:12:01 red-queen kernel: [   22.372000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
Feb 11 18:12:01 red-queen kernel: [   22.372000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Feb 11 18:12:01 red-queen kernel: [   22.372000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
Feb 11 18:12:01 red-queen kernel: [   22.444000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Feb 11 18:12:01 red-queen kernel: [   22.444000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
Feb 11 18:12:02 red-queen kernel: [   22.488000] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
Feb 11 18:12:02 red-queen kernel: [   22.488000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
Feb 11 18:12:02 red-queen anacron[5641]: Anacron 2.3 started on 2008-02-11
Feb 11 18:12:02 red-queen anacron[5641]: Normal exit (0 jobs run)
Feb 11 18:12:02 red-queen /usr/sbin/cron[5668]: (CRON) INFO (pidfile fd = 3)
Feb 11 18:12:02 red-queen /usr/sbin/cron[5669]: (CRON) STARTUP (fork ok)
Feb 11 18:12:02 red-queen /usr/sbin/cron[5669]: (CRON) INFO (Running @reboot jobs)
Feb 11 18:12:02 red-queen kernel: [   22.860000] usb 2-1: new full speed USB device using uhci_hcd and address 2
Feb 11 18:12:02 red-queen kernel: [   23.044000] usb 2-1: configuration #1 chosen from 1 choice
Feb 11 18:12:02 red-queen NetworkManager: <debug> [1202775122.565066] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial'). 
Feb 11 18:12:02 red-queen kernel: [   23.064000] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
Feb 11 18:12:02 red-queen kernel: [   23.064000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
Feb 11 18:12:02 red-queen kernel: [   23.112000] Bluetooth: HCI USB driver ver 2.9
Feb 11 18:12:02 red-queen hcid[5551]: HCI dev 0 registered
Feb 11 18:12:02 red-queen kernel: [   23.112000] usbcore: registered new interface driver hci_usb
Feb 11 18:12:02 red-queen NetworkManager: <debug> [1202775122.643084] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if0'). 
Feb 11 18:12:02 red-queen NetworkManager: <debug> [1202775122.658420] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if1'). 
Feb 11 18:12:02 red-queen hcid[5551]: HCI dev 0 up
Feb 11 18:12:02 red-queen hcid[5551]: Device hci0 has been added
Feb 11 18:12:02 red-queen NetworkManager: <debug> [1202775122.667439] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if3'). 
Feb 11 18:12:02 red-queen NetworkManager: <debug> [1202775122.669205] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if2'). 
Feb 11 18:12:02 red-queen NetworkManager: <debug> [1202775122.669713] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if0_bluetooth_hci'). 
Feb 11 18:12:02 red-queen hcid[5551]: Starting security manager 0
Feb 11 18:12:02 red-queen NetworkManager: <debug> [1202775122.686937] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_usbraw'). 
Feb 11 18:12:02 red-queen hcid[5551]: Device hci0 has been activated
Feb 11 18:12:03 red-queen kernel: [   24.452000] [drm] Initialized drm 1.1.0 20060810
Feb 11 18:12:03 red-queen kernel: [   24.456000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Feb 11 18:12:03 red-queen kernel: [   24.456000] [drm] Initialized i915 1.6.0 20060119 on minor 0
Feb 11 18:12:04 red-queen kernel: [   25.312000] usb 2-1: USB disconnect, address 2
Feb 11 18:12:04 red-queen hcid[5551]: HCI dev 0 down
Feb 11 18:12:04 red-queen hcid[5551]: Stopping security manager 0
Feb 11 18:12:04 red-queen hcid[5551]: Device hci0 has been disabled
Feb 11 18:12:04 red-queen NetworkManager: <debug> [1202775124.836840] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if0_bluetooth_hci'). 
Feb 11 18:12:05 red-queen hcid[5551]: HCI dev 0 unregistered
Feb 11 18:12:05 red-queen hcid[5551]: Unregister path: /org/bluez/hci0
Feb 11 18:12:05 red-queen hcid[5551]: Device hci0 has been removed
Feb 11 18:12:05 red-queen NetworkManager: <debug> [1202775125.086133] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if0'). 
Feb 11 18:12:05 red-queen NetworkManager: <debug> [1202775125.089220] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if3'). 
Feb 11 18:12:05 red-queen NetworkManager: <debug> [1202775125.092099] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if1'). 
Feb 11 18:12:05 red-queen NetworkManager: <debug> [1202775125.092729] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if2'). 
Feb 11 18:12:05 red-queen NetworkManager: <debug> [1202775125.095724] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial'). 
Feb 11 18:12:05 red-queen NetworkManager: <debug> [1202775125.098311] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_usbraw'). 
Feb 11 18:12:05 red-queen kernel: [   25.804000] usb 2-1: new full speed USB device using uhci_hcd and address 3
Feb 11 18:12:05 red-queen kernel: [   25.968000] usb 2-1: configuration #1 chosen from 1 choice
Feb 11 18:12:05 red-queen NetworkManager: <debug> [1202775125.492669] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial'). 
Feb 11 18:12:05 red-queen hcid[5551]: HCI dev 0 registered
Feb 11 18:12:05 red-queen hcid[5551]: HCI dev 0 up
Feb 11 18:12:05 red-queen hcid[5551]: Device hci0 has been added
Feb 11 18:12:05 red-queen hcid[5551]: Starting security manager 0
Feb 11 18:12:05 red-queen NetworkManager: <debug> [1202775125.579604] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if1'). 
Feb 11 18:12:05 red-queen hcid[5551]: Device hci0 has been activated
Feb 11 18:12:05 red-queen NetworkManager: <debug> [1202775125.601546] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if0'). 
Feb 11 18:12:05 red-queen NetworkManager: <debug> [1202775125.602324] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if0_bluetooth_hci'). 
Feb 11 18:12:05 red-queen NetworkManager: <debug> [1202775125.626890] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if3'). 
Feb 11 18:12:05 red-queen NetworkManager: <debug> [1202775125.663982] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_if2'). 
Feb 11 18:12:05 red-queen NetworkManager: <debug> [1202775125.681412] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_413c_8126_noserial_usbraw'). 
Feb 11 18:12:13 red-queen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Feb 11 18:12:22 red-queen ntfs-3g[6117]: Version 1.1120 
Feb 11 18:12:22 red-queen ntfs-3g[6117]: Mounted /dev/sdc1 (Read-Write, label "The Hive", NTFS 3.1) 
Feb 11 18:12:22 red-queen ntfs-3g[6117]: Cmdline options: rw,nosuid,nodev,locale=en_US.UTF-8 
Feb 11 18:12:22 red-queen ntfs-3g[6117]: Mount options: rw,nosuid,nodev,silent,allow_other,nonempty,relatime,fsname=/dev/sdc1,blkdev,blksize=4096 
Feb 11 18:12:22 red-queen hald: mounted /dev/sdc1 on behalf of uid 1000
Feb 11 18:12:22 red-queen hald: mounted /dev/sdb1 on behalf of uid 1000
Feb 11 18:12:23 red-queen dhclient: No DHCPOFFERS received.
Feb 11 18:12:23 red-queen dhclient: No working leases in persistent database - sleeping.
Feb 11 18:12:23 red-queen avahi-autoipd(eth0)[6145]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Feb 11 18:12:23 red-queen avahi-autoipd(eth0)[6145]: Successfully called chroot().
Feb 11 18:12:23 red-queen avahi-autoipd(eth0)[6145]: Successfully dropped root privileges.
Feb 11 18:12:23 red-queen avahi-autoipd(eth0)[6145]: Starting with address 169.254.7.85
Feb 11 18:12:26 red-queen hcid[5551]: Default passkey agent (:1.24, /org/bluez/passkey) registered
Feb 11 18:12:26 red-queen hcid[5551]: Default authorization agent (:1.24, /org/bluez/auth) registered
Feb 11 18:12:28 red-queen avahi-autoipd(eth0)[6145]: Callout BIND, address 169.254.7.85 on interface eth0
Feb 11 18:12:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:12:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:12:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:12:30 red-queen avahi-daemon[5516]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.7.85.
Feb 11 18:12:30 red-queen avahi-daemon[5516]: New relevant interface eth0.IPv4 for mDNS.
Feb 11 18:12:30 red-queen avahi-daemon[5516]: Registering new address record for 169.254.7.85 on eth0.IPv4.
Feb 11 18:12:31 red-queen kernel: [   52.264000] PPP generic driver version 2.4.2
Feb 11 18:12:31 red-queen NetworkManager: <info>  Updating allowed wireless network lists. 
Feb 11 18:12:32 red-queen pppd[6192]: pppd 2.4.4 started by matt, uid 1000
Feb 11 18:12:32 red-queen kernel: [   52.904000] NET: Registered protocol family 10
Feb 11 18:12:32 red-queen kernel: [   52.904000] lo: Disabled Privacy Extensions
Feb 11 18:12:32 red-queen kernel: [   52.904000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 11 18:12:32 red-queen kernel: [   52.904000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 11 18:12:32 red-queen pppd[6192]: Using interface ppp0
Feb 11 18:12:32 red-queen pppd[6192]: Connect: ppp0 <--> /dev/ttyUSB0
Feb 11 18:12:32 red-queen avahi-autoipd(eth0)[6145]: Successfully claimed IP address 169.254.7.85
Feb 11 18:12:33 red-queen kernel: [   53.736000] PPP BSD Compression module registered
Feb 11 18:12:33 red-queen kernel: [   54.308000] PPP Deflate Compression module registered
Feb 11 18:12:33 red-queen pppd[6192]: not replacing existing default route through eth0
Feb 11 18:12:33 red-queen pppd[6192]: Cannot determine ethernet address for proxy ARP
Feb 11 18:12:33 red-queen pppd[6192]: local  IP address 70.216.106.26
Feb 11 18:12:33 red-queen pppd[6192]: remote IP address 66.174.46.4
Feb 11 18:12:33 red-queen pppd[6192]: primary   DNS address 69.78.96.14
Feb 11 18:12:33 red-queen pppd[6192]: secondary DNS address 66.174.92.14
Feb 11 18:12:54 red-queen ntpdate[6279]: can't find host ntp.ubuntu.com 
Feb 11 18:12:54 red-queen ntpdate[6279]: no servers can be used, exiting
Feb 11 18:12:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:12:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:12:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:13:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:13:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:13:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:13:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:13:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:13:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:14:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:14:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:14:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:14:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:14:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:14:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:15:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:15:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:15:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:15:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:15:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:15:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:16:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:16:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:16:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:16:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:16:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:16:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:17:01 red-queen /USR/SBIN/CRON[6525]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 11 18:17:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:17:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:17:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:17:47 red-queen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Feb 11 18:17:53 red-queen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Feb 11 18:17:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:17:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:17:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:18:08 red-queen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Feb 11 18:18:18 red-queen dhclient: No DHCPOFFERS received.
Feb 11 18:18:18 red-queen dhclient: No working leases in persistent database - sleeping.
Feb 11 18:18:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:18:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:18:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:18:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:18:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:18:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:19:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:19:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:19:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:19:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:19:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:19:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:20:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:20:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:20:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:20:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:20:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:20:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:21:15 red-queen kernel: [  575.732000] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Feb 11 18:21:15 red-queen kernel: [  575.732000] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0xbe data 30576 in
Feb 11 18:21:15 red-queen kernel: [  575.732000]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Feb 11 18:21:20 red-queen kernel: [  580.780000] ata2: port is slow to respond, please be patient (Status 0xd0)
Feb 11 18:21:25 red-queen kernel: [  585.764000] ata2: device not ready (errno=-16), forcing hardreset
Feb 11 18:21:25 red-queen kernel: [  585.764000] ata2: soft resetting port
Feb 11 18:21:25 red-queen kernel: [  586.288000] ata2.00: configured for UDMA/33
Feb 11 18:21:25 red-queen kernel: [  586.288000] ata2: EH complete
Feb 11 18:21:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:21:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:21:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:21:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:21:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:21:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:22:15 red-queen kernel: [  636.292000] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Feb 11 18:22:15 red-queen kernel: [  636.292000] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0xbe data 30576 in
Feb 11 18:22:15 red-queen kernel: [  636.292000]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Feb 11 18:22:20 red-queen kernel: [  641.332000] ata2: port is slow to respond, please be patient (Status 0xd0)
Feb 11 18:22:25 red-queen kernel: [  646.316000] ata2: device not ready (errno=-16), forcing hardreset
Feb 11 18:22:25 red-queen kernel: [  646.316000] ata2: soft resetting port
Feb 11 18:22:26 red-queen kernel: [  647.064000] ata2.00: configured for UDMA/33
Feb 11 18:22:26 red-queen kernel: [  647.064000] ata2: EH complete
Feb 11 18:22:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:22:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:22:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:22:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:22:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:22:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:23:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:23:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:23:29 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:23:47 red-queen NetworkManager: <debug> [1202775827.873576] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_554039296'). 
Feb 11 18:23:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:23:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:23:59 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:24:21 red-queen NetworkManager: <debug> [1202775861.957421] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_554039296'). 
Feb 11 18:24:30 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:24:30 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:24:30 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:25:00 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:25:00 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:25:00 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:25:27 red-queen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Feb 11 18:25:30 red-queen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Feb 11 18:25:30 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:25:30 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:25:30 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:25:37 red-queen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Feb 11 18:25:46 red-queen dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Feb 11 18:25:58 red-queen dhclient: No DHCPOFFERS received.
Feb 11 18:25:58 red-queen dhclient: No working leases in persistent database - sleeping.
Feb 11 18:26:00 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:26:00 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:26:00 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Feb 11 18:26:30 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: io/hpmud/musb.c 1057: unable to open hp:/usb/HP_Color_LaserJet_4650?serial=00000D922X6D 
Feb 11 18:26:30 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Feb 11 18:26:30 red-queen HP_Color_LaserJet_4650?serial=00000D922X6D: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds...

---

