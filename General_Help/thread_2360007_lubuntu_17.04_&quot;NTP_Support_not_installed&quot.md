---
title: "lubuntu 17.04 &quot;NTP Support not installed&quot;"
date: 2017-04-30
forum: General Help
---

### Post by alan-v-hennessy on 2017-04-30
Lubuntu 17.04 on an old Core2 Sony Vaio cant sync to an internet time server. Attempting to select that option gets a "NTP Support not installed" message with an install option. Clicking the install option gets a "Could not install" with "GDBus.error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.PackageKit was not provided by any .service files".

Going to 'Software' and searching for NTP finds a "ntp server snap app" Trying to install it first requires a UbuntuOne account and the fails saying "GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name io.snapdLoginService was not  provided by any .service files"

So... How do I get Lubuntu 17.04 to sync with an internet time server? Also, how do I get it off a 24 hour clock to a 12 hour am/pm clock?

Thanks

---

### Post by Xian on 2017-05-01
The software package you want is ntp:

```
sudo apt-get install ntp
```

This has some good/basic info:

[https://help.ubuntu.com/lts/serverguide/NTP.html](https://help.ubuntu.com/lts/serverguide/NTP.html)

---

