---
title: "What's a good USB WiFi/PCI WiFi adapter that'll work with Ubuntu?"
date: 2013-03-03
forum: General Help
---

### Post by Cam! on 2013-03-03
I have a Netgear WNDA USB dongle and it can't work with any OS out the box (let alone Linux distros!) What's a good PCI-based WiFi adapter, or even a USB dongle that'll work with Ubuntu?

---

### Post by itrogers on 2013-03-03
Check out this link: [http://wireless.kernel.org/en/users/Devices/USB](http://wireless.kernel.org/en/users/Devices/USB)

This seems to be a set of compatible hardware and drivers built right into the kernel for USB wireless adapters. Hope that helps!

---

### Post by Cam! on 2013-03-03
Oh, damn. I have a WNDA3100, but I see the 3**2**00 is supported. xD What about PCI cards? Am I better off with them?

---

### Post by 3rdalbum on 2013-03-03
> **Cam! said:**
> Oh, damn. I have a WNDA3100, but I see the 3**2**00 is supported. xD What about PCI cards? Am I better off with them?

Not really. It doesn't matter if a card connects via PCI or USB, if the chipset is not supported it won't work.

USB is probably a better bet as it's easier to sell if it doesn't work on Linux :-)

The last time I wanted a USB wifi device to work with Linux, I looked on Amazon and found one that advertised Linux compatibility. On the current version of Ubuntu at the time, I needed to blacklist a module to make it work. On the next version of Ubuntu, I didn't, it just worked out of the box.

---

### Post by BLOODBANKER on 2013-03-04
I just installed the Edimax EW-7128Gn 32-bit PCI adapter. It worked "out of the box" on my 12.04 box. I got it from Amazon.
[http://www.amazon.com/EW-7128Gn-150Mbps-Wireless-External-Detachable/dp/B0067I4Z6O](http://www.amazon.com/EW-7128Gn-150Mbps-Wireless-External-Detachable/dp/B0067I4Z6O). Hope this helps.

---

### Post by carl4926 on 2013-03-04
[COLOR=#333333]Belkin F5D7050[/COLOR]

---

### Post by kurt18947 on 2013-03-04
Wifi adapters and linux are a bit of a mine field.  I recommended Dlink DWA-131 as 'plug -n- play'.  I recently learned there is a firmware V.2 version of the  DWA-131 which is not only not plug -n- play, it currently does not play at all, even with NDISwrapper.  AFAIK TrendNet's TEW-649UB is still plug -n- play.  If you can find Intel based PCI cards, I think they mostly work although some have issues with N speeds.

---

### Post by CaptainMark on 2013-03-04
Get one of the Alfa Awus036 range, theyre cheap as hell have a massive range and have worked out of the box with no configuration for as long as I've had it, my friend recommended I get one and I was dubious when it arrived in the post as it feels cheap and naff in your hands but I'd never consider another adapter now

---

### Post by mike555 on 2013-03-04
I just got a   Rosewill USB 2.0 External 5dBi Antenna Wireless Adapter (RNX-N180UBE)   from Amazon and it is plug/play it also really boosts the range it gives 5 bars when my old wireless got 1 or 2 .......... highly recommend.

---

### Post by 3rdalbum on 2013-03-04
> **CaptainMark said:**
> Get one of the Alfa Awus036 range, theyre cheap as hell have a massive range and have worked out of the box with no configuration for as long as I've had it, my friend recommended I get one and I was dubious when it arrived in the post as it feels cheap and naff in your hands but I'd never consider another adapter now

Oh yes, I forgot to mention that I have one of the Alfa devices. Big antenna, great for wardriving but also really good Linux-compatible wifi units. Highly recommended.

---

### Post by ellishgibbons on 2013-03-04
Small difference between USB WiFi  vs PCI WiFi,                                                                                                                                                                           PCI with good Antenna that have an extension cord and sit over the system is better than USB.
USB vs. PCI with the Antenna at the source stuck between the case and the wall is Better.

---

