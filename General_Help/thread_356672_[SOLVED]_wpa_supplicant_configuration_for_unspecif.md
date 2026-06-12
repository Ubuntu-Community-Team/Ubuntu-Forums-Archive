---
title: "[SOLVED] wpa_supplicant configuration for unspecified ssids"
date: 2007-02-08
forum: General Help
---

### Post by rrwo on 2007-02-08
I have my wpa_supplicant.conf set up to with various SSIDs for home and work with appropriate settings.

But I don't know how to set it up so that when it encounters a new, unrecognised id for the first time, to assume no security and try to connect.  I have to kill wpa_supplicant (using sudo ifdown) and manually bring the interface back up and use dhclient without starting wpa_supplicant so as to connect.

---

### Post by sdide on 2007-02-09
Hey, 

from ```
/usr/share/doc/wpasupplicant/examples
```

```
$ more wpa_connect_open_ap.conf
```
```
# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf.gz for more
#  complete configuration parameters.
#
# Also see the other files in /usr/share/doc/wpasupplicant/examples/ for
#  specific configuration examples.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Example of basic WPA-PSK secured AP
#network={
#    ssid="ournet"
#    psk="w243sd5f324asdf5123sadf54324"
#}

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        ssid=""
        key_mgmt=NONE
}

```

---

