---
title: "compyz"
date: 2008-06-12
forum: General Help
---

### Post by t4ggs on 2008-06-12
Hi, I'm running ubuntu 8.04 and using the emerald theme manager and also beryl+compiz... my question is how do I make transparent windows borders to be flur like the vista glass effect.. I'm attaching some pictures..

I tries using the blur windows effect in the CompizConfig Setting Manager (Advanced Desktop Effects Settings) but nothing changes...

i want my currents windows (pic 1) to be like in pic 2.

---

### Post by Grishka on 2008-06-12
you have to use a proper emerald theme. not all of them have translucent borders. find a theme you like for example here: [http://compiz-themes.org](http://compiz-themes.org).

---

### Post by Forlong on 2008-06-12
Your graphics card driver need to support this.

What graphics chip and driver do you have?

---

### Post by Genius314 on 2008-06-12
If the blur windows plug-in doesn't work, it's most likely a problem with you're hardware or drivers.
Blur didn't work for me until I installed the restricted driver.

Try going to System>Administration>Hardware Drivers. If you see a graphics driver in the list there, enable it, and reboot. If it works, blur might work as well.
If not, I can't help you.

---

### Post by t4ggs on 2008-06-12
well I'm using the theme of the pic 2 and pic 1 is how i see it...and my graphic card is nvidia 6600 GT about the driver...i suppose is the original...when i enter in System, Administration, Hardware Drivers, i see Nvidia Accelerated graphics driver (latest cards) enabled...


I've also tried with other themes but still the same problem...

---

### Post by Forlong on 2008-06-12
Run ```
emerald-theme-manager
``` and make sure **Compiz Decoration Blur Type** is not set to None in the **Emerald Settings** tab.

---

### Post by t4ggs on 2008-06-12
> **Forlong said:**
> Run ```
emerald-theme-manager
``` and make sure **Compiz Decoration Blur Type** is not set to None in the **Emerald Settings** tab.

ops really simple...
thank man.... it was all.

---

