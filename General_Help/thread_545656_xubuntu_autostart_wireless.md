---
title: "xubuntu autostart wireless"
date: 2007-09-07
forum: General Help
---

### Post by nonewmsgs on 2007-09-07
i installed xfce and it is rocking but my wireless doesn't autostart like it does with gnome.  gnome starts with the keyring manager and then i type in that password and my wep key is used to log me in.

---

### Post by nonewmsgs on 2007-09-07
do i have to do this every time?

root@william-laptop-hp900:/home/william# modprobe ath_pciroot@william-laptop-hp900:/home/william# modprobe wlan_scan_sta
root@william-laptop-hp900:/home/william# iwlist ath0 scan
root@william-laptop-hp900:/home/william# iwconfig ath0 key xxxxxxx
root@william-laptop-hp900:/home/william# iwconfig ath0 essid "NITD6"

root@william-laptop-hp900:/home/william# iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:0F:B3:A3:9C:B2
                    ESSID:"NITD6"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=32/94  Signal level=-63 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200

root@william-laptop-hp900:/home/william# dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:14:6c:14:3d:96
Sending on   LPF/ath0/00:14:6c:14:3d:96
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6

root@william-laptop-hp900:/home/william# iwpriv ath0 authmode 1
root@william-laptop-hp900:/home/william# dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:14:6c:14:3d:96
Sending on   LPF/ath0/00:14:6c:14:3d:96
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.1.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.70 -- renewal in 39718 seconds.

---

### Post by dakuran on 2007-09-09
I'm havin the same problems as you buddy, I have KDE,Gnome, and Xfce installed I really dig Xfc, but like you my wireless doesn't autostart =[

---

### Post by nonewmsgs on 2007-09-09
i'd be ok if someone could tell me where to put in the batch script for it and then we'll be straight.

---

