---
title: "WLAN disconnect automatically"
date: 2020-03-04
forum: General Help
---

### Post by marcosch on 2020-03-04
Hi all

I've a very big problem.
My new ubuntu server is disconnecting automatically from the wifi.
I'm able to find the following at /etc/log/syslog (this repeats about 300 times in the log):

[FONT=courier new]Mar  4 15:11:37 cloudcube wpa_supplicant[4812]: wlan0: Associated with 2c:3a:fd:02:98:d5
Mar  4 15:11:37 cloudcube wpa_supplicant[4812]: wlan0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
Mar  4 15:11:37 cloudcube NetworkManager[4816]: <info>  [1583331097.7627] device (wlan0): supplicant interface state: associating -> 4-way handshake
Mar  4 15:11:37 cloudcube wpa_supplicant[4812]: wlan0: WPA: Key negotiation completed with 2c:3a:fd:02:98:d5 [PTK=CCMP GTK=CCMP]
Mar  4 15:11:37 cloudcube wpa_supplicant[4812]: wlan0: CTRL-EVENT-CONNECTED - Connection to 2c:3a:fd:02:98:d5 completed [id=0 id_str=]
Mar  4 15:11:37 cloudcube wpa_supplicant[4812]: wlan0: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=-17 noise=9999 txrate=6000
Mar  4 15:11:37 cloudcube NetworkManager[4816]: <info>  [1583331097.7800] device (wlan0): supplicant interface state: 4-way handshake -> completed
Mar  4 15:11:37 cloudcube wpa_supplicant[4812]: wlan0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-17 noise=9999 txrate=6000
Mar  4 15:11:37 cloudcube kernel: [13722.566584] wlan0: Limiting TX power to 20 (23 - 3) dBm as advertised by 2c:3a:fd:02:98:d5
Mar  4 15:11:50 cloudcube wpa_supplicant[4812]: wlan0: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=0 noise=9999 txrate=0
**Mar  4 15:11:50 cloudcube wpa_supplicant[4812]: wlan0: CTRL-EVENT-DISCONNECTED bssid=2c:3a:fd:02:98:d5 reason=4 locally_generated=1**
Mar  4 15:11:50 cloudcube NetworkManager[4816]: <warn>  [1583331110.6014] sup-iface[0x5580fcc190,wlan0]: connection disconnected (reason -4)
Mar  4 15:11:50 cloudcube NetworkManager[4816]: <info>  [1583331110.6069] device (wlan0): supplicant interface state: completed -> disconnected
Mar  4 15:11:50 cloudcube wpa_supplicant[4812]: wlan0: Reject scan trigger since one is already pending
Mar  4 15:11:50 cloudcube wpa_supplicant[4812]: wlan0: Failed to initiate AP scan
Mar  4 15:11:51 cloudcube wpa_supplicant[4812]: wlan0: Reject scan trigger since one is already pending
Mar  4 15:11:51 cloudcube wpa_supplicant[4812]: wlan0: Failed to initiate AP scan
Mar  4 15:11:52 cloudcube wpa_supplicant[4812]: wlan0: Reject scan trigger since one is already pending
Mar  4 15:11:52 cloudcube wpa_supplicant[4812]: wlan0: Failed to initiate AP scan
Mar  4 15:11:53 cloudcube wpa_supplicant[4812]: wlan0: SME: Trying to authenticate with 2c:3a:fd:02:98:d5 (SSID='schmuckis' freq=5300 MHz)
Mar  4 15:11:53 cloudcube kernel: [13738.218229] wlan0: authenticate with 2c:3a:fd:02:98:d5
Mar  4 15:11:53 cloudcube kernel: [13738.232165] wlan0: send auth to 2c:3a:fd:02:98:d5 (try 1/3)
Mar  4 15:11:53 cloudcube NetworkManager[4816]: <info>  [1583331113.4813] device (wlan0): supplicant interface state: disconnected -> authenticating
Mar  4 15:11:53 cloudcube kernel: [13738.336851] wlan0: send auth to 2c:3a:fd:02:98:d5 (try 2/3)
Mar  4 15:11:53 cloudcube kernel: [13738.340662] wlan0: authenticated
Mar  4 15:11:53 cloudcube wpa_supplicant[4812]: wlan0: Trying to associate with 2c:3a:fd:02:98:d5 (SSID='schmuckis' freq=5300 MHz)
Mar  4 15:11:53 cloudcube kernel: [13738.344900] wlan0: associate with 2c:3a:fd:02:98:d5 (try 1/3)
Mar  4 15:11:53 cloudcube kernel: [13738.348914] wlan0: RX AssocResp from 2c:3a:fd:02:98:d5 (capab=0x1511 status=0 aid=1)
Mar  4 15:11:53 cloudcube kernel: [13738.352841] wlan0: associated
Mar  4 15:11:53 cloudcube NetworkManager[4816]: <info>  [1583331113.5776] device (wlan0): supplicant interface state: authenticating -> associating
Mar  4 15:11:53 cloudcube wpa_supplicant[4812]: wlan0: Associated with 2c:3a:fd:02:98:d5
Mar  4 15:11:53 cloudcube wpa_supplicant[4812]: wlan0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
Mar  4 15:11:53 cloudcube NetworkManager[4816]: <info>  [1583331113.5875] device (wlan0): supplicant interface state: associating -> 4-way handshake
Mar  4 15:11:53 cloudcube wpa_supplicant[4812]: wlan0: WPA: Key negotiation completed with 2c:3a:fd:02:98:d5 [PTK=CCMP GTK=CCMP]
Mar  4 15:11:53 cloudcube wpa_supplicant[4812]: wlan0: CTRL-EVENT-CONNECTED - Connection to 2c:3a:fd:02:98:d5 completed [id=0 id_str=]
Mar  4 15:11:53 cloudcube wpa_supplicant[4812]: wlan0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-17 noise=9999 txrate=6000
Mar  4 15:11:53 cloudcube NetworkManager[4816]: <info>  [1583331113.6044] device (wlan0): supplicant interface state: 4-way handshake -> completed
Mar  4 15:11:53 cloudcube kernel: [13738.438886] wlan0: Limiting TX power to 20 (23 - 3) dBm as advertised by 2c:3a:fd:02:98:d5
Mar  4 15:11:53 cloudcube wpa_supplicant[4812]: wlan0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-17 noise=9999 txrate=6000
**Mar  4 15:12:06 cloudcube wpa_supplicant[4812]: wlan0: CTRL-EVENT-DISCONNECTED bssid=2c:3a:fd:02:98:d5 reason=4 locally_generated=1**[/FONT]


Does anybody know how to fix it?

Many thanks & best regards.


PS: I've the following version:

[FONT=courier new]# sudo lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:       Ubuntu 18.04.4 LTS
Release:           18.04
Codename:          bionic[/FONT]

---

