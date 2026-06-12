---
title: "ASUS ROG GL551JW-WH71(WX) Mic not working on headphone/microphone combo jack"
date: 2016-05-25
forum: General Help
---

### Post by davidbullship on 2016-05-25
Laptop Model: ASUS ROG GL551JW-WH71(WX)
Link to product page: [http://www.newegg.com/Product/Product.aspx?Item=N82E16834232848](http://www.newegg.com/Product/Product.aspx?Item=N82E16834232848)

Headset Model: HyperX Cloud Gaming Headset - Black (KHX-H3CL/WR)
Link to product page: [http://www.amazon.com/HyperX-Cloud-Gaming-Headset-KHX-H3CL/dp/B00JJNQG98](http://www.amazon.com/HyperX-Cloud-Gaming-Headset-KHX-H3CL/dp/B00JJNQG98)

I've searched everywhere, but can't make heads or tails of why my microphone will not work when I connect my headset/mic combo into the 3.5mm combo audio port. Currently, my laptop's built in microphone is picking up sound, but it sounds horrible. Would love to be able to use my headset's microphone instead

Here are a few common requests I've seen from other threads, hopefully this helps.

uname -a output
```
Linux oracle-G551JW 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```
aplay -l output
```
Linux oracle-G551JW 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
oracle@oracle-G551JW:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC668 Analog [ALC668 Analog]
  Subdevices: 0/1
```
cat /proc/asound/version output
```
Advanced Linux Sound Architecture Driver Version k4.4.0-22-generic.
```
head -n 1 /proc/asound/card*/codec#* output
```
==> /proc/asound/card0/codec#0 <==
Codec: Intel Haswell HDMI

==> /proc/asound/card1/codec#0 <==
Codec: Realtek ALC668
```

Please let me know if there is anything else I can supply to get this working.

Thank you!

---

### Post by davidbullship on 2016-05-26
Daily bump

---

