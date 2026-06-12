---
title: "Read/Write Access in Recovery Mode With WPA2 Wireless."
date: 2013-07-31
forum: General Help
---

### Post by maciimacii on 2013-07-31
I was installing something and it took out xorg on my system and I could not boot into X.

So I tried to work out how to reinstall xorg from recovery mode with read/write access and wireless.

My USB Wireless needed a WPA2 password which means that wpa_supplicant had to be used instead of iwconfig which is for WEP.

Here is what worked for Ubuntu 12.04.


------------------------------------------------------


1: Choose recovery mode (menu or by holding shift key)


2: Drop to a root shell prompt (read only)


3: Remount to read and write

mount --options remount,rw /
mount --all


4: Add dns server just to be safe that dns will work

The entries in /etc/network/interfaces seem to get automatically copied to /etc/resolv.conf and it overwrites any /etc/resolve.conf edits so editing resolv.conf and adding dns nameservers is useless, so /etc/network/interfaces is the file to add dns nameservers to [http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

pico /etc/network/interfaces

add

dns-nameservers 8.8.8.8

(8.8.8.8 is the Google dns server)


5: Reboot and get into a root shell again with read/write access ie

Choose recovery mode (menu or by holding shift key)

Drop to a root shell prompt (read only)

Remount to read and write

mount --options remount,rw /
mount --all


6: Stop networking

service network-manager stop


7: Setup wireless connection and scan

ifconfig wlan0 up 

iwlist wlan0 scan


8: Create wpa configuration file and connect

wpa_passphrase NETWORK_ID WIRELESS_KEY > /home/(username)/wpa.conf

wpa_supplicant -B -i wlan0 -c /home/(username)/wpa.conf

(ignore any IOCSIWENCODEEXT and SIOCSIWGENIE errors)

dhclient wlan0


9: now you should be online and can do whatever updates or installs that are needed.

For WEP use

ifconfig wlan0 up

iwlist wlan0 scan

iwconfig wlan0 essid NETWORK_ID key FEFEFEFEFE

Where FEFEFEFEFE is the WEP key in hexadecimal

or

iwconfig wlan0 essid NETWORK_ID key s:WIRELESS_KEY

dhclient wlan0

---

