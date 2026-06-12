---
title: "RDP client with native TLS 1.2 and NLA support"
date: 2018-01-18
forum: General Help
---

### Post by 98cwitr on 2018-01-18
Tried Remmina, rdesktop, xfreerdp and none seem to allow me to connect. Our Windows servers force TLS and NLA. Any rdp client out there that will natively work?

---

### Post by TheFu on 2018-01-19
[https://www.linuxquestions.org/questions/linux-networking-3/which-rdp-client-for-support-nla-4175447658/](https://www.linuxquestions.org/questions/linux-networking-3/which-rdp-client-for-support-nla-4175447658/) says xfreerdp.  It is a little picky about some things.  

To minimize risks, we only allow RDP from the LAN, so actually use x2go for internet access from the internet, then RDP into Windows from there.  x2go is much, much, faster too.

I tested xfreerdp this morning. Haven't found a way to migrate all the settings from the other tool we use into xfreerdp.  Some of them simply caused an ERROR that I couldn't fix.  Found it very, very, slow compared to rdesktop, but rdesktop doesn't do encryption.

---

