---
title: "ModemManager segfault pls help"
date: 2016-05-21
forum: General Help
---

### Post by surgeongg on 2016-05-21
Latest Ubuntu version. Got this after installing Apache, MySQL and php yesterday and now I have no wireless. 

```
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.135358] usb 7-2: new SuperSpeed USB device number 3 using xhci_hcd
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.154895] usb 7-2: New USB device found, idVendor=0b05, idProduct=17eb
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.154904] usb 7-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.154909] usb 7-2: Product: 802.11ac WLAN
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.154912] usb 7-2: Manufacturer: MediaTek Inc.
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.154916] usb 7-2: SerialNumber: 000000000
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.156947] 
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.156947] === pAd = ffffc90001361000, size = 1292952 ===
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.156947] 
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.156957] driver version: 3.0.0.1 (May  7 2016 12:51:52) .
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.158417] ==>rlt_wlan_chip_onoff(): OnOff:1, Reset= 1, pAd->WlanFunCtrl:0x0, Reg-WlanFunCtrl=0x20a
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.185168] RtmpChipOpsEepromHook::e2p_type=0, inf_Type=2
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.185175] RtmpEepromGetDefault::e2p_dafault=1
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.185886] NVM is EFUSE mode
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.185890] Endpoint(8) is for In-band Command
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.185894] Endpoint(4) is for WMM0 AC0
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.185896] Endpoint(5) is for WMM0 AC1
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.185899] Endpoint(6) is for WMM0 AC2
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.185901] Endpoint(7) is for WMM0 AC3
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.185904] Endpoint(9) is for WMM1 AC0
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.185906] Endpoint(84) is for Data-In
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.185908] Endpoint(85) is for Command Rsp
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.186428] 80211> CurTxPower = 20 dBm
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.186433] ====> Radar Channel 52
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.186436] ====> Radar Channel 54
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.186438] ====> Radar Channel 56
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.186440] ====> Radar Channel 60
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.186442] ====> Radar Channel 62
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.186444] ====> Radar Channel 64
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.186446] ====> Radar Channel 100
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.186448] ====> Radar Channel 104
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.186451] 80211> TxStream = 0
May 21 21:12:28 jimmy-MS-7891 NetworkManager[944]: <info>  [1463857948.3143] (wlan0): using nl80211 for WiFi device control
May 21 21:12:28 jimmy-MS-7891 NetworkManager[944]: <info>  [1463857948.3144] device (wlan0): driver supports Access Point (AP) mode
May 21 21:12:28 jimmy-MS-7891 NetworkManager[944]: <info>  [1463857948.3159] manager: (wlan0): new 802.11 WiFi device (/org/freedesktop/NetworkManager/Devices/3)
May 21 21:12:28 jimmy-MS-7891 mtp-probe: checking bus 7, device 3: "/sys/devices/pci0000:00/0000:00:10.0/usb7/7-2"
May 21 21:12:28 jimmy-MS-7891 mtp-probe: bus: 7, device: 3 was not an MTP device
May 21 21:12:28 jimmy-MS-7891 NetworkManager[944]: <info>  [1463857948.3281] rfkill1: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:10.0/usb7/7-2/ieee80211/phy1/rfkill1) (driver usb)
May 21 21:12:28 jimmy-MS-7891 systemd-udevd[2976]: Process 'vlan-network-interface' failed with exit code 1.
May 21 21:12:28 jimmy-MS-7891 ifupdown-hotplug[2993]: Bad ifupdown udev helper invocation: $INTERFACE is not set
May 21 21:12:28 jimmy-MS-7891 systemd-udevd[2976]: Process 'ifupdown-hotplug' failed with exit code 1.
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.210949] show_signal_msg: 58 callbacks suppressed
May 21 21:12:28 jimmy-MS-7891 kernel: [ 1789.210954] ModemManager[1164]: segfault at 0 ip 0000000000431ab3 sp 00007ffd5885dfb0 error 4 in ModemManager[400000+103000]
May 21 21:12:28 jimmy-MS-7891 systemd[1]: ModemManager.service: Main process exited, code=dumped, status=11/SEGV
May 21 21:12:28 jimmy-MS-7891 NetworkManager[944]: <info>  [1463857948.5341] ModemManager disappeared from bus
May 21 21:12:28 jimmy-MS-7891 systemd[1]: ModemManager.service: Unit entered failed state.
May 21 21:12:28 jimmy-MS-7891 systemd[1]: ModemManager.service: Failed with result 'core-dump'.
May 21 21:12:28 jimmy-MS-7891 systemd[1]: ModemManager.service: Service hold-off time over, scheduling restart.
May 21 21:12:28 jimmy-MS-7891 systemd[1]: Stopped Modem Manager.
May 21 21:12:28 jimmy-MS-7891 systemd[1]: Starting Modem Manager...
May 21 21:12:28 jimmy-MS-7891 ModemManager[3000]: <info>  ModemManager (version 1.4.12) starting in system bus...
May 21 21:12:28 jimmy-MS-7891 systemd[1]: Started Modem Manager.
May 21 21:12:28 jimmy-MS-7891 NetworkManager[944]: <info>  [1463857948.8586] ModemManager disappeared from bus
May 21 21:12:28 jimmy-MS-7891 NetworkManager[944]: <info>  [1463857948.8789] ModemManager available in the bus
May 21 21:12:31 jimmy-MS-7891 ModemManager[3000]: <info>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:03.1/0000:02:00.0': not supported by any plugin
May 21 21:12:31 jimmy-MS-7891 ModemManager[3000]: <info>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:10.0/usb7/7-2': not supported by any plugin
May 21 21:12:35 jimmy-MS-7891 dbus[895]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
May 21 21:12:35 jimmy-MS-7891 systemd[1]: Starting Hostname Service...
May 21 21:12:35 jimmy-MS-7891 dbus[895]: [system] Successfully activated service 'org.freedesktop.hostname1'
May 21 21:12:35 jimmy-MS-7891 systemd[1]: Started Hostname Service.
```

---

### Post by surgeongg on 2016-05-21
I should point out that i'm not a 100 percent sure it's because of the lamp installation. Wireless worked fine yesterday but didn't work when i woke up today.

---

### Post by surgeongg on 2016-05-22
Turns out it had nothing to do with LAMP. Tested it with new installation and It broke the same way for some reason when I ran apt-get upgrade.

Fixed the problem and was able to get wifi again with:
sudo service network-manager restart

Gotta restart network-manager every time I restart the computer though, but it works.

---

### Post by unxed on 2017-05-01
Had the same issue.
Fixed it by blacklisting default wifi driver (rtl8192cu) and using rtl8xxxu instead.

btw, you can give a try to
[https://github.com/ulli-kroll/mt7612u](https://github.com/ulli-kroll/mt7612u)

---

