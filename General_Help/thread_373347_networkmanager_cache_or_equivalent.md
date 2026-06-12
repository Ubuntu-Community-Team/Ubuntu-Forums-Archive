---
title: "networkmanager cache or equivalent?"
date: 2007-03-01
forum: General Help
---

### Post by harty83 on 2007-03-01
Does networkmanager cache its network settings somewhere?

My college has some routers that have WPA (I do not know the password) and some that do not and they are all named NRCC.  The problem comes when I go to connect one without WPA.  iwlist scan does not indicate WPA at all and I can connect via ifup, but networkmanager usually refuses to allow me to connect because it thinks it has WPA security enabled.  If I try to connect to another network and enter NRCC without security a zillion times, sometimes networkmanager will then allow me to connect.

So I wonder, does networkmanager cache network settings that I could clear to solve this problem?  It's a pain having to change /etc/network/interfaces every time I want to connect to this one network.

Thanks
Alan

---

### Post by yopnono on 2007-03-01
Cache? don't known anything about that, however the settings are stored in the .gconf/system/networking/wireless/networks/ in you home folder.

Also have a look at this application.
[http://ubuntuforums.org/showthread.php?t=299462](http://ubuntuforums.org/showthread.php?t=299462)

---

### Post by harty83 on 2007-03-01
Wcid is perfect for what I need.  Works like a charm. 

Thanks!
Alan

---

