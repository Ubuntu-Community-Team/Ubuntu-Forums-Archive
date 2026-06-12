---
title: "System Freezing"
date: 2016-01-20
forum: General Help
---

### Post by Mel_Blakey on 2016-01-20
Ubuntu 14.04.3 - 64bit (up to date)
RAM: 4GB
Device:    HP Compaq Presario CQ57 - Laptop
Processor: Intel Pentium CPU B960 @ 2.2GHz x 2
Graphics:  Intel Sandybridge Mobile

I have been running Ubuntu 14.04 on this machine since its release alonside Windows 7 without any major problems (only WiFi related issues).
Late last year I installed Xampp and wasn't happy with it, so decided that as I had lots of other clutter I would do a fresh install of Ubuntu. I backed up the Home directory with RSync.

The machine has worked well since, for the last 3 weeks up until yesterday when it started freezing if I left it idle for up to 3 minutes. The keypad locked, the mouse would move but nothing is clickable.

At first I suspected Firefox and am now running it without and addons, but the system still freezes when using other apps, LibreOffice for example.

I have not installed any new apps in the last 10 days, so I can't really point the finger at anything that has caused this. The machine was running hot though so I've cleaned it out and the fan is not running wild now but its still freezing.

Iv'e done several searches but not found a solution.
One piece of info that was asked for in the other posts that I've read is:
```
 /var/log/syslog
Jan 20 10:31:45 Presario-CQ57 kernel: [   26.986927] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff88014b0aecf8), AE_AML_BUFFER_LIMIT (20141107/psparse-536)
Jan 20 10:31:47 Presario-CQ57 ntpdate[1240]: adjust time server 91.189.89.199 offset 0.364887 sec
Jan 20 10:31:57 Presario-CQ57 NetworkManager[689]: <info> (wlan0): IP6 addrconf timed out or failed.
Jan 20 10:31:57 Presario-CQ57 NetworkManager[689]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jan 20 10:31:57 Presario-CQ57 NetworkManager[689]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jan 20 10:31:57 Presario-CQ57 NetworkManager[689]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jan 20 10:31:59 Presario-CQ57 wpa_supplicant[721]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 20 10:41:20 Presario-CQ57 dbus[579]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Jan 20 10:41:20 Presario-CQ57 kernel: [  601.472124] systemd-hostnamed[2104]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Jan 20 10:41:20 Presario-CQ57 dbus[579]: [system] Successfully activated service 'org.freedesktop.hostname1'
```

I hope this helps someone to help me fix this.

Please note that I am not a Linux expert by any means!

Thanks

---

### Post by Mel_Blakey on 2016-01-20
I had a Logitech Wireless Mouse USB Dongle plugged in.

I unplugged it and my system has returned to normal!

Thanks for your interest.

---

