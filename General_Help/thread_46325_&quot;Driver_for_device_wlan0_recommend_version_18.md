---
title: "&quot;Driver for device wlan0 recommend version 18 of Wireless Extension, but...&quot;"
date: 2005-07-04
forum: General Help
---

### Post by traherom on 2005-07-04
I'm trying to setup my wireless card. (A broadcom chipset under ndiswrapper - the driver is reported as fine) When I do a iwconfig, I get:
> 
~$ iwconfig wlan0
[b]Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...[/b]

wlan0     IEEE 802.11g  ESSID: off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management min timeout:0us  mode:All packets received
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


What exactly does the warning mean/how can I fix it? Thanks in advance. :)

---

### Post by clarke.rainey on 2005-07-04
I too get this error and was wondering what it meant... I am not a big fan of getting errors...

---

