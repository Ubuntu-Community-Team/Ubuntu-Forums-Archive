---
title: "[wpa_supplicant] Unsupported driver 'bcmwl5'"
date: 2005-10-30
forum: General Help
---

### Post by yellowbm on 2005-10-30
Hi, I have some difficulties setting up a connection with my accesspoint through WPA.

I'm running Breezy on my laptop, which is a Dell Inspiron 8500. The wlan is Dell's Truemobile 1300b/g. With ndiswrapper and the windows driver 'bcmwl5' the wireless card works perfectly. But I want to keep the WPA (TKIP) security on my accesspoint. 
That's why I tried the WPAHowto wiki. The problem is the following message:

```

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'bcmwl5'
Unsupported driver 'bcmwl5'.
```

which occurs when I run this command:
```
sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -D bcmwl5 -w -dd
```

The wpa_supplicant.conf looks like this:
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        ssid="onair"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
psk="wpa-passphrase"
}
```


The following shows that the wireless driver is loaded succesfully (I think)
```

dmesg | grep bcmwl5 
[4294697.182000] ndiswrapper: driver bcmwl5 (Broadcom,05/26/2005, 3.120.27.0) loaded
[4294697.881000] wlan0: ndiswrapper ethernet device 00:90:7b:9c:2a:5b using driver bcmwl5, configuration file 14E4:4320.5.conf
```

Is there someone with the same Truemobile wlan and drivers who has WPA running succesfully? 

Hopefully someone can help me setting up the WPA connection succesfully? :)

---

### Post by firecat53 on 2005-10-30
Change```
 sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -D bcmwl5 -w -dd
``` to```
 sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -D ndiswrapper -w -dd
``` 

Good luck!
Scott

---

### Post by yellowbm on 2005-10-31
firecat53 thanks! when I read it, I thought WHY didn't I think of it myself :p 

but, now I am one step further but I also have a new 'problem'. Hopefully you or someone else can help me with that. While trying to connect to my accesspoint I now receive:

```

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=2
fast_reauth=1
Line: 15 - start of a new network block
ssid - hexdump_ascii(len=5):
     6f 6e 61 69 72                                    onair
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
pairwise: 0x18
group: 0x1e
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='onair'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: No such device
SIOCGIWRANGE: too old (short) data - assuming WPA is not supported
Own MAC address: 00:90:4b:2c:8a:4b
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b2a len=12
Wireless event: cmd=0x8b2a len=12
Wireless event: cmd=0x8b2a len=12
Wireless event: cmd=0x8b2a len=12
State: DISCONNECTED -> SCANNING
Trying to associate with SSID 'onair'
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: Failed to parse WPA IE from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 30 pairwise 24 key_mgmt 2
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
No keys have been configured - skip key clearing
State: SCANNING -> ASSOCIATING
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
State: ASSOCIATING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0

```

In my eyes it looks like the authentication is going wrong somewhere....

---

### Post by firecat53 on 2005-11-03
Try removing all the extraneous stuff from wpa_supplicant.conf

Mine looks like:

network={
  ssid="network"
  psk=asd;flkadsfkljagjhadfg8903245987345
  key_mgmt=WPA-PSK
  proto=WPA
}

I tried all that stuff too, but for a simple home network WPA-PSK, that seems to be all you need!  Also, make sure that your /etc/default/wpasupplicant has the ENABLED=1 setting.

Good luck!

Scott

---

