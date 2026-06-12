---
title: "What are the /dev names for firewire (IEEE1394) ports in 14.04.1"
date: 2014-12-04
forum: General Help
---

### Post by cscj01 on 2014-12-04
I am using Ubuntu 14.04.1 x64.  In /dev, I have two devices named fw0 and fw1.  Are these my firewire ports?

If so, I am a little confused.  If I use Kdenlive, I can just click the connect icon, and I can connect to my device.  However, if I use Shotcut, I have to specify the device.  I have tried both /dev/fw0 and /dev/fw1, but neither one connects to my device.

---

### Post by tgalati4 on 2014-12-04
Perhaps it is a permissions problem.  Try loosening up the permissions on the firewire ports:

```
sudo chmod 777 /dev/fw0
```

---

