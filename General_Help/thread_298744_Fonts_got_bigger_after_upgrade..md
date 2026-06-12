---
title: "Fonts got bigger after upgrade."
date: 2006-11-13
forum: General Help
---

### Post by Dead_$partan on 2006-11-13
Hi All,

I recently installed beryl and the latest nvidia drivers in order to get the fantastic eye candy available for linux.

Everything looks class but the only thing I have noticed is that the font is all slightly larger/bolder.

For example when the login screen comes up and I enter my name the font is noticably bigger and is also the same with firefox.  Does anyone know why this happens and how to resolve it?

Thanks.

---

### Post by tmastran on 2006-11-13
Don't know why but I had a similar problem. I "fixed" it by adding:

    Option         "UseEdidDpi" "FALSE"
    Option         "DPI" "96 x 96"

to my /etc/X11.xorg.conf file in the "Screen" section (for NVIDIA driver). Restarted X to see the change -  Ctrl-Alt-Backspace.

---

### Post by Dead_$partan on 2006-11-13
Thanks for that,

I'll try that tonight when I get home from work.

Regards

---

### Post by Dead_$partan on 2006-11-14
Worked a treat, thanks for the help :D

---

