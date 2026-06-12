---
title: "[SOLVED] system crash"
date: 2008-01-02
forum: General Help
---

### Post by powderhound99 on 2008-01-02
So I'm running a core2 duo w/ gutsy. It's been about a month or too now where I've been having an issue where my system just powers off. There seems to be no link between any particular app. I usally have XMMS, Azurues, Firefox, and a terminal open at all times. I'm running compiz-fussion. The issue has gotten worse over the last couple of weeks. Lately I've been playing with CSS through Firefox files such as .mozillia/firefox/@#@.default/user.js an Firefox/#@@.default/chrome/userChr...... and etc. I have the syslog out-put and have received the same from each crash.



n  2 19:04:11 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:04:41 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:04:41 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:05:12 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:05:12 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:05:42 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:05:42 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:06:12 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:06:12 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:06:19 mc-escher dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jan  2 19:06:27 mc-escher dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Jan  2 19:06:37 mc-escher dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Jan  2 19:06:42 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:06:42 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:06:50 mc-escher dhclient: No DHCPOFFERS received.
Jan  2 19:06:50 mc-escher dhclient: No working leases in persistent database - sleeping.
Jan  2 19:07:12 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:07:12 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:07:42 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:07:42 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:08:12 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:08:12 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:08:42 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:08:42 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:09:12 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:09:12 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:09:42 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:09:42 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:10:12 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:10:12 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:10:42 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:10:42 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:11:13 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:11:13 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:11:43 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:11:43 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:12:13 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:12:13 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:12:43 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:12:43 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:13:13 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:13:13 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:13:38 mc-escher dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan  2 19:13:41 mc-escher dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jan  2 19:13:43 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:13:43 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:13:47 mc-escher dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jan  2 19:13:54 mc-escher dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Jan  2 19:14:04 mc-escher dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Jan  2 19:14:09 mc-escher dhclient: No DHCPOFFERS received.
Jan  2 19:14:09 mc-escher dhclient: No working leases in persistent database - sleeping.
Jan  2 19:14:13 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:14:13 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:14:43 mc-escher psc_1100_series?serial=MY389D14151U: io/hpmud/musb.c 1003: unable to open hp:/usb/psc_1100_series?serial=MY389D14151U 
Jan  2 19:14:43 mc-escher psc_1100_series?serial=MY389D14151U: INFO: open device failed; will retry in 30 seconds... 
Jan  2 19:21:47 mc-escher syslogd 1.4.1#21ubuntu3: restart.


can anyone tell me whats going on so i can fix it?

---

### Post by disturbed1 on 2008-01-02
The only thing your log shows is issues with an HP printer connected to a USB port. Unplug the printer.

For instant rebooting issues, these are common with memory errors, over-heating CPU, and power supply failure.

Run memtest to check your memory.

See your BIOS for CPU temps.

See your BIOS for power supply voltages (+12 should be close to +12V not +10V or +15V)

Could also be over/under volting your RAM/CPU through improper attempts at overclocking, cheap motherboard using underspec'd power rails.

---

### Post by powderhound99 on 2008-01-27
OK so it's been a long couple of weeks. I hadn't had the printer plugged in which was the problem there. I was never able to find any temp, fan, or voltage readouts in my bios. I installed lm-sensors and have found I'm running really hot. The next step seems to be to adjust my fan speed. Problem is I'm only getting a core temp read when I run sensors. Having the same issues on a fresh install. I don't even have my Nvidia driver enaled let alone compiz. Short of doing it blind (wont happen) what can I do? any suggestions?

:confused:

---

