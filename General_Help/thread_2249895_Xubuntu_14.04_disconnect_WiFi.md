---
title: "Xubuntu 14.04 disconnect WiFi"
date: 2014-10-25
forum: General Help
---

### Post by 2xenobii on 2014-10-25
Hi I have a problem with disengaging the Wifi on my Xubuntu 14.04.Wi-Fi after switching on computer is working but after about 5 minutes disconnects.The network card is a TP-LINK TL-WN321G on Windows everything running on the RT2870 driver
lshw -C network
```
sudo lshw -C network
[sudo] password for kaczka2: 
  *-network               
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4.2
       logical name: wlan0
       serial: d8:5d:4c:99:ff:a7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.13.0-37-generic firmware=0.29 ip=192.168.0.2 link=yes multicast=yes wireless=IEEE 802.11bg
```
dmesg | egrep -i 'rt2'
```
dmesg | egrep -i 'rt2'
[   16.467404] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[   16.495530] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0006 detected
[   16.505132] usbcore: registered new interface driver rt2800usb
[   18.943054] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   18.980365] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   22.163222] rt2800usb 1-4.2:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   22.872175] rt2800usb 1-4.2:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1166.321111] rt2800usb 1-4.2:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1529.159335] rt2800usb 1-4.2:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1570.303506] rt2800usb 1-4.2:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1601.088119] rt2800usb 1-4.2:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
```
dmesg | egrep -i 'firmware'
```
dmesg | egrep -i 'firmware'
[    0.102316] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-1f] only partially covers this bridge
[   18.943054] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   18.980365] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29

```

---

