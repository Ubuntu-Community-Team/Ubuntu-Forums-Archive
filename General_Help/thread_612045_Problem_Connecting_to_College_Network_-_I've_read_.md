---
title: "Problem Connecting to College Network - I've read around but can't find anything"
date: 2007-11-13
forum: General Help
---

### Post by cl_audio on 2007-11-13
Hey!

I've read around but can't seem to find any literature to help me connect to my school wireless.

Here's what my college needs for the wireless:

Network Name (SSID): Students
Network Type: Infrastructure Mode (Access Point)
Network Authentication or Association Mode: WPA
Encryption Method: TKIP
**Enable IEEE 802.1x authentication: Yes**
EAP Type: Protected EAP (PEAP)
Authentication Method or Inner EAP Protocol: MS-CHAP Ver. 2
Machine Authentication or Authenticate as computer: No
Connect to networks that do not broadcast: Yes
Certificate based authentication: No
Login Name: You're User ID
Password: You're Password
Anonymous Name: Anonymous

In the new Netmanager I can do everything except ** Enable IEEE802.1x...**

I also can't seem to find the wpa-supplicant config file....


Any help would be really appreciated!!

Thanks

---

### Post by cl_audio on 2007-11-13
Bump... Please someone must have any tips...

---

### Post by knowledge_is_power on 2007-11-13
Theres an app by Open1X called Xsupplicant.  You should be able to find it in synaptic.  However, i always thought 802.1x was practaclly the same as WPA or WPA2 encryption.  I could be wrong however.
g/l with your problem.  post-secondary networks suck >.<  mine keeps booting me off and sending one of my cpus into an infinate loop. :(

---

### Post by cl_audio on 2007-11-13
Yea I'm not really sure, The option is there when I was running Windowz, anyways, thanks a lot for your help, I'll let you know how it goes!

---

### Post by cl_audio on 2007-11-13
I downloaded the Xsupplicant, but have no idea to go about using it... I''ll look it up, if any one has ideas feel free to share :)

---

### Post by cl_audio on 2007-11-13
bump.... Any help?

---

### Post by jharbert on 2007-11-14
If you are using Gusty then Network Manager should be installed by default and an icon for it should appear in the notification area on the panel.  Left click that icon, select Connect to Other Wireless Network.  Choose the following settings:
Network Name: Students
Wireless Security: WPA Enterprise
EAP Method: PEAP
Key Type: TKIP
Identity: You're User ID
Password: You're Password
Click Connect and everything should be fine.  My university uses a similar setup (Dynamic WEP instead of TKIP) and it works fine for me.

---

### Post by cl_audio on 2007-11-14
I have attempted that, I also attempted using MSCHAPv2,



Thanks for the advice though, I hope someone out there can help me!

---

