---
title: "Using systemd (in Ubuntu Mate 16.04) to turn off Bluetooth at boot time"
date: 2017-06-07
forum: General Help
---

### Post by desconocido on 2017-06-07
I saw a lot of comments suggesting that amending /etc/rc.local to turn off Bluetooth at boot time wasn't a good idea because it was being phased out.

So I thought I would try setting something up in systemd.

I followed the instructions in
[https://linuxconfig.org/how-to-automatically-execute-shell-script-at-startup-boot-on-systemd-linux]("https://linuxconfig.org/how-to-automatically-execute-shell-script-at-startup-boot-on-systemd-linux")

I created the file
/etc/systemd/system/turn-bluetooth-off.service 
```
[Unit]
Description=Service to always turn bluetooth off at system start time
After=NetworkManager.service
Before=network-online.target

[Service]
ExecStart=/usr/local/bin/turn-bluetooth-off.sh

[Install]
WantedBy=default.target

```
and the file
/usr/local/bin/turn-bluetooth-off.sh
```
#!/bin/bash

date > /root/disk_space_report.txt
rfkill block bluetooth
du -sh /home/ >> /root/disk_space_report.txt
```

I gave these commands:
```
$ sudo chmod 744 /usr/local/bin/turn-bluetooth-off.sh
$ sudo chmod 664 /etc/systemd/system/turn-bluetooth-off.service 
$ systemctl daemon-reload
$ systemctl enable turn-bluetooth-off.service
Created symlink from /etc/systemd/system/default.target.wants/turn-bluetooth-off.service to /etc/systemd/system/turn-bluetooth-off.service.

```
I left the date and du actions in as a way of testing it works. Both date and du execute, so I guess the rfkill in between does too.

I had to guess the settings for After=, Before=, and WantedBy=
as I don't know the order in which all these services and targets should really occur.

Using the Bluetooth top panel applet icon as a proxy for the actual state of Bluetooth,
it appears as OFF, disappears, then it seems to nudge the Weather Report applet twice (without actually appearing), then it appears as ON then turns to OFF.
[ATTACH=CONFIG]275522[/ATTACH]

Later you can use this applet to turn Bluetooth on or off.

Would welcome advice on finetuning the timing of running the script in order to have Bluetooth on for the smallest possible time while the system boots.

---

### Post by cariboo on 2017-06-07
If you don't want bluetooth to start at all on boot use the following command:

```
sudo systemctl disable bluetooth.service
```

---

### Post by desconocido on 2017-06-08
> **cariboo said:**
> If you don't want bluetooth to start at all on boot

Thanks. For the moment I will try and leave available the option to turn it on when needed.

---

### Post by desconocido on 2017-06-21
By the way, it takes 25 seconds after login for the Bluetooth icon to finally fade to OFF.

I am hoping for something a bit quicker.
At least I see how they speeded up booting - looks like it doesn't finish until well after you have started using the computer.

---

### Post by desconocido on 2017-06-28
Here is a selection of entries (those that contained the word "blue") from the syslog when I reboot the system with my service turned OFF.
Items beginning === are my comments

```
[COLOR="#FF0000"]=== Bluetooth is set OFF via applet; System restart requested:[/COLOR]

Jun 28 21:13:50 Otilia systemd[1]: Stopped target Bluetooth.

Jun 28 21:13:51 Otilia bluetoothd[789]: Endpoint unregistered: sender=:1.48 path=/MediaEndpoint/A2DPSource
Jun 28 21:13:51 Otilia bluetoothd[789]: Endpoint unregistered: sender=:1.48 path=/MediaEndpoint/A2DPSink

[COLOR="#FF0000"]=== restart[/COLOR]

Jun 28 21:15:26 Otilia systemd[1]: Starting Bluetooth service...

Jun 28 21:15:26 Otilia systemd[1]: Started Service to always turn bluetooth off at system start time.
[COLOR="#FF0000"]=== (N.B. the rfkill block command in this service is currently commented out and the service before and after directives are also commented out)
[/COLOR]
Jun 28 21:15:26 Otilia bluetoothd[823]: Bluetooth daemon 5.37

Jun 28 21:15:26 Otilia systemd[1]: Started Bluetooth service.

Jun 28 21:15:26 Otilia bluetoothd[823]: Starting SDP server

Jun 28 21:15:26 Otilia kernel: [   12.982682] toshiba_bluetooth: Toshiba ACPI Bluetooth device driver

Jun 28 21:15:26 Otilia kernel: [   14.590384] Bluetooth: Core ver 2.21
Jun 28 21:15:26 Otilia kernel: [   14.590429] Bluetooth: HCI device and connection manager initialized
Jun 28 21:15:26 Otilia kernel: [   14.590439] Bluetooth: HCI socket layer initialized
Jun 28 21:15:26 Otilia kernel: [   14.590445] Bluetooth: L2CAP socket layer initialized
Jun 28 21:15:26 Otilia kernel: [   14.590459] Bluetooth: SCO socket layer initialized

Jun 28 21:15:26 Otilia kernel: [   25.224411] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun 28 21:15:26 Otilia kernel: [   25.224416] Bluetooth: BNEP filters: protocol multicast
Jun 28 21:15:26 Otilia kernel: [   25.224427] Bluetooth: BNEP socket layer initialized

Jun 28 21:15:26 Otilia bluetoothd[823]: Bluetooth management interface 1.13 initialized

Jun 28 21:15:27 Otilia bluetoothd[823]: Failed to obtain handles for "Service Changed" characteristic
Jun 28 21:15:27 Otilia bluetoothd[823]: Not enough free handles to register service
Jun 28 21:15:27 Otilia bluetoothd[823]: Error adding Link Loss service
Jun 28 21:15:27 Otilia bluetoothd[823]: Not enough free handles to register service
Jun 28 21:15:27 Otilia bluetoothd[823]: message repeated 2 times: [ Not enough free handles to register service]
Jun 28 21:15:27 Otilia bluetoothd[823]: Current Time Service could not be registered
Jun 28 21:15:27 Otilia bluetoothd[823]: gatt-time-server: Input/output error (5)
Jun 28 21:15:27 Otilia bluetoothd[823]: Not enough free handles to register service
Jun 28 21:15:27 Otilia bluetoothd[823]: Not enough free handles to register service
Jun 28 21:15:27 Otilia bluetoothd[823]: Sap driver initialization failed.
Jun 28 21:15:27 Otilia bluetoothd[823]: sap-server: Operation not permitted (1)

Jun 28 21:15:28 Otilia systemd[1]: Reached target Bluetooth.

Jun 28 21:15:29 Otilia NetworkManager[773]: <info>  [1498677329.2385] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so)

Jun 28 21:15:29 Otilia NetworkManager[773]: <info>  [1498677329.6318] bluez: use BlueZ version 5

Jun 28 21:15:53 Otilia bluetoothd[823]: Endpoint registered: sender=:1.47 path=/MediaEndpoint/A2DPSource
Jun 28 21:15:53 Otilia bluetoothd[823]: Endpoint registered: sender=:1.47 path=/MediaEndpoint/A2DPSink

Jun 28 21:15:53 Otilia kernel: [   52.496454] Bluetooth: RFCOMM TTY layer initialized
Jun 28 21:15:53 Otilia kernel: [   52.496476] Bluetooth: RFCOMM socket layer initialized
Jun 28 21:15:53 Otilia kernel: [   52.496496] Bluetooth: RFCOMM ver 1.11

Jun 28 21:16:00 Otilia dbus[761]: [system] Activating service name='org.blueman.Mechanism' (using servicehelper)
Jun 28 21:16:01 Otilia org.blueman.Mechanism[761]: Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Jun 28 21:16:01 Otilia org.blueman.Mechanism[761]: Unable to init server: Could not connect: Connection refused
Jun 28 21:16:01 Otilia org.blueman.Mechanism[761]: Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Jun 28 21:16:01 Otilia org.blueman.Mechanism[761]: Unable to init server: Could not connect: Connection refused
Jun 28 21:16:01 Otilia blueman-mechanism: Starting blueman-mechanism
Jun 28 21:16:01 Otilia dbus[761]: [system] Successfully activated service 'org.blueman.Mechanism'
Jun 28 21:16:01 Otilia org.blueman.Mechanism[761]: (blueman-mechanism:1885): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
Jun 28 21:16:01 Otilia blueman-mechanism: loading Network
Jun 28 21:16:01 Otilia blueman-mechanism: loading RfKill
Jun 28 21:16:01 Otilia blueman-mechanism: loading Ppp
Jun 28 21:16:01 Otilia blueman-mechanism: loading Rfcomm
Jun 28 21:16:02 Otilia systemd[1]: Starting Load/Save RF Kill Switch Status...
Jun 28 21:16:02 Otilia systemd[1]: Started Load/Save RF Kill Switch Status.

Jun 28 21:16:31 Otilia blueman-mechanism: Exiting

[COLOR="#FF0000"]=== At the end of this restart, Bluetooth applet shows ON and "rfkill list all" shows
[/COLOR]0: Toshiba Bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

---

### Post by VMC on 2017-06-28
What does blame show for bluetooth:
```
systemd-analyze blame
```

---

### Post by desconocido on 2017-06-28
> **VMC said:**
> What does blame show for bluetooth:
```
systemd-analyze blame
```
For the version where my service actually works, it's
```
470ms bluetooth.service
```

Nice software that I didn't know existed. systemd-analyze plot is amazing:
[ATTACH]275803[/ATTACH]

---

