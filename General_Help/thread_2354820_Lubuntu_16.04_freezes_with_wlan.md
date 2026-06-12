---
title: "Lubuntu 16.04 freezes with wlan"
date: 2017-03-06
forum: General Help
---

### Post by majumder-pk on 2017-03-06
My desktop is on Lubuntu 16.04. It is freezing just after I enter login  details. While frozen, only caps lock and scroll lock are blinking  continuously. It seems working if I remove wlan adapter. I have checked  google and found [https://ubuntuforums.org/showthread.php?t=852225](https://ubuntuforums.org/showthread.php?t=852225). But I am confused  with the fixes. Can someone guide me for a proper fix and also how to do them step by step?

---

### Post by majumder-pk on 2017-03-06
In a second attempt I booted the system without the wlan adapter and then attached the wlan adapter and the saw what I have attached as an image.

---

### Post by majumder-pk on 2017-03-06
Here are some more logs...

I disabled network manager and attached the wlan adapter and got the following logs.

Mar  7 07:08:48 Phantom-D kernel: [  724.972024] usb 1-5: new high-speed USB device number 3 using ehci-pci
Mar  7 07:08:48 Phantom-D kernel: [  725.105467] usb 1-5: New USB device found, idVendor=7392, idProduct=7811
Mar  7 07:08:48 Phantom-D kernel: [  725.105474] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Mar  7 07:08:48 Phantom-D kernel: [  725.105479] usb 1-5: Product: 802.11n WLAN Adapter
Mar  7 07:08:48 Phantom-D kernel: [  725.105483] usb 1-5: Manufacturer: Realtek
Mar  7 07:08:48 Phantom-D kernel: [  725.105487] usb 1-5: SerialNumber: 00e04c000001
Mar  7 07:08:48 Phantom-D mtp-probe: checking bus 1, device 3: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5"
Mar  7 07:08:48 Phantom-D mtp-probe: bus: 1, device: 3 was not an MTP device
Mar  7 07:08:49 Phantom-D kernel: [  726.241474] cfg80211: World regulatory domain updated:
Mar  7 07:08:49 Phantom-D kernel: [  726.241479] cfg80211:  DFS Master region: unset
Mar  7 07:08:49 Phantom-D kernel: [  726.241480] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Mar  7 07:08:49 Phantom-D kernel: [  726.241483] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Mar  7 07:08:49 Phantom-D kernel: [  726.241485] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Mar  7 07:08:49 Phantom-D kernel: [  726.241487] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Mar  7 07:08:49 Phantom-D kernel: [  726.241489] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Mar  7 07:08:49 Phantom-D kernel: [  726.241492] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Mar  7 07:08:49 Phantom-D kernel: [  726.241494] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Mar  7 07:08:49 Phantom-D kernel: [  726.241496] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Mar  7 07:08:49 Phantom-D kernel: [  726.241497] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Mar  7 07:08:49 Phantom-D kernel: [  726.321469] rtl8192cu: Chip version 0x10
Mar  7 07:08:49 Phantom-D kernel: [  726.406721] rtl8192cu: MAC address: 74:da:38:1a:cd:43
Mar  7 07:08:49 Phantom-D kernel: [  726.406729] rtl8192cu: Board Type 0
Mar  7 07:08:49 Phantom-D kernel: [  726.406962] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
Mar  7 07:08:49 Phantom-D kernel: [  726.407016] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
Mar  7 07:08:50 Phantom-D kernel: [  726.419189] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
Mar  7 07:08:50 Phantom-D kernel: [  726.419521] usbcore: registered new interface driver rtl8192cu
Mar  7 07:08:50 Phantom-D NetworkManager[633]: <info>  [1488850730.0107] (wlan0): using nl80211 for WiFi device control
Mar  7 07:08:50 Phantom-D kernel: [  726.425991] usbcore: registered new interface driver rtl8xxxu
Mar  7 07:08:50 Phantom-D kernel: [  726.429926] rtl8192cu 1-5:1.0 wlx74da381acd43: renamed from wlan0
Mar  7 07:08:50 Phantom-D systemd[1]: Starting Load/Save RF Kill Switch Status...
Mar  7 07:08:50 Phantom-D systemd[1]: Started Load/Save RF Kill Switch Status.
Mar  7 07:08:50 Phantom-D NetworkManager[633]: <info>  [1488850730.0431] device (wlan0): driver supports Access Point (AP) mode
Mar  7 07:08:50 Phantom-D NetworkManager[633]: <info>  [1488850730.0446] manager: (wlan0): new 802.11 WiFi device (/org/freedesktop/NetworkManager/Devices/2)
Mar  7 07:08:50 Phantom-D NetworkManager[633]: <info>  [1488850730.0478] rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/ieee80211/phy0/rfkill0) (driver rtl8192cu)
Mar  7 07:08:50 Phantom-D NetworkManager[633]: <info>  [1488850730.0486] devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/net/wlx74da381acd43, iface: wlx74da381acd43)
Mar  7 07:08:50 Phantom-D NetworkManager[633]: <info>  [1488850730.0486] device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/net/wlx74da381acd43, iface: wlx74da381acd43): no ifupdown configuration found.
Mar  7 07:08:50 Phantom-D dbus[605]: [system] Activating via systemd: service name='fi.w1.wpa_supplicant1' unit='wpa_supplicant.service'
Mar  7 07:08:50 Phantom-D NetworkManager[633]: <info>  [1488850730.0516] device (wlan0): interface index 3 renamed iface from 'wlan0' to 'wlx74da381acd43'
Mar  7 07:08:50 Phantom-D systemd[1]: Starting WPA supplicant...
Mar  7 07:08:50 Phantom-D com.canonical.indicator.application[965]: (process:1113): indicator-application-service-WARNING **: Application already exists, re-requesting properties.
Mar  7 07:08:50 Phantom-D dbus[605]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Mar  7 07:08:50 Phantom-D wpa_supplicant[1229]: Successfully initialized wpa_supplicant
Mar  7 07:08:50 Phantom-D systemd[1]: Started WPA supplicant.
Mar  7 07:08:50 Phantom-D NetworkManager[633]: <info>  [1488850730.1619] supplicant: wpa_supplicant running
Mar  7 07:08:52 Phantom-D ModemManager[591]: <info>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5': not supported by any plugin
Mar  7 07:08:58 Phantom-D ntpd[810]: error resolving pool 0.ubuntu.pool.ntp.org: Temporary failure in name resolution (-3)


pradip@Phantom-D:~$ lsusb
Bus 001 Device 007: ID 0bda:0109 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by majumder-pk on 2017-03-07
I have removed the kernel 4.4.0-64 and reverted back to 4.4.0-62. My system is working fine with wifi again.

---

### Post by oldrocker99 on 2017-03-07
Great! Please mark your thread as [SOLVED] to help other users.

---

