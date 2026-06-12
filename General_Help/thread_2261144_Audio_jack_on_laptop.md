---
title: "Audio jack on laptop"
date: 2015-01-16
forum: General Help
---

### Post by Or_Levy on 2015-01-16
Hello.
After installing the latest Lubuntu on my HP NX6110 (really old XD)
I'v noticed that if I am connecting headphones to the built in audio jack it will play from the headphones, 
but from the built in laptop speakers.
How to cause the system disable the built-in speakers once somthing is connected to the 3.5 mm audio jack?
Thanks for commenters and helpers.

Or

---

### Post by walterorlin on 2015-01-20
In a terminal run alsamixer and press the right arrow key until you find an option for automute and make sure it is enabled. This should stop the speakers playing if you plug in headphones.

---

### Post by Yellow Pasque on 2015-01-20
> How to cause the system disable the built-in speakers once somthing is connected to the 3.5 mm audio jack?
ALSA should do this automatically (it's called 'Auto-Mute').

Give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Or_Levy on 2015-01-28
> **walterorlin said:**
> In a terminal run alsamixer and press the right arrow key until you find an option for automute and make sure it is enabled. This should stop the speakers playing if you plug in headphones.

> **Temüjin said:**
> ALSA should do this automatically (it's called 'Auto-Mute').

Give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Hi, Thank you for answering, 
when i'v launched Alsa it didn't showed the option...
[[IMG]http://srv2.jpg.co.il/2/54c8d47d65456.png[/IMG]]("http://jpg.co.il/view/54c8d47d65456.png/")

---

### Post by Or_Levy on 2015-01-29
**solved**
I'v installed GNOME Alsa mixer,
and marked the "Headphones Jack Sense" box, and it was fixed.

---

