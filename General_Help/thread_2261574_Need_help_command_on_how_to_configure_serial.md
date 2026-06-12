---
title: "Need help command on how to configure serial?"
date: 2015-01-19
forum: General Help
---

### Post by cyclonmaster on 2015-01-19
I need to change ttyACM1 to ttyACM0. Anyone can help me? I need the command to do this. Thanks.

---

### Post by tgalati4 on 2015-01-19
```
sudo ln -s /dev/ttyACM0 /dev/ttyACM1
```

---

### Post by HermanAB on 2015-01-19
Here is everything on serial ports and more:
[http://www.aeronetworks.ca/search?q=serial](http://www.aeronetworks.ca/search?q=serial)

---

### Post by HermanAB on 2015-01-19
dup

---

### Post by cyclonmaster on 2015-01-19
> **tgalati4 said:**
> ```
sudo ln -s /dev/ttyACM0 /dev/ttyACM1
```

Thanks. I did try:

sudo ln -s /dev/ttyACM1 /dev/ttyACM0

It works. But, after restart the settings is not there anymore. Is there a way to make it persistent/permanent?

---

### Post by steeldriver on 2015-01-19
You could probably achieve what you want using a custom udev rule

---

### Post by cyclonmaster on 2015-01-19
Can you help me with that? This is the lsusb:

Bus 001 Device 007: ID 0451:16a8 Texas Instruments, Inc.

it is on ttyACM1. I can see the device in /dev/serial/by-id

I want it to be on ttyACM0 permanent.

Now I am not sure what to put in /lib/udev/rules.d/

---

