---
title: "Unable to escape Nvidia ~~LOGIN LOOP~~"
date: 2016-12-26
forum: General Help
---

### Post by ac2334 on 2016-12-26
Hello,

Please help me diagnose/resolve my Nvidia driver-related login loop.

I have tried every solution that I could find. My model of laptop - MSI GT780DX - seems to have major issues with Linux (it's a 570M card by the way)

The only driver that I can get anywhere with (meaning no black screen after boot) is Nvidia legacy binary 304.132

Thank you in advance

---

### Post by Bashing-om on 2016-12-26
ac2334; Hello;

Have you tried the nVidia recommended 375 version driver ?
[http://www.nvidia.com/download/driverResults.aspx/112992/en-us](http://www.nvidia.com/download/driverResults.aspx/112992/en-us)
This driver is available in our trusted PPA .

[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Show us what is currently installed,
```

sudo find / -name "NVIDIA-Linux-*"
dpkg -l | grep -i nvidia

```

We clean things up and 
[INDENT][INDENT]take off again
[/INDENT][/INDENT]

---

