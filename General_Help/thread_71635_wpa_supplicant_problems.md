---
title: "wpa_supplicant problems"
date: 2005-10-03
forum: General Help
---

### Post by CubanCorona on 2005-10-03
I just installed wpa_supplicant so that I can connect to a WEP EAP-TLS network.  However, when I run wpa_supplicant I get the following errors:

> wpa_supplicant -w -i eth1 -d
Initializing interface 'eth1' conf '(null)' driver 'default'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Priority group 200
   id=0 ssid='willow'
Priority group 100
   id=1 ssid='cavalier'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Own MAC address: 00:02:2d:45:9b:ba
wpa_driver_hostap_set_wpa: enabled=1
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_countermeasures: enabled=0
wpa_driver_hostap_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Starting AP scan (broadcast SSID)
ioctl[SIOCSIWSCAN{,EXT}]: Operation not supported
Failed to initiate AP scan.
Setting scan request: 10 sec 0 usec
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Operation not supported
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
ioctl[SIOCSIWSCAN{,EXT}]: Operation not supported
Failed to initiate AP scan.
Setting scan request: 10 sec 0 usec
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Operation not supported
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
ioctl[SIOCSIWSCAN{,EXT}]: Operation not supported
Failed to initiate AP scan.
Setting scan request: 10 sec 0 usec
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Operation not supported
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
ioctl[SIOCSIWSCAN{,EXT}]: Operation not supported
Failed to initiate AP scan.
Setting scan request: 10 sec 0 usec
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Operation not supported
Scan results: -1
Failed to get scan results
Failed to get scan results - try scanning again


I'm not sure what the problem is, but it doesn't seem like wpa_supplicant is communicating with the hardware at all.  

My wireless works fine without wpa_supplicant, but I need the EAP-TLS functionality.  

Any ideas?

---

### Post by CubanCorona on 2005-10-04
bump

---

### Post by CubanCorona on 2005-10-11
I still haven't been able to resolve this problem!  Help!

---

### Post by firecat53 on 2005-10-11
Try running it as root:

sudo wpa_supplicant .....

Typically (in my limited experience :) ) all the networking commands have to be run as root: ifconfig, iwconfig, wpa_supplicant, iwlist, etc.

Good luck! 

Scott

---

