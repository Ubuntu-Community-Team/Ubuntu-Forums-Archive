---
title: "no output going to HDMI of Samsung TV"
date: 2017-01-18
forum: General Help
---

### Post by rawlins02 on 2017-01-18
I'm connecting to one of the HDMI inputs on a Samsung television through a VGA to HDMI cable from my laptop. I'm running Ubuntu 14.04 on a Lenovo T440p. Card is:

```

> lspci |grep VGA
02:00.0 VGA compatible controller: NVIDIA Corporation GK208M [GeForce GT 730M] (rev a1)

```

xrandr says no input to HDMI when connected to television. I'm using the open source Nouveau driver. Have seen suggestions to try the proprietary driver. Is that true? And is it as simple as selecting in Software and Updates --> Additional Drivers. I see NVIDIA binary drivers version 340.101 and 367.57 ?

I'm able to soon test on another HDMI display in a day or so if needed.

---

### Post by efflandt on 2017-01-18
It is confusing that you say you are using a VGA to HDMI cable, because they are not compatible with each other. VGA is analog video only and HDMI is digital video only. If you bought some sort of VGA to HDMI cable, that is bogus unless it has an actual "converter" that converts analog to digital video (which usually requires some source of power, even if just USB to microUSB).

Certain types of DVI (DVI-I) can work with simple cable or adapter for VGA or HDMI because DVI-I has pins for both analog and digital video. But some DVI is digital only (which can still work with DVI to HDMI cable).

If your laptop only has VGA (and not HDMI or DVI) you would need a VGA to HDMI "converter", not just a simple cable unless your TV has a VGA port on it to use with a cable with VGA plugs on both ends.

---

### Post by Kris_M on 2017-01-19
yeah, try 367

---

### Post by rawlins02 on 2017-01-21
OK. I didn't know the signal needed converting. I've ordered a converter. Thanks for the help.

---

### Post by rawlins02 on 2017-01-26
Here is the converter:

[https://www.amazon.com/gp/product/B00K4W62R4/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B00K4W62R4/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1)

I'm able to now get a display. Just working through getting mouse to behave properly. Will update as I know more.

---

### Post by rawlins02 on 2017-01-26
Everything working fine. Getting closer to cutting the cord...

---

