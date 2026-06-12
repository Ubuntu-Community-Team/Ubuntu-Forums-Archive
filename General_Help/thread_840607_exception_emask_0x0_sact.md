---
title: "exception emask 0x0 sact"
date: 2008-06-25
forum: General Help
---

### Post by ranger47 on 2008-06-25
I have a vostro 200 slim (like the dell 530) and can not get ubuntu to boot.  It gets stuck and puts out pages of exception emask 0x0 sact as you can see on the attached.  I thought it might be related to the busybox problem mentioned [here]("http://ubuntuforums.org/showpost.php?p=4850950&postcount=2").

I tried to insert the all_generic_ide boot-time parameter, but it doesn't work.  Any ideas for a newbie would be appreciated.  Thanks!

---

### Post by abn91c on 2008-06-25
if you are in the middle of an install dont attach any USB devices just yet, like printers, external HDD, etc

---

### Post by ranger47 on 2008-06-25
> **abn91c said:**
> if you are in the middle of an install dont attach any USB devices just yet, like printers, external HDD, etc

Awesome.  It didn't work when I unplugged all the USBs but when I unplugged my PCI tv tuner and firewire card it worked.  Thanks!

---

