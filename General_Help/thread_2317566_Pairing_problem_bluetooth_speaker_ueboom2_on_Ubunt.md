---
title: "Pairing problem bluetooth speaker ueboom2 on Ubuntu 14."
date: 2016-03-17
forum: General Help
---

### Post by goldenstar on 2016-03-17
Good day!
I appreciate your help on how to pair the ue boom 2 speaker on ubuntu 14.

I open the bluetooth box and it keeps scanning but it does not find the device.

I am new to ubuntu and many things I have done on my laptop is through research.  I am not an expert but I am eager to learn.

I would appreciate your help.

Regards.

Natura:D

---

### Post by jeremy31 on 2016-03-17
Please post ```
lsusb; dmesg | egrep -i 'blue|firm'; pactl list short | grep bluetooth
```

The obvious question is- did you put the speaker in pairing/discoverable mode?  Check speaker manual

---

### Post by goldenstar on 2016-03-18
Thanks Jeremy.  Unfortunately the manual does not say much about this  To my knowledge.  I will try to put the speaker on that mode.

---

