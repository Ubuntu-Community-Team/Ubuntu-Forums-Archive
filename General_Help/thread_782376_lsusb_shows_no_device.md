---
title: "lsusb shows no device"
date: 2008-05-04
forum: General Help
---

### Post by Sambo320 on 2008-05-04
I have a Belkin 7050 version 4000. The device uses the zd1211rw driver. The device is not being detected at all in ubuntu 8.04. lsusb does not show the device at all. please help.

---

### Post by geraldm on 2008-05-05
```

lsmod | grep "zd1211rw" -
# if no module is returned, with the device plugged in, then continue:
sudo modprobe zd1211rw

```

Gerald

---

### Post by Sambo320 on 2008-05-06
I tried that. The device is still a no show with lsusb.

---

