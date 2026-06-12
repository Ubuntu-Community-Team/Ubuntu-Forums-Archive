---
title: "WEP Encryption with Netgear Router"
date: 2005-05-06
forum: General Help
---

### Post by thread on 2005-05-06
My Intel 2200 Wireless card has been working Well Enough for unencrypted, public networks for a few weeks now, but now I'm trying to get onto an encrypted network through our Netgear router.

I've tried the command line equivilent, but I'm sure the gui is accomplishing the same thing. I select the essid from the dropdown, and paste our 26 character wep key (that's been verified...) in. When I click okay, I get the little 'hold on...' dialog, and then it ends and eth0 is up, but with only some ipv6 ip address... not the proper ipv4 one it should have.

Doing the same thing at the command line,

```
# iwconfig eth0 essid Bell
# iwconfig eth0 key <26 character wep key>
# iwconfig eth0
```

The last line there shows me the essid and encryption key that I want to see, but as soon as I

```
# dhclient eth0
```

I never get any response from the server, and dhclient eventually tries some other ip, then pinging a router -- definitely going to fail as well. That's where I'm left with the ipv6 address in the ifconfig.

The router's web tool shows our configuration:
Region = USA
Channel = 5
Authentication Type = Share Key
Encryption Strength = 128 bit

... and then below that we use a passphrase to generate the 26 character wep keys.

Any suggestions on this one? Are there any other variables to take into consideration when getting on a network like this?

---

### Post by FX on 2005-05-07
Its pretty early for me. but wouldn't the card you would be looking at either be "ath0" or "wlan" and not eth0. eth0 is the wire or cat5 isn't it?

Probably didn't help much. Sorry. 

I actually would like to get WEP going on mine also. Been running wireless here for about a year without. lol

---

### Post by thread on 2005-05-07
Yeah. I've been using my wireless for unencrypted networks... so I know it works and that it's called eth0. My wired ethernet registers on eth1.

Here's my output from wpa_supplicant now...

```
$ wpa_supplicant -ieth0 -c /etc/wpa_supplicant.conf -d ndiswrapper -c /etc/wpa_supplicant.conf
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Initializing interface 'eth0' conf '/etc/wpa_supplicant.conf' driver 'default'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Priority group 0
   id=0 ssid='Bell'
Initializing interface (2) 'eth0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Own MAC address: 00:12:f0:01:aa:da
wpa_driver_hostap_set_wpa: enabled=1
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
Failed to set encryption.
wpa_driver_hostap_set_countermeasures: enabled=0
wpa_driver_hostap_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth0' added
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 180 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:09:5b:49:43:e3 ssid='Bell' wpa_ie_len=0 rsn_ie_len=0
   skip - no WPA/RSN IE
No suitable AP found.
Setting scan request: 5 sec 0 usec
Signal 2 received - terminating
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_hostap_set_wpa: enabled=0
wpa_driver_hostap_set_drop_unencrypted: enabled=0
wpa_driver_hostap_set_countermeasures: enabled=0
```

---

### Post by thread on 2005-05-08
Okay, well I still haven't learned much about wireless, but I did figure out that if I switched the Authentication Type in the router from shared to open key, I was able to get my dhcp ip with no problems. We're not even using wpa, so wpa_supplicant was entirely the wrong direction for me. I now post this message over thin air!  :razz:

Anyone care to speculate why the shared key method doesn't work for me at all?

---

