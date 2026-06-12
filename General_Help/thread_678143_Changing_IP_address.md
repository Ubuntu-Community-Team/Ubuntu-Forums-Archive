---
title: "Changing IP address"
date: 2008-01-25
forum: General Help
---

### Post by cowinacan on 2008-01-25
Does anyone know how to change the IP adress in Gutsy Gibbon?  I'm just trying to find a way to not have to wait forever on rapidshare between downloads.

---

### Post by HermanAB on 2008-01-25
$ sudo ifconfig eth0 192.168.1.10 netmask 255.255.255.0 up

Cheers,

Herman

---

### Post by stchman on 2008-01-25
> **cowinacan said:**
> Does anyone know how to change the IP adress in Gutsy Gibbon?  I'm just trying to find a way to not have to wait forever on rapidshare between downloads.

You can to to Administration--->Networking.  Select the adapter and change from DHCP to static IP.  Fill in the appropriate fields.

---

