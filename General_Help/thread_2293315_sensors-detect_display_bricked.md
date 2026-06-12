---
title: "sensors-detect display bricked"
date: 2015-09-04
forum: General Help
---

### Post by iliecristiandorobat on 2015-09-04
Hello,

I was running 'sensors-detect' on my Kubuntu x64 and after finished, my display it was whiter and bricked.

The problem is that even I am going to boot in Windows this it still persists.

Someone known how to return it at normal parameters?

(I have ASUS f550jk)

---

### Post by howefield on 2015-09-04
Thread moved to the "*General Help*" forum for better support.

---

### Post by patlkli on 2015-09-04
This looks like a problem with lm-sensors from 2013 when they reported issues with various laptop screens, which were bricked after sensors-detect because they messed with some EEPROMs.

On the Arch Linux Forums is [a thread]("https://bbs.archlinux.org/viewtopic.php?id=193048&p=2") from someone who also bricked the screen of his Lenovo laptop and eventually got a screen replacement.
However, in that thread, some people had success fixing their screens with I2C commands. You might want to read those posts and try it out.

I just don't really want to give you **one** command to try and fix it all.
This is actually quite a bit of trial and error and it's messing with your hardware permanently, so watch out.

---

### Post by iliecristiandorobat on 2015-09-04
Thanks, I hope to resolve those in service and if not, I'll go to Asus to try to solve it.

---

### Post by iliecristiandorobat on 2015-09-21
Finally, my service has replaced the display

---

