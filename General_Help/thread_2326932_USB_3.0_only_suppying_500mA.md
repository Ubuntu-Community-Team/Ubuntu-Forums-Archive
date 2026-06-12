---
title: "USB 3.0 only suppying 500mA"
date: 2016-06-06
forum: General Help
---

### Post by markvdm on 2016-06-06
Hi Guys

Been running Ubuntu 16.04 since release, loving it, and just noticed this little issue. My laptop (HP EliteBook 820 touchscreen) USB 3.0 ports I see are only supplying 500mA. When the laptop is powered down and I plug into the same port, which is an "Always On" I am seeing 1200mA.

I have tried a few suggestions on the web that I have found, but no joy yet.

Any ideas?

---

### Post by mcduck on 2016-06-06
That would depend on the device you plug in. USB standard defines the current as 500mA by default, and then when devices are connected and recognized, they can request for higher current. So I'd assume the problem is that what ever device you are plugging in isn't recognized properly and therefore can't ask for more power.

When the OS is not running, the charging feature on the USB port is handled directly by the laptop's motherboard so compatibility with the OS is not an issue. (Or it cold be it's not handled at all and the laptop just gives more current automatically in that mode, although that would break the standard and possibly cause issues with some devices, so I doubt HP would do it that way)

---

