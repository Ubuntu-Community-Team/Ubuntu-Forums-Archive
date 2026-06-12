---
title: "Sync of Palm T2 to Evolution on edgy hangs"
date: 2006-12-22
forum: General Help
---

### Post by ruscsoekm on 2006-12-22
Hi

I am trying to sync a Palm T2 to Evolution running on 6.10 with all updates installed. gpilotd (I assume) successfully creates the /dev/pilot device and the sync has completed a couple of times. Almost always though, it appears to hang.

I have tried using /dev/ttyUSB0 and /dev/ttyUSB1 rather than /dev/pilot (as described at [http://ubuntuforums.org/showthread.php?t=77387&highlight=palm+evolution](http://ubuntuforums.org/showthread.php?t=77387&highlight=palm+evolution) ) but this made no difference.

$ ps -ef|grep pilot
ruscoekm 14597     1  0 12:36 ?        00:00:00 /usr/bin/gpilot-applet --oaf-activate-iid=OAFIID:GNOME_PilotApplet_Factory --oaf-ior-fd=35
ruscoekm 14694     1  0 12:36 ?        00:00:00 /usr/bin/gpilotd --oaf-activate-iid=OAFIID:GNOME_Pilot_Daemon --oaf-ior-fd=31
ruscoekm 14751 14404  0 12:37 pts/0    00:00:00 grep pilot

$ gpilotd --version
gpilotd-Message: gnome-pilot 2.0.14 starting...
gpilotd-Message: compiled for pilot-link version 0.12.1
gpilotd-Message: compiled with [VFS] [USB] [IrDA] [Network] 
Gnome gnome-pilot 2.0.14

$ ls -l /dev/ttyUSB* /dev/pilot
zsh: no matches found: /dev/ttyUSB*

### Press Hotsync button ###

$ ls -l /dev/ttyUSB* /dev/pilot
lrwxrwxrwx 1 root root         7 Dec 23 12:40 /dev/pilot -> ttyUSB1
crw-rw---- 1 root dialout 188, 0 Dec 23 12:40 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 Dec 23 12:40 /dev/ttyUSB1

gnome-pilot Settings dialog appears (I hit close).
gnome-pilot Settings dialog appears (I hit close again).

Sync times out on handheld.

Output from /var/log/messages:

================================================
Dec 23 12:40:17 laptop kernel: [17180012.240000] usb 5-2.3: new full speed USB device using ehci_hcd and address 7
Dec 23 12:40:17 laptop kernel: [17180012.332000] usb 5-2.3: configuration #1 chosen from 1 choice
Dec 23 12:40:17 laptop kernel: [17180012.560000] usbcore: registered new driver usbserial
Dec 23 12:40:17 laptop kernel: [17180012.564000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Dec 23 12:40:17 laptop kernel: [17180012.564000] usbcore: registered new driver usbserial_generic
Dec 23 12:40:17 laptop kernel: [17180012.564000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
Dec 23 12:40:17 laptop kernel: [17180012.572000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Handspring Visor / Palm OS
Dec 23 12:40:17 laptop kernel: [17180012.572000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 3.5
Dec 23 12:40:17 laptop kernel: [17180012.572000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 5.0
Dec 23 12:40:17 laptop kernel: [17180012.576000] visor 5-2.3:1.0: Handspring Visor / Palm OS converter detected
Dec 23 12:40:17 laptop kernel: [17180012.580000] usb 5-2.3: Handspring Visor / Palm OS converter now attached to ttyUSB0
Dec 23 12:40:17 laptop kernel: [17180012.580000] usb 5-2.3: Handspring Visor / Palm OS converter now attached to ttyUSB1
Dec 23 12:40:17 laptop kernel: [17180012.580000] usbcore: registered new driver visor
Dec 23 12:40:17 laptop kernel: [17180012.580000] drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
Dec 23 12:40:40 laptop kernel: [17180034.820000] usb 5-2.3: USB disconnect, address 7
Dec 23 12:40:40 laptop kernel: [17180034.820000] visor 5-2.3:1.0: device disconnected
Dec 23 12:40:40 laptop kernel: [17180034.824000] visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
Dec 23 12:40:40 laptop kernel: [17180034.824000] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1
================================================

Regards
Kevin

---

