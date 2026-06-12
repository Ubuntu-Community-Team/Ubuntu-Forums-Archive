---
title: "error message eating up all my memory in /var/log"
date: 2014-06-14
forum: General Help
---

### Post by adam64 on 2014-06-14
I keep getting this error from file  "syslog" in /var/log which is 18 gb and counting, I also have a "syslog.1" that is 11 gb with the  same text in it (this is just a sample):

Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: dbus_g_proxy_cancel_call: assertion 'pending != NULL' failed
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <info> (wlan0): supplicant interface state: starting -> down
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <warn> Trying to remove a non-existant call id.
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: nl80211: Driver  does not support authentication/association or connect commands
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: Could not set interface wlan0 flags (UP): Cannot assign requested address
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: WEXT: Could not set interface 'wlan0' UP
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: wlan0: Failed to initialize driver interface
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <error>  [1402608755.122976] [nm-supplicant-interface.c:997] interface_add_cb():  (wlan0): error adding interface: wpa_supplicant couldn't grab this  interface.
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: dbus_g_proxy_cancel_call: assertion 'pending != NULL' failed
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <info> (wlan0): supplicant interface state: starting -> down
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <warn> Trying to remove a non-existant call id.
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: nl80211: Driver  does not support authentication/association or connect commands
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: Could not set interface wlan0 flags (UP): Cannot assign requested address
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: WEXT: Could not set interface 'wlan0' UP
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: wlan0: Failed to initialize driver interface
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <error>  [1402608755.123542] [nm-supplicant-interface.c:997] interface_add_cb():  (wlan0): error adding interface: wpa_supplicant couldn't grab this  interface.
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: dbus_g_proxy_cancel_call: assertion 'pending != NULL' failed
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <info> (wlan0): supplicant interface state: starting -> down
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <warn> Trying to remove a non-existant call id.
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: nl80211: Driver  does not support authentication/association or connect commands
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: Could not set interface wlan0 flags (UP): Cannot assign requested address
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: WEXT: Could not set interface 'wlan0' UP
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: wlan0: Failed to initialize driver interface
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <error>  [1402608755.124093] [nm-supplicant-interface.c:997] interface_add_cb():  (wlan0): error adding interface: wpa_supplicant couldn't grab this  interface.

How would I fix this error message?  Please be specific, I'm a noob.

---

### Post by deadflowr on 2014-06-14
duplicate thread
[http://ubuntuforums.org/showthread.php?t=2229560](http://ubuntuforums.org/showthread.php?t=2229560)
Closed

---

