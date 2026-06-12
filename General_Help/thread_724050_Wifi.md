---
title: "Wifi"
date: 2008-03-14
forum: General Help
---

### Post by nettles on 2008-03-14
I have an Acer Ferrari 4000 laptop. When I first got Ubuntu I got wifi to work within seconds, using the broadcom 43xx driver. All worked well until we the other day got a new router. Apparently we've now switched from a 8mb/s connection to a 24mb/s one, and wifi has stopped working. I really don't understand anything. Any idea of what might have happened (and perhaps how to solve it)?

Thanks a bunch :)

---

### Post by HereInOz on 2008-03-14
It is possible that the old router was either unsecured or using WEP encryption, and the new one has been set up by default to WPA-PSK, and it is possible that either your connection has not been updated or the driver does not support WPA-PSK.

First up, go into your router using a cable connection and disable all wireless security, and see if you can connect.  If you can, then it is clearly a security issue, and you can start playing around with the security until you sort out what will work, and what won't.

---

