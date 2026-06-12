---
title: "WPASupplicant Config File help"
date: 2005-10-20
forum: General Help
---

### Post by Trinitrogen Oxide on 2005-10-20
Im trying to setup a config file so I can properly use WPASupplicant to get on my Purdue's wireless network([http://www.itap.purdue.edu/airlink/setup/winxp.cfm](http://www.itap.purdue.edu/airlink/setup/winxp.cfm)) and Im trying to work out the proper config file. If your too lazy to read the link, I need

WPA network authenication
TKIP data encryption
Protected EAP
And it needs to use THawte Premium Server CA to validate the certificate

Heres what I have so far
```

network={
             ssid="PAL 2.0"
             scan_ssid=1
             key_mgmt=WPA-EAP
             eap=PEAP
             identity="foo"
             password="bar"

```

Am I right so far? And what do I do about the Certificate? Thanks

---

